# AstrBot 全能视频下载助手

这是一个基于 `yt-dlp` 的 AstrBot 视频解析、下载和直链提取插件，支持 Bilibili、YouTube、Twitter/X、TikTok 等常见平台。

## 功能

- `/download <视频链接>`：下载视频并以文件形式发送
- `/video <视频链接>`：下载视频并以视频消息形式发送
- `/直链 <视频链接>`：解析并返回可用媒体直链
- 直接发送支持的平台视频链接时，自动解析并下载
- 支持播放列表确认下载，并打包为加密压缩包
- 使用 `imageio-ffmpeg` 提供 FFmpeg，减少系统环境依赖
- 支持代理配置，适合需要代理访问的平台

## 安装

在 AstrBot 插件管理中通过 GitHub 仓库安装：

```text
https://github.com/taolicx/astrbot_plugin_yt_dlp
```

也可以手动把本仓库放入 AstrBot 的 `data/plugins/astrbot_plugin_yt_dlp` 目录，然后重载插件。

## 依赖

插件依赖会由 AstrBot 根据 `requirements.txt` 自动安装：

```text
yt-dlp
imageio-ffmpeg
pyzipper
```

## 配置

插件提供 `_conf_schema.json`，可在 AstrBot 插件配置页面调整：

- 是否启用代理
- 代理地址
- 最高画质
- 最大文件大小
- 临时文件清理时间
- 是否优先 H.264 编码
- FFmpeg 路径策略
- 是否自动识别普通消息中的视频链接

## 说明

本仓库由 `taolicx` 维护，已修复 AstrBot 桌面版中 `metadata.yaml` 的 `name` 字段非法导致无法安装的问题。插件名为 `astrbot_plugin_yt_dlp`，符合 Python 模块命名规则。

从 `1.0.4` 起，命令后面即使带标题或分享文案，也会自动提取其中第一个支持的视频链接，并优先于其他链接解析插件处理。

`1.0.5` 修复了自动处理时过早停止事件传播导致只发送“正在解析资源信息...”的问题。

部分海外平台需要可用代理。视频能否成功发送还取决于平台文件大小限制，以及当前 AstrBot 适配器是否支持文件上传动作。
