# XIU2/CloudflareSpeedTest

[![Go Version](https://img.shields.io/github/go-mod/go-version/XIU2/CloudflareSpeedTest.svg?style=flat-square&label=Go&color=00ADD8&logo=go)](https://github.com/XIU2/CloudflareSpeedTest/)
[![Release Version](https://img.shields.io/github/v/release/XIU2/CloudflareSpeedTest.svg?style=flat-square&label=Release&color=00ADD8&logo=github)](https://github.com/XIU2/CloudflareSpeedTest/releases/latest)
[![GitHub license](https://img.shields.io/github/license/XIU2/CloudflareSpeedTest.svg?style=flat-square&label=License&color=00ADD8&logo=github)](https://github.com/XIU2/CloudflareSpeedTest/)
[![GitHub Star](https://img.shields.io/github/stars/XIU2/CloudflareSpeedTest.svg?style=flat-square&label=Star&color=00ADD8&logo=github)](https://github.com/XIU2/CloudflareSpeedTest/)
[![GitHub Fork](https://img.shields.io/github/forks/XIU2/CloudflareSpeedTest.svg?style=flat-square&label=Fork&color=00ADD8&logo=github)](https://github.com/XIU2/CloudflareSpeedTest/)

国外很多网站都在使用 Cloudflare CDN，但分配给中国内地访客的 IP 并不友好（延迟高、丢包多、速度慢）。  
虽然 Cloudflare 公开了所有 [IP 段](https://www.cloudflare.com/zh-cn/ips/) ，但想要在这么多 IP 中找到适合自己的，怕是要累死，于是就有了这个软件。

**「自选优选 IP」测试 Cloudflare CDN 延迟和速度，获取最快 IP (IPv4+IPv6)**！好用的话**点个`⭐`鼓励一下叭~**

> _分享我其他开源项目：[**TrackersList.com** - 全网热门 BT Tracker 列表！有效提高 BT 下载速度~](https://github.com/XIU2/TrackersListCollection) <img src="https://img.shields.io/github/stars/XIU2/TrackersListCollection.svg?style=flat-square&label=Star&color=4285dd&logo=github" height="16px" />_  
> _[**UserScript** - 🐵 Github 高速下载、知乎增强、自动无缝翻页、护眼模式 等十几个**油猴脚本**~](https://github.com/XIU2/UserScript) <img src="https://img.shields.io/github/stars/XIU2/UserScript.svg?style=flat-square&label=Star&color=4285dd&logo=github" height="16px" />_  
> _[**SNIProxy** - 🧷 自用的简单 SNI Proxy（支持全平台、全系统、前置代理、配置简单等~](https://github.com/XIU2/SNIProxy) <img src="https://img.shields.io/github/stars/XIU2/SNIProxy.svg?style=flat-square&label=Star&color=4285dd&logo=github" height="16px" />_  

当然了，本项目也支持对 **`其他 CDN / 多个解析 IP 的网站`** 延迟测速，但相对应的下载测速地址需自行寻找。

> [!IMPORTANT]
> Cloudflare CDN 已**明文禁止代理**方式使用，对于**代理套 CDN** 的自行承担风险，请勿过度依赖 [#382](https://github.com/XIU2/CloudflareSpeedTest/discussions/382) [#383](https://github.com/XIU2/CloudflareSpeedTest/discussions/383)

****
## \# 快速使用

### 下载运行

1. 下载编译好的可执行文件（ [Github Releases](https://github.com/XIU2/CloudflareSpeedTest/releases) / [蓝奏云](https://xiu.lanzoub.com/b0742hkxe) ）并解压。  
2. 双击运行 `cfst.exe` 文件（Windows 系统），等待测速完成...

<details>
<summary><code><strong>「 点击查看 Windows 系统下其他安装方式」</strong></code></summary>

****

如果你有 scoop(Windows 下的命令行安装程序)，则可以这样安装:

```sh
# 添加最多人使用的中文软件包仓库：dorado
scoop bucket add dorado https://github.com/chawyehsu/dorado
# 安装cloudflare-speedtest
scoop install dorado/cloudflare-speedtest
```

</details>

<details>
<summary><code><strong>「 点击查看 Linux 系统下的使用示例 」</strong></code></summary>

****

以下命令仅为示例，版本号和文件名请前往 [**Releases**](https://github.com/XIU2/CloudflareSpeedTest/releases) 查看。

``` yaml
# 如果是第一次使用，则建议创建新文件夹（后续更新时，跳过该步骤）
mkdir cfst

# 进入文件夹（后续更新，只需要从这里重复下面的下载、解压命令即可）
cd cfst

# 下载 CFST 压缩包（自行根据需求替换 URL 中 [版本号] 和 [文件名]）
wget -N https://github.com/XIU2/CloudflareSpeedTest/releases/download/v2.3.4/cfst_linux_amd64.tar.gz
# 如果你是在国内网络环境中下载，那么请使用下面这几个镜像加速之一：
# wget -N https://ghfast.top/https://github.com/XIU2/CloudflareSpeedTest/releases/download/v2.3.4/cfst_linux_arm64.tar.gz
# wget -N https://wget.la/https://github.com/XIU2/CloudflareSpeedTest/releases/download/v2.3.4/cfst_linux_arm64.tar.gz
# wget -N https://ghproxy.net/https://github.com/XIU2/CloudflareSpeedTest/releases/download/v2.3.4/cfst_linux_arm64.tar.gz
# wget -N https://gh-proxy.com/https://github.com/XIU2/CloudflareSpeedTest/releases/download/v2.3.4/cfst_linux_arm64.tar.gz
# wget -N https://hk.gh-proxy.com/https://github.com/XIU2/CloudflareSpeedTest/releases/download/v2.3.4/cfst_linux_arm64.tar.gz
# 如果下载失败的话，尝试删除 -N 参数（如果是为了更新，则记得提前删除旧压缩包 rm cfst_linux_amd64.tar.gz ）

# 解压（不需要删除旧文件，会直接覆盖，自行根据需求替换 文件名）
tar -zxf cfst_linux_amd64.tar.gz

# 赋予执行权限
chmod +x cfst

# 运行（不带参数）
./cfst

# 运行（带参数示例）
./cfst -tl 200 -dn 20
```

> 如果平**均延迟非常低**（如 0.xx），则说明 CFST **测速时走了代理**，请先关闭代理软件后再测速。  
> 如果在**路由器**上运行，建议先关闭路由器内的代理（或将其排除），否则测速结果可能会**不准确/无法使用**。

</details>

****

> _在**手机**上独立运行 CFST 测速的简单教程：**[Android](https://github.com/XIU2/CloudflareSpeedTest/discussions/61)、[Android APP](https://github.com/xianshenglu/cloudflare-ip-tester-app)、[IOS](https://github.com/XIU2/CloudflareSpeedTest/discussions/321)**_

> [!NOTE]
> 注意！本软件仅适用于网站，**不支持给使用 UDP 协议的 Cloudflare WARP 优选 IP**，具体见：[#392](https://github.com/XIU2/CloudflareSpeedTest/discussions/392)

### 结果示例

测速完毕后，默认会显示**最快的 10 个 IP**，示例（仅为输出内容示例）：

``` bash
IP 地址           已发送  已接收  丢包率  平均延迟  下载速度(MB/s)  地区码
104.27.200.69     4      4       0.00   146.23    28.64          LAX
172.67.60.78      4      4       0.00   139.82    15.02          SEA
104.25.140.153    4      4       0.00   146.49    14.90          SJC
104.27.192.65     4      4       0.00   140.28    14.07          LAX
172.67.62.214     4      4       0.00   139.29    12.71          LAX
104.27.207.5      4      4       0.00   145.92    11.95          LAX
172.67.54.193     4      4       0.00   146.71    11.55          LAX
104.22.66.8       4      4       0.00   147.42    11.11          SEA
104.27.197.63     4      4       0.00   131.29    10.26          FRA
172.67.58.91      4      4       0.00   140.19    9.14           SJC
...

# 如果平均延迟非常低（如 0.xx），则说明 CFST 测速时走了代理，请先关闭代理软件后再测速。
# 如果在路由器上运行，请先关闭路由器内的代理（或将其排除），否则测速结果可能会不准确/无法使用。

# 因为每次测速都是在每个 IP 段中随机 IP，所以每次的测速结果都不可能相同，这是正常的！

# 注意！我发现电脑开机后第一次测速延迟会明显偏高（手动 TCPing 也一样），后续测速都正常
# 因此建议大家开机后第一次正式测速前，先随便测几个 IP（无需等待延迟测速完成，只要进度条动了就可以直接关了）

# 软件在 默认参数 下的整个流程大概步骤：
# 1. 延迟测速（默认 TCPing 模式，HTTPing 模式需要手动加上参数）
# 2. 延迟排序（延迟 从低到高 排序并按条件过滤，不同丢包率会分开排序，因此可能会有一些延迟低但丢包的 IP 排到后面）
# 3. 下载测速（从延迟最低的 IP 开始依次下载测速，默认测够 10 个就会停止）
# 4. 速度排序（速度从高到低排序）
# 5. 输出结果（通过参数控制是否输出到命令行(-p 0)或输出到文件(-o "")）

# 注意：输出的结果文件 result.csv 通过微软 Excel 表格打开会中文乱码，这是正常的，其他表格软件/记事本都显示正常
```

测速结果第一行就是**既下载速度最快、又平均延迟最低的最快 IP**！

完整结果保存在当前目录下的 `result.csv` 文件中，用**记事本/表格软件**打开，格式如下：

```
IP 地址,已发送,已接收,丢包率,平均延迟,下载速度(MB/s),地区码
104.27.200.69,4,4,0.00,146.23,28.64,LAX
```

> [!NOTE]
> _如果你发现**下载速度为 0.00**，那么可以用**调试模式 `-debug`** 排查一下，详见：[**# 下载测速都是 0.00 ？**](https://github.com/XIU2/CloudflareSpeedTest#-%E4%B8%8B%E8%BD%BD%E6%B5%8B%E9%80%9F%E9%83%BD%E6%98%AF-000-)_

> _大家可以按自己需求，对完整结果**进一步筛选处理**，或者去看一看进阶使用**指定过滤条件**！_

****
## \# 进阶使用

直接运行使用的是默认参数，如果想要测速结果更全面、更符合自己的要求，可以自定义参数。

```Dart
C:\>cfst.exe -h

CloudflareSpeedTest vX.X.X
测试各个 CDN 或网站所有 IP 的延迟和速度，获取最快 IP (IPv4+IPv6)！
https://github.com/XIU2/CloudflareSpeedTest

参数：
    -n 200
        延迟测速线程；越多延迟测速越快，性能弱的设备 (如路由器) 请勿太高；(默认 200 最多 1000)
    -t 4
        延迟测速次数；单个 IP 延迟测速的次数；(默认 4 次)
    -dn 10
        下载测速数量；延迟测速并排序后，从最低延迟起下载测速的数量；(默认 10 个)
    -dt 10
        下载测速时间；单个 IP 下载测速最长时间，不能太短；(默认 10 秒)
    -tp 443
        指定测速端口；延迟测速/下载测速时使用的端口；(默认 443 端口)
    -url https://cf.xiu2.xyz/url
        指定测速地址；延迟测速(HTTPing)/下载测速时使用的地址，默认地址不保证可用性，建议自建；
        当下载测速时，软件会从 HTTP 响应头中获取该 IP 当前地区码（支持 Cloudflare、AWS CloudFront、Fastly、Gcore、CDN77、Bunny 等 CDN）并显示出来。

    -httping
        切换测速模式；延迟测速模式改为 HTTP 协议，所用测试地址为 [-url] 参数；(默认 TCPing)
        当使用 HTTP 测速模式时，软件会从 HTTP 响应头中获取该 IP 当前地区码（支持 Cloudflare、AWS CloudFront、Fastly、Gcore、CDN77、Bunny 等 CDN）并显示出来。
        注意：HTTPing 本质上也算一种 网络扫描 行为，因此如果你在服务器上面运行，需要降低并发(-n)，否则可能会被一些严格的商家暂停服务。
        如果你遇到 HTTPing 首次测速可用 IP 数量正常，后续测速越来越少甚至直接为 0，但停一段时间后又恢复了的情况，那么也可能是被 运营商、Cloudflare CDN 认为你在网络扫描而 触发临时限制机制，因此才会过一会儿就恢复了，建议降低并发(-n)减少这种情况的发生。
    -httping-code 200
        有效状态代码；HTTPing 延迟测速时网页返回的有效 HTTP 状态码，仅限一个；(默认 200 301 302)
    -cfcolo HKG,KHH,NRT,LAX,SEA,SJC,FRA,MAD
        匹配指定地区；IATA 机场地区码或国家/城市码，英文逗号分隔，大小写均可，仅 HTTPing 模式可用；(默认 所有地区)
        支持 Cloudflare、AWS CloudFront、Fastly、Gcore、CDN77、Bunny 等 CDN
        其中 Cloudflare、AWS CloudFront、Fastly 使用的是 IATA 三字机场地区码，如：HKG,LAX
        其中 CDN77、Bunny 使用的是 二字国家/区域码，如：US,CN
        其中 Gcore 使用的是 二字城市码，如：FR,AM
        因此大家使用 -cfcolo 指定地区码时要根据不同的 CDN 来指定不同类型的地区码。

    -tl 200
        平均延迟上限；只输出低于指定平均延迟的 IP，各上下限条件可搭配使用；(默认 9999 ms)
    -tll 40
        平均延迟下限；只输出高于指定平均延迟的 IP；(默认 0 ms)
    -tlr 0.2
        丢包几率上限；只输出低于/等于指定丢包率的 IP，范围 0.00~1.00，0 过滤掉任何丢包的 IP；(默认 1.00)
    -sl 5
        下载速度下限；只输出高于指定下载速度的 IP，凑够指定数量 [-dn] 才会停止测速；(默认 0.00 MB/s)

    -p 10
        显示结果数量；测速后直接显示指定数量的结果，为 0 时不显示结果直接退出；(默认 10 个)
    -f ip.txt
        IP段数据文件；如路径含有空格请加上引号；支持其他 CDN IP段；(默认 ip.txt)
    -ip 1.1.1.1,2.2.2.2/24,2606:4700::/32
        指定IP段数据；直接通过参数指定要测速的 IP 段数据，英文逗号分隔；(默认 空)
    -o result.csv
        写入结果文件；如路径含有空格请加上引号；值为空时不写入文件 [-o ""]；(默认 result.csv)

    -dd
        禁用下载测速；禁用后测速结果会按延迟排序 (默认按下载速度排序)；(默认 启用)
    -allip
        测速全部的IP；对 IP 段中的每个 IP (仅支持 IPv4) 进行测速；(默认 每个 /24 段随机测速一个 IP)

    -debug
        调试输出模式；会在一些非预期情况下输出更多日志以便判断原因；(默认 关闭)
        目前该功能仅针对 HTTPing 延迟测速过程 及 下载测速过程，当过程中因为各种原因导致当前 IP 测速中断都会输出错误原因
        例如：HTTPing 延迟测速过程中，因为 HTTP 状态码不符合或测速地址有问题或超时等原因而终止测速
        例如：下载测速过程中，因为下载测速地址有问题（被阻断、403状态码、超时）等原因而终止测速（导致显示 0.00）

    -v
        打印程序版本 + 检查版本更新
    -h
        打印帮助说明
```

### 界面解释

为了避免大家对测速过程中的**输出内容产生误解（可用、队列等数字，下载测速一半就"中断"？下载测速"卡住"不动？）**，我特意解释下。

<details>
<summary><code><strong>「 点击展开 查看内容 」</strong></code></summary>

****

> 该示例把常用参数都给加上了，即为：`-tll 40 -tl 150 -sl 1 -dn 5`，最后输出结果如下：

```python
# XIU2/CloudflareSpeedTest vX.X.X

开始延迟测速（模式：TCP, 端口：443, 范围：40 ~ 150 ms, 丢包：1.00)
321 / 321 [-----------------------------------------------------------] 可用: 30
开始下载测速（下限：1.00 MB/s, 数量：5, 队列：10）
3 / 5 [-----------------------------------------↗--------------------]
IP 地址           已发送  已接收  丢包率  平均延迟  下载速度(MB/s)  地区码
XXX.XXX.XXX.XXX   4      4       0.00   83.32     3.66           LAX
XXX.XXX.XXX.XXX   4      4       0.00   107.81    2.49           LAX
XXX.XXX.XXX.XXX   4      3       0.25   149.59    1.04           N/A

完整测速结果已写入 result.csv 文件，可使用记事本/表格软件查看。
按下 回车键 或 Ctrl+C 退出。
```

****

> 刚接触 CFST 的人，可能会迷惑**明明延迟测速可用 IP 有 30 个，怎么最后只剩下 3 个了呢？**  
> 下载测速里的队列又是什么意思？难道我下载测速还要排队？

CFST 会先延迟测速，在这过程中进度条右侧会实时显示可用 IP 数量（`可用: 30`），但注意该可用数量指的是**测试通过没有超时的 IP 数量**，和延迟上下限、丢包条件无关。当延迟测速完成后，因为还指定了**延迟上下限、丢包**的条件，所以按照条件过滤后只剩下 `10` 个了（也就是等待下载测速的 `队列：10`）。

即以上示例中，`321` 个 IP 延迟测速完成后，只有 `30` 个 IP 测试通过没有超时，然后根据延迟上下限范围：`40 ~ 150 ms` 及丢包上限条件过滤后，只剩下 `10` 个满足要求的 IP 了。如果你 `-dd` 禁用了下载测速，那么就会直接输出这 `10` 个 IP 了。当然该示例并未禁用，因此接下来软件会继续对这 `10` 个 IP 进行下载测速（`队列：10`）。

> 因为下载测速是单线程一个个 IP 挨着排队测速的，因此等待下载测速的 IP 数量才会叫做 `队列`。

****

> 你可能注意到了，**明明指定了要找到 5 个满足下载速度条件的 IP，怎么才 3 个就 “中断” 了呢？**

下载测速进度条中的 `3 / 5`，前者指的是找到了 `3` 个满足下载速度下限条件的 IP（即下载速度高于 `1 MB/s` ），后者 `5` 指的是你要求找到 `5` 个满足下载速度下限条件的 IP（`-dn 5`）。

> 另外，提醒一下，如果你指定的 `-dn` 大于下载测速队列，比如你延迟测速后只剩下 `4` 个 IP 了，那么下载测速进度条中后面的数字就会和下载测速队列一样都是 `4` 个，而非你 `-dn` 指定的 `5` 个了。

软件在测速完这 `10` 个 IP 后，只找到了 `3` 个下载速度高于 `1 MB/s` 的 IP，剩下的 `7` 个 IP 都是 “不及格” 的。

因此，这不是 `“每次测速都不到 5 就中断了”`，而是所有 IP 都下载测速完了，但却只找到了 `3` 个满足条件的。

****

还有一种情况，那就是当可用 IP 很多时（几百几千），你还设置了下载速度条件，那么可能就会遇到：**怎么下载测速进度条老是卡在 `X / 5` 了呢？**

这其实并不是卡住了，而是只有当找到一个满足条件的 IP 时，进度条才会 +1，因此如果一直找不到，那么 CFST 就会一直下载测速下去，因此在表现为进度条卡住不动，但这也是在提醒你：你设置的下载速度条件对你来说已经高于实际了，你需要适当调低预期。

****

如果不想遇到这种全部测速一遍都没几个满足条件的情况，那么就要**调低下载速度上限参数 `-sl`**，或者移除。

因为只要指定了 `-sl` 参数，那么只要没有凑够 `-dn` 的数量（默认 10 个），就会一直测速下去，直到凑够或全部测速完。移除 `-sl` 并添加 `-dn 20` 参数，这样就是只测速延迟最低的前 20 个 IP，测速完就停止，节省时间。

****

另外，如果全部队列 IP 都测速完了，但一个满足下载速度条件的 IP 都没有，你可能需要调低预期的下载测速下限条件，但你需要知道当前的大概测速速度都在什么范围，那么你就可以加上 `-debug` 参数开启调试模式，这样再遇到这种情况时，就会**忽略条件返回所有测速结果**，你就能看到这些 IP 的下载速度都有多少，心里也就有数了，然后**适当调低 `-sl` 再试试**。

> 注意，如果你**没有指定**下载测速下限 `-sl` 条件，那么无论什么情况下 CFST 都会**输出所有测速结果**。

同样，延迟测速方面，`可用: 30`、`队列：10` 这两个数值也可以让你清楚，你设置的延迟条件对你来说是否过于苛刻。如果可用 IP 一大堆，但条件过滤后只剩下 2、3 个，那不用说就知道需要**调低预期的延迟/丢包条件**了。

这两个机制，一个是告诉你**延迟丢包条件**是否合适的，一个是告诉你**下载速度条件**是否合适的。

</details>

****

### 使用示例

Windows 要指定参数需要在 CMD 中运行，或者把参数添加到快捷方式目标中。

> [!TIP]
> - 各参数均有**默认值**，当使用默认值时参数可以省略（**按需选择**），参数**不分前后顺序**。  
> - Windows **PowerShell** 只需把下面命令中的 `cfst.exe` 改为 `.\cfst.exe` 即可。  
> - Linux / macOS 系统只需要把下面命令中的 `cfst.exe` 改为 `./cfst` 即可。

****

#### \# CMD 带参数运行

对命令行程序不熟悉的人，可能不知道该如何带参数运行，我就简单说一下。

<details>
<summary><code><strong>「 点击展开 查看内容 」</strong></code></summary>

****

很多人打开 CMD 直接就以**绝对路径**运行 CFST 会报错，这是因为默认的 `-f ip.txt` 参数是相对路径，需要指定绝对路径的 ip.txt 才行，但这样毕竟太麻烦了，因此还是建议进入 CFST 程序目录下，以**相对路径**方式运行：

**方式 一**：
1. 打开 CFST 程序所在目录  
2. 空白处按下 <kbd>Shift + 鼠标右键</kbd> 显示右键菜单  
3. 选择 **\[在此处打开命令窗口\]** 来打开 CMD 窗口，此时默认就位于当前目录下  
4. 输入带参数的命令，如：`cfst.exe -tl 200 -dn 20` 即可运行

**方式 二**：
1. 打开 CFST 程序所在目录  
2. 直接在文件夹地址栏中全选(或清空)并输入 `cmd` 回车就能打开 CMD 窗口，此时默认就位于当前目录下  
4. 输入带参数的命令，如：`cfst.exe -tl 200 -dn 20` 即可运行

> 当然你也可以随便打开一个 CMD 窗口，然后输入如 `cd /d "D:\Program Files\cfst"` 来进入程序目录

> **提示**：如果用的是 **PowerShell** 只需把命令中的 `cfst.exe` 改为 `.\cfst.exe` 即可。

</details>

****

#### \# Windows 快捷方式带参数运行

如果不经常修改运行参数（比如平时都是直接双击运行）的人，建议使用快捷方式，更方便点。

<details>
<summary><code><strong>「 点击展开 查看内容 」</strong></code></summary>

****

右键 `cfst.exe` 文件 - **\[创建快捷方式\]**，然后右键该快捷方式 - **\[属性\]**，修改其**目标**：

``` bash
# 如果要不输出结果文件，那么请加上 -o " "，引号里的是空格（没有空格会导致该参数被省略）。
D:\ABC\cfst\cfst.exe -tl 200 -dn 20 -o " "

# 如果文件路径包含引号，则需要把启动参数放在引号外面，记得引号和 - 之间有空格。
"D:\Program Files\cfst\cfst.exe" -tl 200 -dn 20 -o " "

# 注意！快捷方式 - 起始位置 不能是空的，否则就会因为绝对路径而找不到 ip.txt 文件
```

</details>

****

#### \# IPv4/IPv6

<details>
<summary><code><strong>「 点击展开 查看内容 」</strong></code></summary>

****
``` bash
# 指定自带的 IPv4 数据文件可测速这些 IPv4 地址（-f 默认值就是 ip.txt，所以该参数可省略）
cfst.exe -f ip.txt

# 指定自带的 IPv6 数据文件可测速这些 IPv6 地址
# 另外，v2.1.0 版本后支持 IPv4+IPv6 混合测速并移除了 -ipv6 参数，因此一个文件内可以同时包含 IPv4+IPv6 地址
cfst.exe -f ipv6.txt

# 也可以直接通过参数指定要测速的 IP
cfst.exe -ip 1.1.1.1,2606:4700::/32
```

> 测速 IPv6 时，可能会注意到每次测速数量都不一样，了解原因： [#120](https://github.com/XIU2/CloudflareSpeedTest/issues/120)  
> 因为 IPv6 太多（以亿为单位），且绝大部分 IP 段压根未启用，所以我只扫了一部分可用的 IPv6 段写到 `ipv6.txt` 文件中，有兴趣的可以自行扫描增删，ASN 数据源来自：[bgp.he.net](https://bgp.he.net/AS13335#_prefixes6)

</details>

****

#### \# HTTPing

<details>
<summary><code><strong>「 点击展开 查看内容 」</strong></code></summary>

****

目前有两种延迟测速模式，分别为 **TCP 协议、HTTP 协议**。  
TCP 协议耗时更短、消耗资源更少，超时时间为 1 秒，该协议为默认模式。  
HTTP 协议适用于快速测试某域名指向某 IP 时是否可以访问，超时时间为 2 秒。  
同一个 IP，各协议去 Ping 得到的延迟一般为：**ICMP < TCP < HTTP**，越靠右对丢包等网络波动越敏感。

> 注意：HTTPing 本质上也算一种**网络扫描**行为，因此如果你在服务器上面运行，需要**降低并发**(`-n`)，否则可能会被一些严格的商家暂停服务。如果你遇到 HTTPing 首次测速可用 IP 数量正常，后续测速越来越少甚至直接为 0，但停一段时间后又恢复了的情况，那么也可能是被 运营商、Cloudflare CDN 认为你在网络扫描而**触发临时限制机制**，因此才会过一会儿就恢复了，建议**降低并发**(`-n`)减少这种情况的发生。

> 另外，本软件 HTTPing 仅获取**响应头(response headers)**，并不获取正文内容（即 URL 文件大小不影响 HTTPing 测试，但如果你还要下载测速的话，那么还是需要一个大文件的），类似于 curl -i 功能。

> 另外，HTTPing 过程中，软件会从 HTTP 响应头中获取该 IP 当前地区码（支持 Cloudflare、AWS CloudFront、Fastly、Gcore、CDN77、Bunny 等 CDN）并显示出来，而 TCPing 过程中无法这样做（但 下载测速 时也会这样做来获取地区码，毕竟下载测速也是个 HTTP 链接）

``` bash
# 只需加上 -httping 参数即可切换到 HTTP 协议延迟测速模式
cfst.exe -httping

# 软件会根据访问时网页返回的有效 HTTP 状态码来判断可用性（当然超时也算），默认对返回 200 301 302 这三个 HTTP 状态码的视为有效，可以手动指定认为有效的 HTTP 状态码，但只能指定一个（你需要提前确定测试地址正常情况下会返回哪个状态码）
cfst.exe -httping -httping-code 200

# 通过 -url 参数来指定 HTTPing 测试地址（可以是任意网页 URL，不局限于具体文件地址）
cfst.exe -httping -url https://cf.xiu2.xyz/url
# 如果你要 HTTPing 测试其他网站/CDN，那么指定一个该网站/使用该 CDN 的地址（因为软件默认地址是 Cloudflare 的，只能用于测试 Cloudflare 的 IP）

# 注意：如果测速地址为 HTTP 协议，记得加上 -tp 80（这个参数会影响 延迟测速/下载测速 时使用的端口）
# 同理，如果要测速 80 端口，那么也需要加上 -url 参数来指定一个 http:// 协议的地址才行（且该地址不会强制重定向至 HTTPS），如果是非 80 443 端口，那么需要确定该下载测速地址是否支持通过该端口访问。
cfst.exe -httping -tp 80 -url http://cdn.cloudflare.steamstatic.com/steam/apps/5952/movie_max.webm
```

</details>

****

#### \# 匹配指定地区

<details>
<summary><code><strong>「 点击展开 查看内容 」</strong></code></summary>

****

Cloudflare CDN 的节点 IP 是 Anycast IP，即每个 IP 对应的服务器节点及地区不是固定的，而是动态变化的，**不同地区、不同运营商、不同时间段**访问**同一个 IP** 分配到的服务器节点地区和路线也都是不一样的（比如同一个 IP，美国人访问就是分配到就近的美国节点服务器，日本人访问则就又变成了就近的日本节点服务器了，国内内地就比较特殊了，只能给你分配到其他国家，当然不同的 IP 段路由变化/分配逻辑也是不同的，有的 IP 段会较为固定）。

> **注意**！虽然 Cloudflare CDN 有很多亚洲节点，但**不代表你就能用上**，新加坡人测速可能随便一抓一大把的新加坡节点，但你全部扫一遍可能都遇不到一个，因为这是由 CDN 控制的。Anycast IP 的路由是经常变的，同一个 IP 今天可能是美国，明天你再访问可能就又分配到欧洲节点了（当然这只是个例子，一般没有那么频繁，这也和很多因素有关，比如线路拥塞程度，成本变动等），因此**不要对该功能有过高期待**~

或者你随便找个 Cloudflare CDN 的 IP（比如官网域名的解析 IP `104.16.123.96`），然后去那些有全球节点的[在线 Ping 测试](https://ping.sx/ping?t=104.16.123.96)网站，你就会发现这个 IP 在全球大部分地区的延迟都是个位数（而且很多都是 0.X ms），就算一些地方延迟高一些但也基本都控制在 几十ms，只有在国内才会发现突然变成了 上百ms 了。

这就是 Anycast 技术，也就只有国内大陆这种特殊的网络情况，才需要对 Anycast 的 CDN IP 进行优选。

因此，对于这种 Anycast IP 的实际服务器位置，就不能靠那些在线 IP 地址位置查询网站来判断了。

除了通过 **HTTP 响应头**获取地区码外（该功能的实现方式），还可以手动访问 `http://CloudflareIP/cdn-cgi/trace` 来获知 CDN 分配给你的实际节点地区码。

> 该功能支持 **Cloudflare、AWS CloudFront、Fastly、Gcore、CDN77、Bunny** 等 CDN。  
> 但注意，不是所有 CDN 都支持 Anycast 技术的，很多 CDN 会限制一个网站能使用的 IP 范围。

> 其中 **Cloudflare、AWS CloudFront、Fastly** 都使用的是 **`IATA 三字机场地区码`**，如：HKG,LAX  
> 而 **CDN77、Bunny** 使用的是 **`二字国家/区域码`**，如：US,CN  
> **Gcore** 则使用的是 **`二字城市码`**，如：FR,AM  
> 因此大家使用 `-cfcolo` 指定地区码时要根据不同的 CDN 来指定不同类型的地区码。

> **注意**：如果你要用于筛选 AWS CloudFront CDN 地区，那么要通过 `-url` 参数指定一个使用 AWS CloudFront CDN 的下载测速地址（因为软件默认下载测速地址是 Cloudflare CDN 的），另外有时候 HTTPing 模式测速一些 AWS CloudFront 地址会返回 403 错误，这种情况下需要加上 `-httping-code 403` 才能正确获取地区码。

``` bash
# 指定地区名后，延迟测速后得到的结果就都是指定地区的 IP 了（如果没有指定 -dd 的话则会继续进行下载测速）
# 如果延迟测速后结果为 0，则说明没有找到任何一个（未超时可用的）指定地区的 IP。
# 节点地区名为当地 IATA 机场地区码或国家/城市码，指定多个时用英文逗号分隔，v2.2.3 版本后支持小写

cfst.exe -httping -cfcolo HKG,KHH,NRT,LAX,SEA,SJC,FRA,MAD

# 注意，该参数只有在 HTTPing 延迟测速模式下才可用（因为软件是通过 HTTP 链接中的响应头来获得该 IP 的实际地区码）

# 另外，HTTPing 过程中，软件会从 HTTP 响应头中获取该 IP 当前地区码（支持 Cloudflare、AWS CloudFront、Fastly、Gcore、CDN77、Bunny 等 CDN）并显示出来，而 TCPing 过程中无法这样做（但 下载测速 时也会这样做来获取地区码，毕竟下载测速也是个 HTTP 链接）
```

> **`IATA 三字机场地区码`**，可见：https://www.cloudflarestatus.com/  
> **`二字国家码`**，可见：[https://zh.wikipedia.org/wiki/ISO_3166-1二位字母代码#正式分配代码](https://zh.wikipedia.org/wiki/ISO_3166-1%E4%BA%8C%E4%BD%8D%E5%AD%97%E6%AF%8D%E4%BB%A3%E7%A0%81#%E6%AD%A3%E5%BC%8F%E5%88%86%E9%85%8D%E4%BB%A3%E7%A0%81)

</details>

****

#### \# 文件相对/绝对路径

<details>
<summary><code><strong>「 点击展开 查看内容 」</strong></code></summary>

****

``` bash
# 指定 IPv4 数据文件，不显示结果直接退出，输出结果到文件（-p 值为 0）
cfst.exe -f 1.txt -p 0 -dd

# 指定 IPv4 数据文件，不输出结果到文件，直接显示结果（-p 值为 10 条，-o 值为空但引号不能少）
cfst.exe -f 2.txt -o "" -p 10 -dd

# 指定 IPv4 数据文件 及 输出结果到文件（相对路径，即当前目录下，如含空格请加上引号）
cfst.exe -f 3.txt -o result.txt -dd


# 指定 IPv4 数据文件 及 输出结果到文件（相对路径，即当前目录内的 abc 文件夹下，如含空格请加上引号）
# Linux（CFST 程序所在目录内的 abc 文件夹下）
./cfst -f abc/3.txt -o abc/result.txt -dd

# Windows（注意是反斜杠）
cfst.exe -f abc\3.txt -o abc\result.txt -dd


# 指定 IPv4 数据文件 及 输出结果到文件（绝对路径，即 C:\abc\ 目录下，如含空格请加上引号）
# Linux（/abc/ 目录下）
./cfst -f /abc/4.txt -o /abc/result.csv -dd

# Windows（注意是反斜杠）
cfst.exe -f C:\abc\4.txt -o C:\abc\result.csv -dd


# 如果要以【绝对路径】运行 CFST，那么 -f / -o 参数中的文件名也必须是【绝对路径】，否则会报错找不到文件！
# Linux（/abc/ 目录下）
/abc/cfst -f /abc/4.txt -o /abc/result.csv -dd

# Windows（注意是反斜杠）
C:\abc\cfst.exe -f C:\abc\4.txt -o C:\abc\result.csv -dd
```
</details>

****

#### \# 测速其他端口

<details>
<summary><code><strong>「 点击展开 查看内容 」</strong></code></summary>

****

``` bash
# 如果你想要测速非默认 443 的其他端口，则需要通过 -tp 参数指定（该参数会影响 延迟测速/下载测速 时使用的端口）

# 如果要延迟测速 80 端口+下载测速（如果 -dd 禁用了下载测速则不需要），那么还需要指定 http:// 协议的下载测速地址才行（且该地址不会强制重定向至 HTTPS，因为那样就变成 443 端口了）
cfst.exe -tp 80 -url http://cdn.cloudflare.steamstatic.com/steam/apps/5952/movie_max.webm

# 如果是非 80 443 的其他端口，那么需要确定你使用的下载测速地址是否支持通过该非标端口访问。
```

</details>

****

#### \# 自定义测速地址

<details>
<summary><code><strong>「 点击展开 查看内容 」</strong></code></summary>

****

``` bash
# 该参数适用于下载测速 及 HTTP 协议的延迟测速，对于后者该地址可以是任意网页 URL（不局限于具体文件地址）

# 地址要求：可以直接下载、文件大小超过 200MB、用的是 Cloudflare CDN
cfst.exe -url https://cf.xiu2.xyz/url

# 注意：如果测速地址为 HTTP 协议（该地址不能强制重定向至 HTTPS），记得加上 -tp 80（这个参数会影响 延迟测速/下载测速 时使用的端口），如果是非 80 443 端口，那么需要确定下载测速地址是否支持通过该端口访问。
cfst.exe -tp 80 -url http://cdn.cloudflare.steamstatic.com/steam/apps/5952/movie_max.webm
```

</details>

****

#### \# 自定义测速条件（指定 延迟/丢包/下载速度 的目标范围）

<details>
<summary><code><strong>「 点击展开 查看内容 」</strong></code></summary>

****

> 注意：延迟测速进度条右边的**可用数量**，仅指延迟测速过程中**未超时的 IP 数量**，和延迟上下限条件无关。

- 仅指定 **[平均延迟上限]** 条件

``` bash
# 平均延迟上限：200 ms，下载速度下限：0 MB/s
# 即找到平均延迟低于 200 ms 的 IP，然后再按延迟从低到高进行 10 次下载测速
cfst.exe -tl 200
```

> 如果**没有找到一个满足延迟**条件的 IP，那么不会输出任何内容。

****

- 仅指定 **[平均延迟上限]** 条件，且**只延迟测速，不下载测速**

``` bash
# 平均延迟上限：200 ms，下载速度下限：0 MB/s，数量：不知道多少 个
# 即只输出低于 200ms 的 IP，且不再下载测速（因为不再下载测速，所以 -dn 参数就无效了）
cfst.exe -tl 200 -dd
```

- 仅指定 **[丢包几率上限]** 条件

``` bash
# 丢包几率上限：0.25
# 即找到丢包率低于等于 0.25 的 IP，范围 0.00~1.00，如果 -tlr 0 则代表过滤掉任何丢包的 IP
cfst.exe -tlr 0.25
```

****

- 仅指定 **[下载速度下限]** 条件

``` bash
# 平均延迟上限：9999 ms，下载速度下限：5 MB/s，数量：10 个（可选）
# 即需要找到 10 个平均延迟低于 9999 ms 且下载速度高于 5 MB/s 的 IP 才会停止测速
cfst.exe -sl 5 -dn 10
```

> 如果**没有找到一个满足速度**条件的 IP，那么不会输出任何内容，你可能需要调低预期的下载测速下限条件，但你需要知道当前的大概测速速度都在什么范围，那么你就可以加上 `-debug` 参数开启调试模式，这样再遇到这种情况时，就会**忽略条件返回所有测速结果**，你就能看到这些 IP 的下载速度都有多少，心里也就有数了，然后**适当调低 `-sl` 再试试**。  
> 注意，如果你**没有指定**下载测速下限 `-sl` 条件，那么无论什么情况下 CFST 都会**输出所有测速结果**。

> 没有指定平均延迟上限时，如果一直**凑不够**满足条件的 IP 数量，就会**一直测速**下去。  
> 建议**同时指定 [下载速度下限] + [平均延迟上限]**，这样测速到指定延迟上限还没凑够数量，就会终止测速。

****

- 同时指定 **[平均延迟上限] + [下载速度下限]** 条件

``` bash
# 平均延迟上限、下载速度下限均支持小数（如 -sl 0.5）
# 平均延迟上限：200 ms，下载速度下限：5.6 MB/s，数量：10 个（可选）
# 即需要找到 10 个平均延迟低于 200 ms 且下载速度高于 5 .6MB/s 的 IP 才会停止测速
cfst.exe -tl 200 -sl 5.6 -dn 10
```

> 如果**没有找到一个满足延迟**条件的 IP，那么不会输出任何内容。  
> 如果**没有找到一个满足速度**条件的 IP，那么不会输出任何内容，但可以通过加上 `-debug` 参数开启调试模式，这时会忽略条件输出所有 IP 测速结果（方便你下次测速时调整条件）。  
> 所以建议先不指定条件测速一遍，看看平均延迟和下载速度大概在什么范围，避免指定条件**过低/过高**！

> 因为 Cloudflare 公开的 IP 段是**回源 IP+任播 IP**，而**回源 IP**是无法使用的，所以下载测速是 0.00。  
> 运行时可以加上 `-sl 0.01`（下载速度下限），过滤掉**回源 IP**（下载测速低于 0.01MB/s 的结果）。

****

为了避免大家迷糊，我列出了在各种条件组合下的预期输出结果都是什么样的。

**没有指定任何 延迟/速度条件 (即都是默认值)：**
- 无论如何，都直接输出 **所有测速结果**

****

**指定了任何 延迟条件（`-tl` `-tll`，且无论是否开启调试模式 `-debug` 都一样）：**
- 如果找到最少 1 个满足条件的 IP，则只输出 **这几个满足条件的 IP**（如没有禁用下载测速，则会继续下载测速）  
- 如果没找到任何满足条件的 IP，则会输出 **空**（如没有禁用下载测速，也会因为数量为 0 而跳过下载测速）

****

**指定了任何 下载速度条件 (`-sl`)：**

且当 **关闭 调试模式** 时（即没加上 `-debug` 参数，这种情况下和延迟测速的逻辑完全一致）：

- 如果找到最少 1 个满足条件的 IP，则只输出 **这几个满足条件的 IP**  
- 如果没找到任何满足条件的 IP，则输出 **空**

且当 **开启 调试模式** 时（即加上了 `-debug` 参数，延迟测速并没有加上下面第二条里的逻辑，所以依然输出 空）：

- 如果找到最少 1 个满足条件的 IP，则只输出 **这几个满足条件的 IP**  
- 如果没找到任何满足条件的 IP，则直接输出 **所有测速结果**

</details>

****

#### \# 单独对一个或多个 IP 测速

<details>
<summary><code><strong>「 点击展开 查看内容 」</strong></code></summary>

****

**方式 一**：
直接通过参数指定要测速的 IP 段数据。
``` bash
# 先进入 CFST 所在目录，然后运行：
# Windows 系统（在 CMD 中运行）
cfst.exe -ip 1.1.1.1,2.2.2.2/24,2606:4700::/32

# Linux 系统
./cfst -ip 1.1.1.1,2.2.2.2/24,2606:4700::/32
```

****

**方式 二**：
或者把这些 IP 按如下格式写入到任意文本文件中，例如：`1.txt`

```
1.1.1.1
1.1.1.200
1.0.0.1/24
2606:4700::/32
```

> 单个 IP 的话可以省略 `/32` 子网掩码了（即 `1.1.1.1`等同于 `1.1.1.1/32`）。  
> 子网掩码 `/24` 指的是这个 IP 最后一段，即 `1.0.0.1~1.0.0.255`。


然后运行 CFST 时加上启动参数 `-f 1.txt` 来指定 IP 段数据文件。

``` bash
# 先进入 CFST 所在目录，然后运行：
# Windows 系统（在 CMD 中运行）
cfst.exe -f 1.txt

# Linux 系统
./cfst -f 1.txt

# 对于 1.0.0.1/24 这样的 IP 段只会随机最后一段（1.0.0.1~255），如果要测速该 IP 段中的所有 IP，请加上 -allip 参数。
```

</details>

****

#### \# 下载测速都是 0.00 ？

<details>
<summary><code><strong>「 点击展开 查看内容 」</strong></code></summary>

****
**\#\# 原理简单解释：**

首先要明白，CFST 下载测速过程，本质上和你将 `IP 下载测速地址域名` 写入 hosts 文件，然后浏览器去访问下载测速地址是一样的，只不过软件将其自动化了（类似于 `curl -I --resolve 下载测速地址域名:443:IP https://下载测速地址`）。

因此如果下载测速结果全都是 0.00 MB/s，那么代表**下载测速过程中出问题报错**，导致直接终止测速了（并最终显示为 0.00），就只有这几种可能性：

1. **下载测速地址有问题**
2. **测速的 IP 地址有问题**
3. **你的网络有问题**

****

**\#\# 调试模式排查：**

接下来**请务必**先在你原先使用的 CFST 运行命令后**追加一个 `-debug` 参数来开启调试模式**，重新跑一遍测速，这样下载测速过程中出现任何报错都会显示具体原因方便你排查。

常见的下载测速失败报错原因有（因为是 Go 语言的原生报错信息，因此基本都是英文）：

1. `... read: connection reset by peer ...  `  
**链接被重置**，可能是下载测速地址被阻断了 或测速 IP 被针对性 HTTPS 阻断了，可能是蔷干的，也可能是运营商干的（比如移动或部分地区的白名单），当然也可能是测速 IP 服务器单纯的重置了你这个不合法的链接请求
2. `... HTTP 状态码: 403 ...`  
像这种直接提示 **HTTP 状态码**的，比较好判断，如 403 就是下载测速地址禁止你访问，404 就是下载测速地址路径对应的文件找不到（具体其他的可以搜索 HTTP 状态码含义）
3. `... context deadline exceeded (Client.Timeout exceeded while awaiting headers) ...`  
这种一般是**请求超时**引起的，可能是 IP 或网络问题，也可能是 `-dt` 下载测速时间设置的太短了（当然默认的 10 秒肯定算不上短）
4. `... tls: handshake failure ...` 或 `... tls: failed to verify certificate ...`  
这种 **TLS 握手失败/SSL 证书错误** 代表下载测速地址和测速 IP 服务器不匹配，也就是下载测速地址与测速 IP 其中一方有误（例如下载测速地址是托管在 Fastly CDN 的，但测速 IP 是 Cloudflare CDN 的，或者反过来，总之就是你访问下载测速地址时该测速的 IP 服务器告诉你这个网站域名它不认识并把你拒之门外）
5. `... tls: failed to verify certificate: x509: certificate is valid for XXX.XX, not YYY.YY ...`  
这种是 **SSL 证书里没有包含你下载测速地址的域名**，要么是下载测速地址证书配置有问题，要么就是该测速服务器 IP 上并没有该下载测速地址域名对应的 SSL 证书，也就意味着这个服务器 IP 是不能用于该下载测速地址域名的（比如你用谷歌的服务器 IP 去下载测速百度的域名就会这样，或像上面 4 的原因一样）
6. `... tls: failed to verify certificate: x509: certificate has expired or is not yet valid: current time ...`  
这种是 **SSL 证书过期了或者尚未到有效时间**，除了这个原因外，也可能是和上面 4、5 的原因一样（这 4、5、6 三种报错可能会同时出现在同一个服务器 IP 上）
7. `... tls: failed to verify certificate: x509: certificate signed by unknown authority.`  
这种代表**系统证书配置有问题**，导致 TLS 握手时无法验证证书，目前只在 Termux 内遇到过（解决方法见：https://github.com/XIU2/CloudflareSpeedTest/discussions/61 帖子末尾）

> 如果你遇到了其他报错原因，且翻译后还是不懂，可以发 Issues 或 Discussions 询问，我也会更新到这里。  
> 但注意，发 Issues 或 Discussions 询问时，请记得带上**调试模式下 CFST 输出的完整内容（或者完整截图）**。

根据上面的报错原因排查一遍后，如果还是无法解决，那么可以尝试下面这些进一步排查：

****

**一、下载测速地址有问题**：

先去 [#490](https://github.com/XIU2/CloudflareSpeedTest/discussions/490) 找几个其他的下载测速地址都试试。

如果其中有能下载测速出结果的，则就代表你之前使用的下载测速地址有问题（注意，目前默认下载测速地址仅为一个带负载均衡轮询的重定向链接，会自动重定向到上面帖子里大家分享的公益下载测速地址，而这些地址在**不同地区的可用性可能有差异**，因此可能出现之前不行现在又正常的情况，如果**想要稳定，建议自建**，上面帖子写了几种自建方法）。

如果找了很多，都是一样 0.00，那么就要考虑其他可能性了。

****

**二、测速的 IP 地址有问题**：

你用来测速的 IP 地址，可能一些 TCP 测试是通的，但实际上因为各种原因导致不能建立 HTTP 链接（比如是回源 IP，比如是企业用户专用 IP 等等），因此你可以多尝试一些其他的 IP 看是否可行。

****

**三、你的网络有问题**：

这个就比较麻烦了，如果你现在是用电脑+宽带来使用 CFST 测速的，那么可以尝试关闭手机 WIFI 并打开流量，然后数据线连接电脑，设置好 USB 网络共享（不同手机系统不太一样，具体自行搜索哈），并拔掉电脑的网线，这样你的电脑现在就是走的手机流量数据网络了（如果手机流量数据和宽带不是一个运营商会更好排查），然后再次运行 CFST 测速看看结果是否改变（也可以同时尝试上面的排查方法来交叉验证）。

如果测速结果正常了，那么显然就是宽带网络的问题，如果还是一样的 0.00，那么就麻烦了。。。

****

</details>

****

#### \# 一劳永逸加速所有使用 Cloudflare CDN 的网站（不需要再一个个添加域名到 Hosts 了）

我以前说过，开发该软件项目的目的就是为了通过**改 Hosts 的方式来加速访问使用 Cloudflare CDN 的网站**。

但就如 [**#8**](https://github.com/XIU2/CloudflareSpeedTest/issues/8) 所说，一个个添加域名到 Hosts 实在**太麻烦**了，于是我就找到了个**一劳永逸**的办法！可以看这个 [**还在一个个添加 Hosts？完美本地加速所有使用 Cloudflare CDN 的网站方法来了！**](https://github.com/XIU2/CloudflareSpeedTest/discussions/71) 和另一个[依靠本地 DNS 服务来修改域名解析 IP 为自选 IP](https://github.com/XIU2/CloudflareSpeedTest/discussions/317) 的教程。

****

#### \# 自动更新 Hosts

考虑到很多人获得最快 Cloudflare CDN IP 后，需要替换 Hosts 文件中的 IP。

可以看这个 [**Issues**](https://github.com/XIU2/CloudflareSpeedTest/discussions/312) 获取 **Windows/Linux 自动更新 Hosts 脚本**！

****

## 问题反馈

如果你遇到什么问题，可以先去 [**Issues**](https://github.com/XIU2/CloudflareSpeedTest/issues)、[Discussions](https://github.com/XIU2/CloudflareSpeedTest/discussions) 里看看是否有别人问过了（记得去看下  [**Closed**](https://github.com/XIU2/CloudflareSpeedTest/issues?q=is%3Aissue+is%3Aclosed) 的）。  
如果没找到类似问题，请新开个 [**Issues**](https://github.com/XIU2/CloudflareSpeedTest/issues/new) 来告诉我！

> [!NOTE]
> **注意**！_与 CFST 本身 `反馈问题、功能建议` 无关的，请前往项目内部 论坛 讨论（顶部的 `💬 Discussions`_  

****

## 如果帮到你的话就 "打赏" 一下吧~🎉✨

![微信赞赏](https://github.com/XIU2/XIU2/blob/master/img/zs-01.png)![支付宝赞赏](https://github.com/XIU2/XIU2/blob/master/img/zs-02.png)

****

## 衍生项目

- _https://github.com/xianshenglu/cloudflare-ip-tester-app_  
_**CFST 安卓版 APP [#202](https://github.com/XIU2/CloudflareSpeedTest/discussions/320)**_

- _https://github.com/mingxiaoyu/luci-app-cloudflarespeedtest_  
_**CFST OpenWrt 路由器插件版 [#174](https://github.com/XIU2/CloudflareSpeedTest/discussions/319)**_

- _https://github.com/immortalwrt-collections/openwrt-cdnspeedtest_  
_**CFST OpenWrt 原生编译版本 [#64](https://github.com/XIU2/CloudflareSpeedTest/discussions/64)**_

- _https://github.com/hoseinnikkhah/CloudflareSpeedTest-English_  
_**English language version of CFST (Text language differences only) [#64](https://github.com/XIU2/CloudflareSpeedTest/issues/68)**_

> _此处仅收集了在本项目中宣传过的部分 CFST 相关衍生项目，如果有遗漏可以告诉我~_

****

## 感谢项目

- _https://github.com/Spedoske/CloudflareScanner_

> _因为该项目已经很长时间没更新了，而我又产生了很多功能需求，所以我临时学了下 Go 语言就上手了（菜）..._  
> _本软件基于该项目制作，但**已添加大量功能及修复 BUG**，并根据大家的使用反馈积极添加、优化功能（闲）..._

****

## 手动编译

<details>
<summary><code><strong>「 点击展开 查看内容 」</strong></code></summary>

****

为了方便，我是在编译的时候将版本号写入代码中的 version 变量，因此你手动编译时，需要像下面这样在 `go build` 命令后面加上 `-ldflags` 参数来指定版本号：

```bash
go build -ldflags "-s -w -X main.version=v1.0.0"
# 在 CloudflareSpeedTest 目录中通过命令行（例如 CMD、Bat 脚本）运行该命令，即可编译一个可在和当前设备同样系统、位数、架构的环境下运行的二进制程序（Go 会自动检测你的系统位数、架构）且版本号为 v1.0.0
```

如果想要在 Windows 64位系统下编译**其他系统、架构、位数**，那么需要指定 **GOOS** 和 **GOARCH** 变量。

例如在 Windows 系统下编译一个适用于 **Linux 系统 amd 架构 64 位**的二进制程序：

```bat
SET GOOS=linux
SET GOARCH=amd64
go build -ldflags "-s -w -X main.version=v1.0.0"
```

例如在 Linux 系统下编译一个适用于 **Windows 系统 amd 架构 32 位**的二进制程序：

```bash
GOOS=windows
GOARCH=386
go build -ldflags "-s -w -X main.version=v1.0.0"
```

> 可以运行 `go tool dist list` 来查看当前 Go 版本支持编译哪些组合。

****

当然，为了方便批量编译，我会专门指定一个变量为版本号，后续编译直接调用该版本号变量即可。  
同时，批量编译的话，还需要分开放到不同文件夹才行（或者文件名不同），需要加上 `-o` 参数指定。

```bat
:: Windows 系统下是这样：
SET version=v1.0.0
SET GOOS=linux
SET GOARCH=amd64
go build -o Releases\cfst_linux_amd64\cfst -ldflags "-s -w -X main.version=%version%"
```

```bash
# Linux 系统下是这样：
version=v1.0.0
GOOS=windows
GOARCH=386
go build -o Releases/cfst_windows_386/cfst.exe -ldflags "-s -w -X main.version=${version}"
```

</details>

****

## License

The GPL-3.0 License.
