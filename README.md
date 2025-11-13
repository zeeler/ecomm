# Redmi AX6000 Router

## 硬件介绍

Redmi AX6000路由器是一款在中端市场性价比不错的产品，硬件配置比较扎实。下面这个表格汇总了它的主要硬件配置信息，你可以快速了解：

| **组件类别** | **具体配置** |
| :--- | :--- |
| **处理器 (CPU)** | 联发科 **Filogic 830** 4核处理器，单核主频 **2GHz** |
| **内存 (RAM)** | **512MB** |
| **无线规格** | • **无线速率**：**6000兆级**<br>• **2.4GHz**：574Mbps<br>• **5GHz**：4804Mbps<br>• **技术特点**：支持 **160MHz** 频宽，**8数据流**设计 |
| **信号放大器** | **8路** 独立信号放大器 |
| **有线接口** | 4个自适应网口 (均为千兆口)，支持 **LAN口聚合**，可将任一网口设置为 **IPTV口** |
| **其他功能** | 支持 **Mesh组网**，赠送游戏加速器会员 |

## 获取SSH权限

- 固件版本：1.0.67 尝试成功
- 具体步骤：https://www.right.com.cn/forum/thread-8253125-1-1.html

## 按照OpenCrash

参考文档：https://github.com/juewuy/ShellCrash/blob/dev/README_CN.md

- 安装脚本
```shell
sh -c "$(curl -kfsSl https://fastly.jsdelivr.net/gh/juewuy/ShellCrash@master/install.sh)" && source /etc/profile &> /dev/null
```

- 设置
第一项：选稳定版
第二项：安装到 /data，确认安装
3）启动crash：
第一项：路由设备配置局域网透明代理
第二项：1（启用）
第三项：是否启用软固化功能？选 0，因为上面已经固化了

- 配置
基本配置
a. 切换源：主菜单-9 更新/卸载，7 切换安装源，4 Cloudflare_CDN源，这个源速度快一些
b. 修改内核：主菜单-2 内核功能设置，1 切换防火墙运行模式，改成混合模式
c. 配置文件：主菜单-6 导入配置文件，3 本地生成providers配置文件，a 添加providers提供者，输入url（自己的配置做成在线地址）；c 选择模板，根据路由器配置选择极简或者其他；b 生成基于providers的配置文件即可生成完整config.yaml，也可以用本项目clash目录下的config.yaml作为模板修改
d. 启动clash，选择内核进阶设置，启用域名嗅探
e. 安装UI

- 启动clash
选择9更新/卸载，再选择4安装本地Dashboard面板，选择2 Yacd-Meta魔改面板，安装目录选择1 /data/ShellCrash/ui
安装完后，再浏览器打开 http://192.168.12.1:9999/ui

## 配置SSH链接
openwrt的公钥要放在：/etc/dropbear/authorized_keys里
