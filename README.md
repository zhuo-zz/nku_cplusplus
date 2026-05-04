# ImageToPPT

基于 Qt/C++ 的图片到 PowerPoint 半自动重建工具。

## 项目简介

ImageToPPT 可以读取一张图片，通过人工框选和可选 OCR 的方式，将图片中的部分区域重建为 PowerPoint 对象。图片区域会被裁剪并插入到 PPT 中，文字区域会生成可编辑文本框。

为了提高视觉还原效果，程序支持“高保真背景”模式：导出时会将原图作为背景，并对已标记的文字区域进行背景色填充，再叠加可编辑文字框。

## 功能

- 导入一张图片
- 鼠标拖拽框选区域
- 将区域标记为图片区域或文字区域
- 图片区域自动裁剪并插入 PPT
- 文字区域生成可编辑文本框
- 可设置文字内容、字号、颜色和加粗
- 可选调用 Tesseract OCR 自动识别文字
- 支持高保真背景导出
- 一键导出 `.pptx` 文件

## 技术栈

- Qt Widgets：图形界面、图片显示、鼠标框选、弹窗交互
- C++17：核心业务逻辑和数据结构
- QImage：图片读取、裁剪和背景处理
- Office Open XML：生成 PowerPoint 内部 XML 文件
- PowerShell/.NET ZIP API：将 XML 和媒体资源打包为 `.pptx`
- Tesseract OCR：可选文字识别功能

## 构建

推荐使用 Qt Creator 打开 `Image2Ppt.pro` 直接构建运行。

也可以使用 CMake：

```powershell
cmake -S . -B build
cmake --build build --config Release
```

## 使用方法

1. 点击“打开图片”，选择需要转换的图片。
2. 在图片预览区域用鼠标拖拽框选内容。
3. 在弹窗中选择“图片区域”或“文字区域”。
4. 如果选择文字区域，可以手动输入文字；如果安装了 Tesseract，程序会尝试自动识别。
5. 根据需要设置文字字号、颜色和加粗。
6. 勾选或取消“高保真背景”。
7. 点击“导出 PPTX”，生成 PowerPoint 文件。

## 目录结构

```text
include/        头文件
source/         源文件
CMakeLists.txt  CMake 构建配置
Image2Ppt.pro   Qt qmake 构建配置
README.md       项目说明文档
.gitignore      Git 忽略规则
```

## 项目特点

本项目不是完全自动的 OCR 转 PPT 系统，而是一个半自动重建工具。既能体现 Qt 图形界面、鼠标事件、图片裁剪、数据结构、文件生成和 PPTX 打包，也避免了全自动版面分析带来的过高难度。

## 后续改进方向

- 增加自动区域检测
- 支持多页 PPT 导出
- 增强背景修复效果
- 增加图片区域和文字区域的属性编辑面板
