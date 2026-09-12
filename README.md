# 快递单号扫码收集工具

一个**纯前端、单文件、零后端**的快递单号扫码录入小工具。打开网页即可用手机摄像头扫描条形码 / 二维码，自动识别快递单号并登记，支持补充收件信息、搜索、去重和导出。扫码引擎（ZXing）已内联进 HTML，**离线也能运行**。

## 功能特性

- 摄像头实时扫码：支持条形码（Code128 / Code39 / EAN / ITF 等）与二维码
- 相册识别：可从相册选择含条码的图片进行识别
- 手动录入：不方便扫码时直接输入单号
- 信息登记：单号、收件人、联系电话、快递公司、物品类型、备注
- 自动去重：重复录入会提示，避免重复登记
- 搜索：按单号 / 收件人 / 电话 / 备注实时筛选
- 数据导出：一键导出 CSV（可用 Excel 打开）或 TXT
- 本地存储：数据保存在浏览器 localStorage，不上传任何服务器
- 移动端适配：全屏扫码页、扫描框动画、按下即扫、流畅省电

## 使用方法

### 方式一：直接打开（最简单）

下载 `express-scanner.html`，用手机或电脑浏览器打开即可。

> 摄像头权限要求页面运行在 `https://` 或 `localhost` 环境。
> 手机上请用系统浏览器（Safari / Chrome）打开，并允许相机权限；
> 部分 App 内置浏览器出于安全限制可能无法调用摄像头。

### 方式二：部署到网页（推荐手机使用）

将 `express-scanner.html` 放到任意支持 HTTPS 的静态托管服务即可，例如 GitHub Pages、Vercel、Netlify、腾讯云 COS 等，之后用手机浏览器访问网址。

#### 使用 GitHub Pages 部署

1. 进入仓库 **Settings → Pages**
2. **Source** 选择 `main` 分支、根目录 `/ (root)`，保存
3. 等待片刻，通过 `https://<用户名>.github.io/baodan/express-scanner.html` 访问

## 数据说明

- 所有记录仅保存在**当前浏览器本地**（localStorage），清除浏览器数据会一并删除，请及时用导出功能备份。
- 不同设备 / 不同浏览器之间数据不互通。
- CSV 导出为 UTF-8 编码，Excel 打开若出现乱码，可用「数据 → 自文本/CSV」方式导入。

## 技术栈

- 原生 HTML / CSS / JavaScript，无构建步骤
- [@zxing/browser](https://github.com/zxing-js/browser) 条码识别（已内联，无需联网加载）
- MediaDevices `getUserMedia` 调用摄像头
- localStorage 本地持久化

## 目录结构

```
baodan/
├── express-scanner.html   # 应用本体（单文件，含全部样式、逻辑与扫码引擎）
└── .gitignore
```

## 浏览器要求

- 较新版本的 Chrome / Edge / Safari
- 需授予摄像头权限（仅扫码时使用，不录制、不上传）
