---
title: 搭建openvpn
date: 2019-05-17 14:51:23
tags:
---

#### server安装

- 运行以下脚本自动安装openvpn

    > wget https://git.io/vpn -O openvpn-install.sh && bash openvpn-install.sh

- 这时候会有下面的提示：

    1. 设置监听的ip，默认是本机ip：可以直接回车
    2. 设置公网ip：在浏览器中直接搜索ip，查看公网ip
    3. 选择使用哪种协议：选择tcp协议
    4. 输入端口号：默认 1194 端口
    5. 选择DNS：默认当前系统
    6. 输入客户端证书名称：随便起名字
    7. 回车继续...
    8. 在 `~/` 目录下会生成一个 `client.ovpn` 的文件, 把这个文件保存下来。

- 坑
    1. openvpn包找不到，卸载并重新安装epel-release, 并清理yum缓存，并重新生成缓存
        > yum remove epel-release; yum install epel-release; yum clean all; yum makecache


#### 配置路由器转发

- tplink路由 => 高级功能 => 虚拟服务器 => 新增 => 输入虚拟服务器规则

#### client安装

##### macos

- 安装
    1.  [下载shimo客户端](https://www.shimovpn.com/)
    2. 选择OpenVpn协议
    3. 导入 `client.ovpn`

- 坑：
    1. macos下会提示net.sf.tuntaposx.tun未安装，去[下载安装](https://sourceforge.net/projects/tuntaposx/)

##### window

- 安装
    1. [下载openvpn客户端](https://openvpn.net/vpn-server-resources/connecting-to-access-server-with-windows/)
    2. 选择OpenVpn协议
    3. 导入 `client.ovpn`
