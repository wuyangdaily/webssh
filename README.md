# WebSSH
![webssh](./Picture.gif)

为你的SSH连接需求提供安全便捷的管理方案

## ✨ 项目简介
WebSSH 是一个基于 Web 的轻量级 SSH 管理工具，方便地在浏览器中进行安全的远程服务器管理。

## 🐳 Docker 一键部署
```bash
docker run -d \
  --name webssh \
  -p 8888:8888 \
  -e TZ=Asia/Shanghai \
  --restart=always \
  wuyangdaily/webssh:latest
```

## ⚙️ Docker `compose.yml` 部署
```yml
services:
    webssh:
        container_name: webssh
        restart: always
        ports:
            - 8888:8888
        environment:
            - TZ=Asia/Shanghai
        image: wuyangdaily/webssh:latest
```

## 💡 工作原理
WebSSH 通过 WebSocket 与浏览器进行实时交互，并将请求转发给基于 Tornado 与 Paramiko 的后端，实现对 SSH 服务器的安全连接和交互。流程如下所示：
```
+---------+     http     +--------+    ssh    +-----------+
| browser | <==========> | webssh | <=======> | ssh server|
+---------+   websocket  +--------+    ssh    +-----------+
```
这使得用户无需本地安装 SSH 客户端，即可通过网页方便快速地完成服务器管理操作。
