---
title: "No IP, no wireless, please help"
date: 2010-10-19
forum: Networking &amp; Wireless
---

### Post by erjoalgo on 2010-10-19
I posted this two months ago, I still have this problem. If someone could PLEASE help me I could actually have a laptop with internet connectivity, I'd really appreciate that.

Whenever I am on campus, I have no wireless internet.
Following this [official guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide"), I notice that I dont have an IP.

This is evident from the ouput of ifconfig:
```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:e8:d0:6f:8b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3864 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1754 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1636193 (1.6 MB)  TX bytes:510839 (510.8 KB)
          Interrupt:31 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:184 errors:0 dropped:0 overruns:0 frame:0
          TX paI dont think this can be very helpful at all. Any ideas??ckets:184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15376 (15.3 KB)  TX bytes:15376 (15.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:d6:0c:f2:44  
          inet6 addr: fe80::224:d6ff:fe0c:f244/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:65392 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18377 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19308882 (19.3 MB)  TX bytes:5011628 (5.0 MB)
```

The suggestion in said guide is to do:
"sudo dhclient <ath0>
or
sudo invoke-rc.d networking restart
then try the first command again"
But this is no good. Here is the output:
```

user@laptop:~$ sudo invoke-rc.d networking restart 
 * Reconfiguring network interfaces...                                                                                                                                                        [ OK ] 
user@laptop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 4023
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/00:24:d6:0c:f2:44
Sending on   LPF/wlan0/00:24:d6:0c:f2:44
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
user@laptop:~$

```

Also, just now, I got this for the first time:

```

user@laptop:~$ sudo invoke-rc.d networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
                                                                         [ OK ]
user@laptop:~$ sudo invoke-rc.d networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
user@laptop:~$ 

```
Notice that after running the command a second time, the 
"Ignoring unknown interface wlan0=wlan0." was not output.

Please help!
I have no wireless connectivity issues in the same laptop under Windows OS.

---

### Post by utilitytrack on 2010-10-19
> **erjoalgo said:**
> I posted this two months ago, I still have this problem.

TWO MONTHS? And nobody didn't helped you??

Give here the outputs of following commands:
```
$ lsb_release -d
$ uname -a
$ cat /proc/cmdline
$ lspci -nn 
$ ps -ef | grep -E -i 'supplicant|netwo|nm-app|wicd'
$ cat /etc/network/interfaces

```

Write out model of your PC/laptop and shortly describe your network setup.

---

### Post by erjoalgo on 2010-10-19
Sorry for the delay, I was at school, having to use Windows OS in order to get Internet access.
My laptop is a Dell Studio, I dont know what much to say, I guess its 64bit dual core, 4GB RAM, I think more detailed info is on these commands.
```
user@laptop:~$ lsb_release -d
Description: Ubuntu 10.04.1 LTS
user@laptop:~$ uname -a
Linux user-laptop 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:05:27 UTC 2010 x86_64 GNU/Linux
user@laptop:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-2.6.32-25-generic root=UUID=ec843793-118a-4fae-81ba-595a47bb3124 ro quiet splash
user@laptop:~$ cat /etc/network/interfaces
auto lo iface lo inet loopback #MYFIX #auto wlan0 #iface wlan0 inet dhcp

```

```


user@laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07) 00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07) 00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03) 00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03) 00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03) 00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03) 00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03) 00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03) 00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03) 00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03) 00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03) 00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03) 00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03) 00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03) 00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03) 00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03) 00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03) 00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93) 00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M-E LPC Interface Controller [8086:2917] (rev 03) 00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03) 00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03) 01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series] [1002:9553] 01:00.1 Audio device [0403]: ATI Technologies Inc RV710/730 [1002:aa38] 08:00.0 Network controller [0280]: Intel Corporation Wireless WiFi Link 5100 [8086:4232] 14:00.0 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Device [1217:10f7] (rev 01) 14:00.1 SD Host controller [0805]: O2 Micro, Inc. Device [1217:8120] (rev 01) 14:00.2 Mass storage controller [0180]: O2 Micro, Inc. Device [1217:8130] (rev 01) 20:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
user@laptop:~$ ps -ef | grep -E -i 'supplicant|netwo|nm-app|wicd'
ERROR: Garbage option.
********* simple selection *********  ********* selection by list *********
-A all processes                      -C by command name
-N negate selection                   -G by real group ID (supports names)
-a all w/ tty except session leaders  -U by real user ID (supports names)
-d all except session leaders         -g by session OR by effective group name
-e all processes                      -p by process ID
T  all processes on this terminal     -s processes in the sessions given
a  all w/ tty, including other users  -t by tty
g  OBSOLETE -- DO NOT USE             -u by effective user ID (supports names)
r  only running processes             U  processes for specified users
x  processes w/o controlling ttys     t  by tty
*********** output format **********  *********** long options ***********
-o,o user-defined  -f full            --Group --User --pid --cols --ppid
-j,j job control   s  signal          --group --user --sid --rows --info
-O,O preloaded -o  v  virtual memory  --cumulative --format --deselect
-l,l long          u  user-oriented   --sort --tty --forest --version
-F   extra full    X  registers       --heading --no-heading --context
                    ********* misc options *********
-V,V  show version      L  list format codes  f  ASCII art forest
-m,m,-L,-T,H  threads   S  children in sum    -y change -l format
-M,Z  security data     c  true command name  -c scheduling class
-w,w  wide output       n  numeric WCHAN,UID  -H process hierarchy

```

---

### Post by utilitytrack on 2010-10-19
**erjoalgo**

Please again post here output of commands that I specified. But on this time more accurately copy output from terminal. All formatting must be preserved:

```
$ cat /proc/cpuinfo | grep 'model name'
$ ps --version
$ dpkg -l network\* wicd\*
$ cat /etc/network/interfaces
$ lspci -nn
```

Exact model of your laptop is printed at the bottom of device. Check it and write here.

Also I asked:
> **utilitytrack said:**
> *shortly describe your network setup.*

What the device is connected to your laptop? What technology uses your ISP (Wired Ethernet, xDSL, DOCSIS, ISDN, Wi-Fi, Satellite and so on)?

---

### Post by erjoalgo on 2010-10-20
Here's the exact output, I hope this can help you/anyone else help me solve this.
```


user@user-laptop:~/wifiProblem$ cat /proc/cpuinfo | grep 'model name'
model name				: Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz
model name				: Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz
user@user-laptop:~/wifiProblem$ ps --version
procps version 3.2.8
user@user-laptop:~/wifiProblem$ dpkg -l network\* wicd\*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                Version             Description
+++-===================-===================-======================================================
ii  network-manager     0.8-0ubuntu3        network management framework daemon
ii  network-manager-gno 0.8-0ubuntu3        network management framework (GNOME frontend)
un  network-manager-kde <none>              (no description available)
ii  network-manager-ppt 0.8-0ubuntu3        network management framework (PPTP plugin)
ii  network-manager-ppt 0.8-0ubuntu3        network management framework (PPTP plugin, GNOME UI)
un  network-manager-ppt <none>              (no description available)
No packages found matching wicd*.
user@user-laptop:~/wifiProblem$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
user@user-laptop:~/wifiProblem$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M-E LPC Interface Controller [8086:2917] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series] [1002:9553]
01:00.1 Audio device [0403]: ATI Technologies Inc RV710/730 [1002:aa38]
08:00.0 Network controller [0280]: Intel Corporation Wireless WiFi Link 5100 [8086:4232]
14:00.0 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Device [1217:10f7] (rev 01)
14:00.1 SD Host controller [0805]: O2 Micro, Inc. Device [1217:8120] (rev 01)
14:00.2 Mass storage controller [0180]: O2 Micro, Inc. Device [1217:8130] (rev 01)
20:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
user@user-laptop:~/wifiProblem$ 

```
The model is just a Dell Studio 17.
The network Im having trouble accessing is my school's wireless, which is open and blankets the whole campus. Something I noted in my previous post is that this problem doesnt happen near my dorm, which is the location where I first connected to the network.
Outside my dorm, I dont get an IP, as evident from the first post.
Thanks for your help

---

### Post by utilitytrack on 2010-10-20
Ok. Next completely remove Network Manager. Follow instructions of aptitude:
```
# aptitude purge network-manager network-manager-pptp network-manager-gnome
```

Next give here:
```
$ lshw -C network
$ lsmod | grep -e iw -e ndis
$ dmesg | grep -e iw -e wlan
$ dpkg -l dhcp\* pump\* ndisw\*
$ ls -l /lib/modules/`uname -r`/kernel/drivers/net/wireless/iwlwifi/*

```

---

### Post by erjoalgo on 2010-10-20
I ran those commands, it asked me to resolve dependencies, I said "n". Well, I hope I can trust you and this will work out.
I am still connected though, so did I actually remove network manager? Maybe I should kill nm processes first? Still thanks for your help.
```

user@user-laptop:/$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 00
       serial: 00:24:d6:0c:f2:44
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=128.237.232.235 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:33 memory:f2200000-f2201fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:20:00.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:d0:6f:8b
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:31 ioport:4000(size=256) memory:f2004000-f2004fff(prefetchable) memory:f2000000-f2003fff(prefetchable) memory:f2020000-f203ffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
user@user-laptop:/$ lsmod | grep -e iw -e ndis
iwlagn                122996  0 
iwlcore               125179  1 iwlagn
mac80211              238896  2 iwlagn,iwlcore
led_class               3764  2 iwlcore,sdhci
cfg80211              148725  3 iwlagn,iwlcore,mac80211
user@user-laptop:/$ dmesg | grep -e iw -e wlan
[   15.752348] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   15.752350] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   15.752416] iwlagn 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.752424] iwlagn 0000:08:00.0: setting latency timer to 64
[   15.752482] iwlagn 0000:08:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   15.821149] iwlagn 0000:08:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   15.821228] iwlagn 0000:08:00.0: irq 33 for MSI/MSI-X
[   15.827987] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   16.707475] iwlagn 0000:08:00.0: firmware: requesting iwlwifi-5000-2.ucode
[   16.736641] iwlagn 0000:08:00.0: loaded firmware version 8.24.2.12
[   16.903065] Registered led device: iwl-phy0::radio
[   16.903081] Registered led device: iwl-phy0::assoc
[   16.903094] Registered led device: iwl-phy0::RX
[   16.903110] Registered led device: iwl-phy0::TX
[   16.933280] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   34.535370] wlan0: deauthenticating from 00:0f:7d:1d:49:51 by local choice (reason=3)
[   34.535440] wlan0: direct probe to AP 00:0f:7d:1d:49:51 (try 1)
[   34.541707] wlan0: direct probe responded
[   34.541711] wlan0: authenticate with AP 00:0f:7d:1d:49:51 (try 1)
[   34.548154] wlan0: authenticated
[   34.548174] wlan0: associate with AP 00:0f:7d:1d:49:51 (try 1)
[   34.551963] wlan0: RX AssocResp from 00:0f:7d:1d:49:51 (capab=0x1 status=0 aid=659)
[   34.551967] wlan0: associated
[   34.553555] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   44.229645] iwlagn 0000:08:00.0: iwl_tx_agg_start on ra = 00:0f:7d:1d:49:51 tid = 0
[   45.522525] wlan0: no IPv6 routers present
[  174.002684] wlan0: deauthenticating from 00:0f:7d:1d:49:51 by local choice (reason=3)
[  174.034932] wlan0: direct probe to AP 00:0f:7d:1d:49:51 (try 1)
[  174.034986] wlan0: deauthenticating from 00:0f:7d:1d:49:51 by local choice (reason=3)
[  174.036899] wlan0: direct probe to AP 00:0f:7d:1d:49:11 (try 1)
[  174.230293] wlan0: direct probe to AP 00:0f:7d:1d:49:11 (try 2)
[  174.234747] wlan0: direct probe responded
[  174.234759] wlan0: authenticate with AP 00:0f:7d:1d:49:11 (try 1)
[  174.245211] wlan0: authenticated
[  174.245261] wlan0: associate with AP 00:0f:7d:1d:49:11 (try 1)
[   from 00:0f:7d:1d:49:51 (capab=0x1 status=0 aid=657)
[ 1196.588412] wlan0: associated
[ 1198.971584] iwlagn 0000:08:00.0: iwl_tx_agg_start on ra = 00:0f:7d:1d:49:51 tid = 0
[ 1434.740160] wlan0: deauthenticating from 00:0f:7d:1d:49:51 by local choice (reason=3)
[ 1434.742835] wlan0: deauthenticating from 00:0f:7d:1d:49:51 by local choice (reason=3)
[ 1434.745795] wlan0: direct probe to AP 00:0f:7d:1d:49:11 (try 1)
[ 1434.768948] wlan0: direct prob58] wlan0: RX AssocResp from 00:0f:7d:1d:49:51 (capab=0x1 status=0 aid=657)
[ 3114.291563] wlan0: associated
[ 3233.602622] wlan0: deauthenticating from 00:0f:7d:1d:49:51 by local choice (reason=3)
[ 3233.617696] wlan0: deauthenticating from 00:0f:7d:1d:49:51 by local choice (reason=3)
[ 3233.619520] wlan0: direct probe to AP 00:0f:7d:1d:49:71 (try 1)
[ 3233.810162] wlan0: direct probe to AP 00:0f:7d:1d:49:71 (try 2)
[ 3233.817112] wlan0: direct probe responded
[ 3233.817121] wlan0: authenticate with AP 00:0f:7d:1d:49:71 (try 1)
[ 3233.823750] wlan0: authenticated
[ 3233.823801] wlan0: associate with AP 00:0f:7d:1d:49:71 (try 1)
[ 3233.833125] wlan0: RX AssocResp from 00:0f:7d:1d:49:71 (capab=0x1 sthenticate with AP 00:0f:7d:1d:49:51 (try 1)
[ 3954.412549] wlan0: authenticated
[ 3954.412576] wlan0: associate with AP 00:0f:7d:1d:49:51 (try 1)
[ 3954.416456] wlan0: RX AssocResp from 00:0f:7d:1d:49:51 (capab=0x1 status=0 aid=657)
[ 3954.416459] wlan0: associated
[ 4006.923378] iwlagn 0000:08:00.0: iwl_tx_agg_start on ra = 00:0f:7d:1d:49:51 tid = 0
[ 4554.040071] wlan0: deauthenticating from 00:0f:7d:1d:49:51 by local choice (reason=3)
[ 4554.043192] wlan0: deauthenticating from 00:0f:7d:1d:49:51 by local choice (reason=3)
[ 4554.044475] wlan0: direct probe to AP 00:0f:7d:1d:49:71 (try 1)
[ 4554.072203] w2010-09-17 19:33 /lib/modules/2.6.32-25-generic/kernel/drivers/net/wireless/iwlwifi/iwlcore.ko
user@user-laptop:/$
```

---

### Post by utilitytrack on 2010-10-20
> **erjoalgo said:**
> ... did I actually remove network manager?

Yes, because it's not needed on this stage and only creates confusion and additional complexity FOR REMOTE HELPERS (i.e. for me). Do as I say. However, if you don't trust nobody, you shouldn't ask for help on this (or any other) forum in general.

So, if you want to continue,  
```
# aptitude purge network-manager network-manager-pptp network-manager-gnome
$ dpkg -l dhcp\* pump\* ndisw\*

```

If not - no problem, I will not deal with your troubles. The choice is yours.

---

### Post by erjoalgo on 2010-10-20
As I mentioned, I gladly accept your help. I was just a little worried about removing network manager.
Although I did run those commands last time, it seems that I never actually finished removing the packages. This time I did:
```


user@user-laptop:/$ dpkg -l dhcp\* pump\* ndisw\*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                Version             Description
+++-===================-===================-======================================================
un  dhcp-client         <none>              (no description available)
ii  dhcp3-client        3.1.3-2ubuntu3      DHCP client
ii  dhcp3-common        3.1.3-2ubuntu3      common files used by all the dhcp3* packages
un  ndiswrapper-modules <none>              (no description available)
No packages found matching pump*.
user@user-laptop:/$ 

```

---

### Post by utilitytrack on 2010-10-20
> **erjoalgo said:**
> Although I did run those commands last time, it seems that I never actually finished removing the packages.

So, you removed network manager or not? If you have difficulties with installing/uninstalling packages, this means that your system has broken packages. But it's other problem. Check it:

```
$ dpkg -l network-manager\*
```

Now unload the wifi driver and show how it made:
```

# rmmod -v iwlagn && rmmod -v iwlcore && rmmod -v mac80211 && rmmod -v cfg80211
# tail -n 20 -f /var/log/messages
# logger TOKEN
```

All output post here.

---

### Post by erjoalgo on 2010-10-20
```


user@user-laptop:/$ rmmod -v iwlagn && rmmod -v iwlcore && rmmod -v mac80211 && rmmod -v cfg80211
rmmod iwlagn, wait=no
ERROR: Removing 'iwlagn': Operation not permitted
user@user-laptop:/$ sudo rmmod -v iwlagn && rmmod -v iwlcore && rmmod -v mac80211 && rmmod -v cfg80211
[sudo] password for user: 
rmmod iwlagn, wait=no
rmmod iwlcore, wait=no
ERROR: Removing 'iwlcore': Operation not permitted
user@user-laptop:/$ sudo rmmod -v iwlagn && rmmod -v iwlcore && rmmod -v mac80211 && rmmod -v cfg80211
ERROR: Module iwlagn does not exist in /proc/modules
user@user-laptop:/$ tail -n 20 -f /var/log/messages
Oct 20 15:14:00 user-laptop kernel: [ 1044.764755] sd 0:0:0:0: [sda] Starting disk
Oct 20 15:14:00 user-laptop kernel: [ 1046.500105] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Oct 20 15:14:00 user-laptop kernel: [ 1046.552753] ata1.00: configured for UDMA/100
Oct 20 15:14:00 user-laptop kernel: [ 1046.618787] PM: resume of drv:sd dev:0:0:0:0 complete after 1854.032 msecs
Oct 20 15:14:00 user-laptop kernel: [ 1046.619061] PM: resume of devices complete after 2794.616 msecs
Oct 20 15:14:00 user-laptop kernel: [ 1046.619229] PM: resume devices took 2.790 seconds
Oct 20 15:14:00 user-laptop kernel: [ 1046.619260] Restarting tasks ... done.
Oct 20 15:14:02 user-laptop kernel: [ 1048.226116] Registered led device: iwl-phy0::radio
Oct 20 15:14:02 user-laptop kernel: [ 1048.226133] Registered led device: iwl-phy0::assoc
Oct 20 15:14:02 user-laptop kernel: [ 1048.226148] Registered led device: iwl-phy0::RX
Oct 20 15:14:02 user-laptop kernel: [ 1048.226161] Registered led device: iwl-phy0::TX
Oct 20 15:14:02 user-laptop kernel: [ 1048.263233] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 20 15:14:02 user-laptop kernel: [ 1048.267043] r8169: eth0: link down
Oct 20 15:14:02 user-laptop kernel: [ 1048.267420] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 20 15:14:05 user-laptop kernel: [ 1051.158223] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct 20 15:14:20 user-laptop kernel: [ 1066.701795] iwlagn 0000:08:00.0: iwl_tx_agg_start on ra = 00:0f:7d:1d:49:51 tid = 0
Oct 20 15:14:58 user-laptop kernel: [ 1104.349923] iwlagn 0000:08:00.0: iwl_tx_agg_start on ra = 00:0f:7d:1d:49:11 tid = 0
Oct 20 15:15:06 user-laptop pulseaudio[1555]: ratelimit.c: 11 events suppressed
Oct 20 15:17:43 user-laptop kernel: [ 1269.497899] iwlagn 0000:08:00.0: iwl_tx_agg_start on ra = 00:0f:7d:1d:49:51 tid = 0
Oct 20 15:19:59 user-laptop kernel: [ 1405.171618] iwlagn 0000:08:00.0: PCI INT A disabled

^C
user@user-laptop:/$ logger TOKEN
user@user-laptop:/$ 

```
I noted the,
"ERROR: Removing 'iwlcore': Operation not permitted"
even as I ran it as root.

---

### Post by erjoalgo on 2010-10-21
I've removed nm. Will you help me?

---

### Post by utilitytrack on 2010-10-21
Do not worry, I'm here :))

So, no problem, driver unload can be made consistently:
```
# rmmod -v iwlagn ; rmmod -v iwlcore ; rmmod -v mac80211 ; rmmod -v cfg80211
```

Just in case check that you have firware installed:
```
$ ls -l /lib/firmware/iw*
```

After unloading, you should accurately load driver and monitor how it been made:
```
# logger TOKEN
# modprobe -v iwlagn 
# tail -n 20 -f /var/log/messages
```

Copy all output here.

> 
After that, remove your old network interfaces settings, we will create them anew:
```
# rm /etc/network/interfaces
```

If you ready to go, tell me.

PS
Did you pay attention that I write sign '#' before command or not? If you will to execute commands without enough rights it's will not have any sense.


PPS
Don't use hibernation/suspend while you set up wireless network.
See [https://bugzilla.kernel.org/show_bug.cgi?id=16133]("https://bugzilla.kernel.org/show_bug.cgi?id=16133")

---

### Post by erjoalgo on 2010-10-21
```
user@user-laptop:/$ sudo rmmod -v iwlagn ; rmmod -v iwlcore ; rmmod -v mac80211 ; rmmod -v cfg80211
ERROR: Module iwlagn does not exist in /proc/modules
rmmod iwlcore, wait=no
ERROR: Removing 'iwlcore': Operation not permitted
ERROR: Module mac80211 is in use by iwlcore
ERROR: Module cfg80211 is in use by iwlcore,mac80211
user@user-laptop:/$ ls -l /lib/firmware/iw*
-rw-r--r-- 1 root root 335056 2010-05-26 12:10 /lib/firmware/iwlwifi-1000-3.ucode
-rw-r--r-- 1 root root 150100 2010-05-26 12:10 /lib/firmware/iwlwifi-3945-2.ucode
-rw-r--r-- 1 root root 187972 2010-05-26 12:10 /lib/firmware/iwlwifi-4965-2.ucode
-rw-r--r-- 1 root root 345008 2010-05-26 12:10 /lib/firmware/iwlwifi-5000-1.ucode
-rw-r--r-- 1 root root 353240 2010-05-26 12:10 /lib/firmware/iwlwifi-5000-2.ucode
-rw-r--r-- 1 root root 337400 2010-05-26 12:10 /lib/firmware/iwlwifi-5150-2.ucode
-rw-r--r-- 1 root root 462280 2010-05-26 12:10 /lib/firmware/iwlwifi-6000-4.ucode
user@user-laptop:/$ sudo logger TOKEN
user@user-laptop:/$ sudo modprobe -v iwlagn 
insmod /lib/modules/2.6.32-25-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko 
user@user-laptop:/$ tail -n 20 -f /var/log//messages
Oct 21 01:46:11 user-laptop kernel: [ 1297.684555] iwlagn 0000:08:00.0: iwl_tx_agg_start on ra = 00:0f:7d:09:93:d1 tid = 0
Oct 21 01:48:09 user-laptop kernel: [ 1415.101081] iwlagn 0000:08:00.0: iwl_tx_agg_start on ra = 00:0f:7d:1d:49:71 tid = 0
Oct 21 01:52:47 user-laptop kernel: [ 1692.989663] iwlagn 0000:08:00.0: iwl_tx_agg_start on ra = 00:0f:7d:1d:49:51 tid = 0
Oct 21 01:56:57 user-laptop kernel: [ 1943.552126] iwlagn 0000:08:00.0: PCI INT A disabled
Oct 21 01:58:18 user-laptop user: TOKEN
Oct 21 01:58:55 user-laptop user: TOKEN
Oct 21 01:59:01 user-laptop kernel: [ 2067.386111] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Oct 21 01:59:01 user-laptop kernel: [ 2067.386119] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Oct 21 01:59:01 user-laptop kernel: [ 2067.386224] iwlagn 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Oct 21 01:59:01 user-laptop kernel: [ 2067.386439] iwlagn 0000:08:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
Oct 21 01:59:01 user-laptop kernel: [ 2067.425626] iwlagn 0000:08:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Oct 21 01:59:01 user-laptop kernel: [ 2067.432189] iwlagn 0000:08:00.0: firmware: requesting iwlwifi-5000-2.ucode
Oct 21 01:59:01 user-laptop kernel: [ 2067.434605] iwlagn 0000:08:00.0: loaded firmware version 8.24.2.12
Oct 21 01:59:01 user-laptop kernel: [ 2067.588147] Registered led device: iwl-phy1::radio
Oct 21 01:59:01 user-laptop kernel: [ 2067.588638] Registered led device: iwl-phy1::assoc
Oct 21 01:59:01 user-laptop kernel: [ 2067.588779] Registered led device: iwl-phy1::RX
Oct 21 01:59:01 user-laptop kernel: [ 2067.589194] Registered led device: iwl-phy1::TX
Oct 21 01:59:01 user-laptop kernel: [ 2067.633969] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 21 01:59:12 user-laptop kernel: [ 2078.496948] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct 21 01:59:15 user-laptop kernel: [ 2081.060403] iwlagn 0000:08:00.0: iwl_tx_agg_start on ra = 00:0f:7d:1d:49:11 tid = 0
  
^C
user@user-laptop:/$ 

```
There's something that isnt working, evidently. After a few seconds the network manager applet connects wirelessly to the network (remember I am in my dorm, the only place that I can connect wirelessly on campus).
I dont think network manager is removed, I should try removing it again, maybe I should kill processes before unloading the drivers?

---

### Post by utilitytrack on 2010-10-21
```
ERROR: Removing 'iwlcore': Operation not permitted
```

It's strange, really. But anyway, before we will connect to network, driver should be completely unloaded and then load again. So try this: become root,
```
$ sudo su
```

and now
```
# rmmod -v iwlagn
# rmmod -v iwlcore 
# rmmod -v mac80211 
# rmmod -v cfg80211
```

> **erjoalgo said:**
> After a few seconds the network manager applet connects wirelessly to the network 

OMG.

> **erjoalgo said:**
> remember I am in my dorm, the only place that I can connect wirelessly on campus
It's very good. Please stay there.

> **erjoalgo said:**
> I dont think network manager is removed, I should try removing it again, maybe I should kill processes before unloading the drivers?

You should shut down NM. Do you understand this? Beat him with a hammer :) Actually, why you can not uninstall it? Provide logs, I will tell what need to do.

PS
All what you will do next, you should do from root only.

---

### Post by utilitytrack on 2010-10-21
**erjoalgo**,

I may advice you go to terminal (Ctrl+Alt+F1) and do all work there. Also this will be useful so you have not been tempted to use network manager.

---

### Post by erjoalgo on 2010-10-21
Ok, now I did get rid of network manager. It was asking me to resolve dependencies by installing the same packages I was trying to uninstall, and apparently I was agreeing to resolve those dependencies.
Now NM is definitely out. And yeah, I've been running these commands as root. And I dont know how else I would do those commands outside from the terminal ;).
```

user@user-laptop:/$ sudo su
[sudo] password for user: 
root@user-laptop:/# rmmod -v iwlagn
rmmod iwlagn, wait=no
root@user-laptop:/# rmmod -v iwlcore
rmmod iwlcore, wait=no
root@user-laptop:/# rmmod -v mac80211
rmmod mac80211, wait=no
root@user-laptop:/# rmmod -v cfg80211
rmmod cfg80211, wait=no
root@user-laptop:/# aptitude purge network-manager network-manager-pptp network-manager-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  network-manager-pptp-gnome 
The following packages will be REMOVED:
  network-manager{p} network-manager-gnome{p} network-manager-pptp{p} 
0 packages upgraded, 0 newly installed, 3 to remove and 47 not upgraded.
Need to get 0B of archives. After unpacking 8,393kB will be freed.
The following packages have unmet dependencies:
  network-manager-pptp-gnome: Depends: network-manager-pptp but it is not installable
The following actions will resolve these dependencies:

Remove the following packages:
network-manager-pptp-gnome

Leave the following dependencies unresolved:
ubuntu-desktop recommends network-manager-gnome
ubuntu-desktop recommends network-manager-pptp
ubuntu-desktop recommends network-manager-pptp-gnome
Score is -481

Accept this solution? [Y/n/q/?] 
The following packages will be REMOVED:
  network-manager{p} network-manager-gnome{p} network-manager-pptp{p} 
  network-manager-pptp-gnome{a} 
0 packages upgraded, 0 newly installed, 4 to remove and 47 not upgraded.
Need to get 0B of archives. After unpacking 8,647kB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
(Reading database ... 261379 files and directories currently installed.)
Removing network-manager-gnome ...
Purging configuration files for network-manager-gnome ...
Removing network-manager ...
network-manager stop/waiting
Purging configuration files for network-manager ...
dpkg: warning: while removing network-manager, directory '/var/lib/NetworkManager' not empty so not removed.
dpkg: warning: while removing network-manager, directory '/etc/NetworkManager/system-connections' not empty so not removed.
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
(Reading database ... 261238 files and directories currently installed.)
Removing network-manager-pptp-gnome ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 261224 files and directories currently installed.)
Removing network-manager-pptp ...
Purging configuration files for network-manager-pptp ...
dpkg: warning: while removing network-manager-pptp, directory '/etc/NetworkManager' not empty so not removed.
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

root@user-laptop:/#

```
Whats the next step?

---

### Post by utilitytrack on 2010-10-21
Well done. Finally.

Next step is accurately load driver and to see how it been made. 
From root, don't forget.

First delete your old settings
```
# rm /etc/network/interfaces
```

Now insert module into kernel.
```
# logger MARK
# modprobe -v iwlagn
# tail -n 20 -f /var/log/kern.log
```

Please post output here.

---

### Post by erjoalgo on 2010-10-21
Done
```

user@user-laptop:/etc/network$ sudo rm interfaces
[sudo] password for user: 
user@user-laptop:/etc/network$ ls
if-down.d  if-post-down.d  if-pre-up.d  if-up.d  interfaces~
user@user-laptop:/etc/network$ sudo logger MARK
user@user-laptop:/etc/network$ sudo modprobe -v iwlagn
insmod /lib/modules/2.6.32-25-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/2.6.32-25-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/2.6.32-25-generic/kernel/drivers/net/wireless/iwlwifi/iwlcore.ko 
insmod /lib/modules/2.6.32-25-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko 
user@user-laptop:/etc/network$ sudo tail -n 20 -f /var/log/kern.log
Oct 21 06:52:07 user-laptop kernel: [10100.565543] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Oct 21 06:52:18 user-laptop kernel: [10111.232550] eth0: no IPv6 routers present
Oct 21 07:17:46 user-laptop kernel: [11639.873075] r8169: eth0: link down
Oct 21 07:17:48 user-laptop kernel: [11641.409326] r8169: eth0: link up
Oct 21 07:23:13 user-laptop kernel: [11966.391484] cfg80211: Calling CRDA to update world regulatory domain
Oct 21 07:23:13 user-laptop kernel: [11966.574431] cfg80211: World regulatory domain updated:
Oct 21 07:23:13 user-laptop kernel: [11966.574440] 		 (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Oct 21 07:23:13 user-laptop kernel: [11966.574448] 		 (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 21 07:23:13 user-laptop kernel: [11966.574455] 		 (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct 21 07:23:13 user-laptop kernel: [11966.574461] 		 (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct 21 07:23:13 user-laptop kernel: [11966.574467] 		 (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 21 07:23:13 user-laptop kernel: [11966.574474] 		 (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 21 07:23:13 user-laptop kernel: [11966.620130] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Oct 21 07:23:13 user-laptop kernel: [11966.620132] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Oct 21 07:23:13 user-laptop kernel: [11966.620244] iwlagn 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Oct 21 07:23:13 user-laptop kernel: [11966.620276] iwlagn 0000:08:00.0: setting latency timer to 64
Oct 21 07:23:13 user-laptop kernel: [11966.620354] iwlagn 0000:08:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
Oct 21 07:23:13 user-laptop kernel: [11966.659814] iwlagn 0000:08:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Oct 21 07:23:13 user-laptop kernel: [11966.659891] iwlagn 0000:08:00.0: irq 33 for MSI/MSI-X
Oct 21 07:23:13 user-laptop kernel: [11966.660206] phy0: Selected rate control algorithm 'iwl-agn-rs'
^C
user@user-laptop:/etc/network$ 

```

---

### Post by utilitytrack on 2010-10-21
Ok, fill out the interfaces file
```
# nano /etc/network/interfaces
```

Write in file only three strings (third is empty):
```
auto lo
iface lo inet loopback

```

Save. Then reload network subsystem:
```
# /etc/init.d/networking restart
```

Show here output of
```
# ifconfig
# iwconfig

```

---

### Post by erjoalgo on 2010-10-21
Done
```

user@user-laptop:/etc/network$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                              Ignoring unknown interface eth0=eth0.
                                                                                             [ OK ]
user@user-laptop:/etc/network$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:e8:d0:6f:8b  
          inet addr:128.237.66.218  Bcast:128.237.67.255  Mask:255.255.252.0
          inet6 addr: fe80::224:e8ff:fed0:6f8b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64094 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32707 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:61455996 (61.4 MB)  TX bytes:6161120 (6.1 MB)
          Interrupt:32 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:580 errors:0 dropped:0 overruns:0 frame:0
          TX packets:580 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:48544 (48.5 KB)  TX bytes:48544 (48.5 KB)

user@user-laptop:/etc/network$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
user@user-laptop:/etc/network$ 

```
I'll thank you again for your time.

---

### Post by utilitytrack on 2010-10-21
> **erjoalgo said:**
> ```

user@user-laptop:/etc/network$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:e8:d0:6f:8b  
          inet addr:128.237.66.218  Bcast:128.237.67.255  Mask:255.255.252.0
          inet6 addr: fe80::224:e8ff:fed0:6f8b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64094 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32707 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:61455996 (61.4 MB)  TX bytes:6161120 (6.1 MB)
          Interrupt:32 Base address:0xc000 


```

WTF? Show contents of /etc/network/interfaces file and output of $ ps waux

---

### Post by erjoalgo on 2010-10-21
Well, since I have no wireless, I am currently connected through eth0. Should I disconnect from this? What is strange about that ifconfig.
```

user@user-laptop:~/wifiProblem$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
user@user-laptop:~/wifiProblem$ ps waux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0  23688  1256 ?        Ss   01:24   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    01:24   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    01:24   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S    01:24   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S    01:24   0:00 [watchdog/0]
root         9  0.0  0.0      0     0 ?        S    01:24   0:00 [events/0]
root        11  0.0  0.0      0     0 ?        S    01:24   0:00 [cpuset]
root        12  0.0  0.0      0     0 ?        S    01:24   0:00 [khelper]
root        13  0.0  0.0      0     0 ?        S    01:24   0:00 [netns]
root        14  0.0  0.0      0     0 ?        S    01:24   0:00 [async/mgr]
root        15  0.0  0.0      0     0 ?        S    01:24   0:00 [pm]
root        17  0.0  0.0      0     0 ?        S    01:24   0:00 [sync_supers]
root        18  0.0  0.0      0     0 ?        S    01:24   0:00 [bdi-default]
root        19  0.0  0.0      0     0 ?        S    01:24   0:00 [kintegrityd/0]
root        21  0.0  0.0      0     0 ?        S    01:24   0:00 [kblockd/0]
root        23  0.0  0.0      0     0 ?        S    01:24   0:00 [kacpid]
root        24  0.0  0.0      0     0 ?        S    01:24   0:00 [kacpi_notify]
root        25  0.0  0.0      0     0 ?        S    01:24   0:00 [kacpi_hotplug]
root        26  0.0  0.0      0     0 ?        S    01:24   0:00 [ata/0]
root        28  0.0  0.0      0     0 ?        S    01:24   0:00 [ata_aux]
root        29  0.0  0.0      0     0 ?        S    01:24   0:00 [ksuspend_usbd]
root        30  0.0  0.0      0     0 ?        S    01:24   0:00 [khubd]
root        31  0.0  0.0      0     0 ?        S    01:24   0:00 [kseriod]
root        32  0.0  0.0      0     0 ?        S    01:24   0:00 [kmmcd]
root        35  0.0  0.0      0     0 ?        S    01:24   0:00 [khungtaskd]
root        36  0.0  0.0      0     0 ?        S    01:24   0:00 [kswapd0]
root        37  0.0  0.0      0     0 ?        SN   01:24   0:00 [ksmd]
root        38  0.0  0.0      0     0 ?        S    01:24   0:00 [aio/0]
root        40  0.0  0.0      0     0 ?        S    01:24   0:00 [ecryptfs-kthrea]
root        41  0.0  0.0      0     0 ?        S    01:24   0:00 [crypto/0]
root        54  0.0  0.0      0     0 ?        S    01:24   0:00 [kstriped]
root        55  0.0  0.0      0     0 ?        S    01:24   0:00 [kmpathd/0]
root        57  0.0  0.0      0     0 ?        S    01:24   0:00 [kmpath_handlerd]
root        58  0.0  0.0      0     0 ?        S    01:24   0:00 [ksnapd]
root        59  0.0  0.0      0     0 ?        S    01:24   0:08 [kondemand/0]
root        61  0.0  0.0      0     0 ?        S    01:24   0:00 [kconservative/0]
root       241  0.0  0.0      0     0 ?        S    01:24   0:00 [scsi_eh_0]
root       273  0.0  0.0      0     0 ?        S    01:24   0:00 [scsi_eh_1]
root       296  0.0  0.0      0     0 ?        S    01:24   0:00 [scsi_eh_2]
root       297  0.0  0.0      0     0 ?        S    01:24   0:00 [scsi_eh_3]
root       302  0.0  0.0      0     0 ?        S    01:24   0:00 [khpsbpkt]
root       303  0.0  0.0      0     0 ?        S    01:24   0:00 [scsi_eh_4]
root       304  0.0  0.0      0     0 ?        S    01:24   0:01 [scsi_eh_5]
root       320  0.0  0.0      0     0 ?        S    01:24   0:00 [knodemgrd_0]
root       339  0.0  0.0      0     0 ?        S    01:24   0:00 [jbd2/sda6-8]
root       340  0.0  0.0      0     0 ?        S    01:24   0:00 [ext4-dio-unwrit]
root       374  0.0  0.0      0     0 ?        S    01:24   0:00 [flush-8:0]
root       400  0.0  0.0  17036   644 ?        S    01:24   0:00 upstart-udev-bridge --daemon
root       402  0.0  0.0  17460   392 ?        S<s  01:24   0:00 udevd --daemon
root       720  0.0  0.0      0     0 ?        S    01:24   0:00 [kpsmoused]
root       796  0.0  0.0      0     0 ?        S    01:24   0:00 [hd-audio0]
root       817  0.0  0.0  94296   260 ?        Ss   01:24   0:00 smbd -F
syslog     838  0.0  0.0 126616   916 ?        Sl   01:24   0:00 rsyslogd -c4
102        840  0.0  0.0  24504  2004 ?        Ss   01:24   0:03 dbus-daemon --system --fork
root       844  0.0  0.0  49260    12 ?        Ss   01:24   0:052000
user  1534  0.0  0.0 186680  3492 ?        S    01:25   0:00 /usr/lib/vino/vino-server --sm-disable
user  1535  0.0  0.0 164140  1420 ?        S    01:25   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
user  1538  0.0  0.3 760108 14940 ?        SLl  01:25   0:10 rhythmbox --sm-client-id 102febfafc987e97d7128746253749691300000015
user  1541  0.0  0.2 515520 10052 ?        S    01:25   0:01 nautilus --sm-client-id 1061ce56e6664eb5ea1284025762781516000000149
user  1543  0.0  0.2 353196 11724 ?        Sl   01:25   0:03 evince --sm-client-id 10bbbda73962e6ec39128746850349793600000014450
user  1544  0.0  0.0 374828  3696.0  0.0 138460   920 ?        S    01:25   0:00 /usr/lib/indicator-messages/indicator-messages-service
user  1650  0.0  0.0 143976   964 ?        S    01:25   0:00 /usr/lib/indicator-me/indicator-me-service
user  1652  0.0  0.0 140908  1648 ?        S    01:25   0:00 /usr/lib/indicator-session/indicator-session-service
user  1662  0.0  0.0  47864    16 ?        S    01:25   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.6 /org/gtk/gvfs/exec_spaw/1
user  1684  0.0  0.2 222668  9744 ? 01 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fiel
user  5247  0.1  0.3 214376 15868 ?        S    06:22   0:11 /usr/games/mahjongg
user  5248  0.0  0.0 132696  1224 ?        S    06:22   0:00 /usr/games/mahjongg
user  5269  0.1  0.5 856660 23112 ?        SNl  06:24   0:12 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fiel
user  5345  0.0  1.3 310244 54888 ?        SN   06:25   0:04 /usr/bin/python2.6 /usr/bin/update-manager --no-focus-on-map
user  5621  0.8  2.0 938488 81168 ?        SNl  06:47   0:44 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fiel
user  5689  0.1  0.4 229308 17588 ?        Rl   06:49   0:06 gnome-terminal --geometry=100x20+300+200
user  5690  0.0  0.0  14488   816 ?        S    06:50   0:00 gnome-pty-helper
user  5691  0.0  0.1  21400  4200 pts/0    Ss   06:50   0:00 bash
root      5710  0.0  0.0  97744  2896 pts/0    S    06:50   0:00 su
root      5719  0.0  0.0  19380  2144 pts/0    S+   06:50   0:00 bash
root      5733  0.0  0.0

```

---

### Post by utilitytrack on 2010-10-21
> **erjoalgo said:**
> Well, since I have no wireless, I am currently connected through eth0. Should I disconnect from this?

No, if so. 

Next, try this, wait after first command one minute and post here the log.
```
# ifconfig wlan0 up
# ifconfig
# tail -n 20 -f /var/log/kern.log
```

---

### Post by erjoalgo on 2010-10-21
```
user@user-laptop:/$ sudo ifconfig wlan0 up
[sudo] password for user: 
user@user-laptop:/$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:e8:d0:6f:8b  
          inet addr:128.237.66.218  Bcast:128.237.67.255  Mask:255.255.252.0
          inet6 addr: fe80::224:e8ff:fed0:6f8b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:99759 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49610 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:87838061 (87.8 MB)  TX bytes:10282276 (10.2 MB)
          Interrupt:32 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:606 errors:0 dropped:0 overruns:0 frame:0
          TX packets:606 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:51892 (51.8 KB)  TX bytes:51892 (51.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:d6:0c:f2:44  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

user@user-laptop:/$ tail -n 20 -f /var/log/kern.log
Oct 21 07:23:13 user-laptop kernel: [11966.574455]	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct 21 07:23:13 user-laptop kernel: [11966.574461] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct 21 07:23:13 user-laptop kernel: [11966.574467] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 21 07:23:13 user-laptop kernel: [11966.574474] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 21 07:23:13 user-laptop kernel: [11966.620130] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Oct 21 07:23:13 user-laptop kernel: [11966.620132] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Oct 21 07:23:13 user-laptop kernel: [11966.620244] iwlagn 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Oct 21 07:23:13 user-laptop kernel: [11966.620276] iwlagn 0000:08:00.0: setting latency timer to 64
Oct 21 07:23:13 user-laptop kernel: [11966.620354] iwlagn 0000:08:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
Oct 21 07:23:13 user-laptop kernel: [11966.659814] iwlagn 0000:08:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Oct 21 07:23:13 user-laptop kernel: [11966.659891] iwlagn 0000:08:00.0: irq 33 for MSI/MSI-X
Oct 21 07:23:13 user-laptop kernel: [11966.660206] phy0: Selected rate control algorithm 'iwl-agn-rs'
Oct 21 07:51:27 user-laptop kernel: [13661.000012] CE: hpet increasing min_delta_ns to 22500 nsec
Oct 21 08:39:17 user-laptop kernel: [16530.246445] iwlagn 0000:08:00.0: firmware: requesting iwlwifi-5000-2.ucode
Oct 21 08:39:17 user-laptop kernel: [16530.291215] iwlagn 0000:08:00.0: loaded firmware version 8.24.2.12
Oct 21 08:39:17 user-laptop kernel: [16530.455056] Registered led device: iwl-phy0::radio
Oct 21 08:39:17 user-laptop kernel: [16530.455191] Registered led device: iwl-phy0::assoc
Oct 21 08:39:17 user-laptop kernel: [16530.455718] Registered led device: iwl-phy0::RX
Oct 21 08:39:17 user-laptop kernel: [16530.455876] Registered led device: iwl-phy0::TX
Oct 21 08:39:17 user-laptop kernel: [16530.492277] ADDRCONF(NETDEV_UP): wlan0: link is not ready
^C
user@user-laptop:/$ 

```

---

### Post by utilitytrack on 2010-10-21
Please, now again
```
# tail -n 30 -f /var/log/kern.log
$ ifconfig -a
```

Also
```
$ cat /etc/udev/rules.d/70-persistent-net.rules
```

> **erjoalgo said:**
> Well, since I have no wireless, I am currently connected through eth0. Should I disconnect from this?

I re-read your previous post. First, you previously was connected the same way, through cable. Or not? Second, we are talking about one and the same machine? Do you can say definitely? Because earlier you wrote this:

> **erjoalgo said:**
> Sorry for the delay, I was at school, having to use Windows OS in order to get Internet access.

If so, then it's doesn't matter how connected your Linux box. If it's still the same machine, then your **/etc/network/interfaces** file should look like:
```
# loopback
auto lo
iface lo inet loopback

# wired network setup
auto eth0
iface eth0 inet dhcp
```

And for connect to your local network use this:
```
# ifup -v eth0
```

---

### Post by erjoalgo on 2010-10-21
Excuse the delay, I had class.
I now rebooted, do I have to unload the drivers again? 

Just to clarify:
It is the same machine, my laptop.
Windows: ethernet + wireless works
Ubuntu: ethernet works
Ubuntu: wireless works only on my dorm, when on campus, I dont get IP assigned

Before removing network manager, I was using wireless in my dorm near my dorm, after removing it, I used ethernet chord.

---

### Post by erjoalgo on 2010-10-21
Ok, I understand what you were saying. My ethernet broke, now the last "interfaces" file fixed it. How to connect to wifi?
Output of last commands.
```

user@user-laptop:~/wifiProblem$ sudo tail -n 30 -f /var/log/kern.log
Oct 21 16:43:49 user-laptop kernel: [   15.863246] type=1505 audit(1287693829.439:7):  operation="profile_replace" pid=885 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Oct 21 16:43:49 user-laptop kernel: [   15.863537] type=1505 audit(1287693829.439:8):  operation="profile_replace" pid=885 name="/usr/lib/connman/scripts/dhclient-script"
Oct 21 16:43:49 user-laptop kernel: [   15.870524] type=1505 audit(1287693829.449:9):  operation="profile_load" pid=886 name="/usr/bin/evince"
Oct 21 16:43:49 user-laptop kernel: [   15.877404] type=1505 audit(1287693829.449:10):  operation="profile_load" pid=886 name="/usr/bin/evince-previewer"
Oct 21 16:43:49 user-laptop kernel: [   15.883918] type=1505 audit(1287693829.459:11):  operation="profile_load" pid=886 name="/usr/bin/evince-thumbnailer"
Oct 21 16:43:50 user-laptop kernel: [   16.993422] vboxdrv: Trying to deactivate the NMI watchdog permanently...
Oct 21 16:43:50 user-laptop kernel: [   16.993424] vboxdrv: Successfully done.
Oct 21 16:43:50 user-laptop kernel: [   16.993426] vboxdrv: Found 2 processor cores.
Oct 21 16:43:50 user-laptop kernel: [   16.993821] VBoxDrv: dbg - g_abExecMemory=ffffffffa051ba20
Oct 21 16:43:50 user-laptop kernel: [   16.994512] vboxdrv: fAsync=0 offMin=0x139 offMax=0x147c
Oct 21 16:43:50 user-laptop kernel: [   16.994679] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Oct 21 16:43:50 user-laptop kernel: [   16.994681] vboxdrv: Successfully loaded version 3.1.6_OSE (interface 0x00100001).
Oct 21 16:43:50 user-laptop kernel: [   16.999097] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1e0b1, caps: 0xd04731/0xa40000
Oct 21 16:43:50 user-laptop kernel: [   17.091692] ppdev: user-space parallel port driver
Oct 21 16:43:50 user-laptop kernel: [   17.160197] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input12
Oct 21 16:43:50 user-laptop kernel: [   17.239040]   alloc irq_desc for 34 on node -1
Oct 21 16:43:50 user-laptop kernel: [   17.239043]   alloc kstat_irqs on node -1
Oct 21 16:43:50 user-laptop kernel: [   17.239054] fglrx_pci 0000:01:00.0: irq 34 for MSI/MSI-X
Oct 21 16:43:50 user-laptop kernel: [   17.239525] [fglrx] Firegl kernel thread PID: 1259
Oct 21 16:43:50 user-laptop kernel: [   17.239720] [fglrx] IRQ 34 Enabled
Oct 21 16:43:52 user-laptop kernel: [   18.677258] [fglrx] Gart USWC size:1236 M.
Oct 21 16:43:52 user-laptop kernel: [   18.677261] [fglrx] Gart cacheable size:491 M.
Oct 21 16:43:52 user-laptop kernel: [   18.677265] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Oct 21 16:43:52 user-laptop kernel: [   18.677267] [fglrx] Reserved FB block: Unshared offset:fc21000, size:3df000 
Oct 21 16:43:52 user-laptop kernel: [   18.677269] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
Oct 21 16:44:00 user-laptop kernel: [   27.079127] lo: Disabled Privacy Extensions
Oct 21 16:44:02 user-laptop kernel: [   28.466905] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Oct 21 16:46:50 user-laptop kernel: [  196.895927] r8169: eth0: link up
Oct 21 16:46:50 user-laptop kernel: [  196.895947] r8169: eth0: link up
Oct 21 16:47:00 user-laptop kernel: [  207.620038] eth0: no IPv6 routers present
^C
user@user-laptop:~/wifiProblem$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:24:e8:d0:6f:8b  
          inet addr:128.237.66.218  Bcast:128.237.67.255  Mask:255.255.252.0
          inet6 addr: fe80::224:e8ff:fed0:6f8b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5051 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1816 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2280781 (2.2 MB)  TX bytes:349238 (349.2 KB)
          Interrupt:31 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:41 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4224 (4.2 KB)  TX bytes:4224 (4.2 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:24:d6:0c:f2:44  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

user@user-laptop:~/wifiProblem$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:24:e8:d0:6f:8b", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4232 (iwlagn)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:24:d6:0c:f2:44", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
user@user-laptop:~/wifiProblem$

```

---

### Post by utilitytrack on 2010-10-22
Ok, if so, then reload driver (see above); next try this:
```
# iwconfig
# ifconfig wlan0 up
```

Through one minute
```
# ifconfig -a
# iwlist scan
# tail -n 30 -f /var/log/kern.log
```

Cut from kern.log that you give last time is irrelevant.

---

### Post by erjoalgo on 2010-10-22
```

Script started on Fri 22 Oct 2010 10:05:51 AM EDT
user-laptop:/# iKwconfig
lo	  no wireless extensions.

eth0	  no wireless extensions.

wlan0	  IEEE 802.11abgn  ESSID:off/any
	  Mode:Managed	Access Point: Not-Associated   Tx-Power=15 dBm
	  Retry  long limit:7	RTS thr:off   Fragment thr:off
	  Encryption key:off
	  Power Management:off

vboxnet0  no wireless extensions.

user-laptop:/# ifconfig wlan0 up
user-laptop:/# ifconfig -a
eth0	  Link encap:Ethernet  HWaddr 00:24:e8:d0:6f:8b
	  inet addr:128.237.66.218  Bcast:128.237.67.255  Mask:255.255.252.0
	  inet6 addr: fe80::224:e8ff:fed0:6f8b/64 Scope:Link
	  UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
	  RX packets:48498 errors:0 dropped:0 overruns:0 frame:0
	  TX packets:19162 errors:0 dropped:0 overruns:0 carrier:0
	  collisions:0 txqueuelen:1000
	  RX bytes:24659411 (24.6 MB)  TX bytes:3197718 (3.1 MB)
	  Interrupt:31

lo	  Link encap:Local Loopback
	  inet addr:127.0.0.1  Mask:255.0.0.0
	  inet6 addr: ::1/128 Scope:Host
	  UP LOOPBACK RUNNING  MTU:16436  Metric:1
	  RX packets:12 errors:0 dropped:0 overruns:0 frame:0
	  TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
	  collisions:0 txqueuelen:0
	  RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00
	  BROADCAST MULTICAST  MTU:1500  Metric:1
	  RX packets:0 errors:0 dropped:0 overruns:0 frame:0
	  TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
	  collisions:0 txqueuelen:1000
	  RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0	  Link encap:Ethernet  HWaddr 00:24:d6:0c:f2:44
	  UP BROADCAST MULTICAST  MTU:1500  Metric:1
	  RX packets:0 errors:0 dropped:0 overruns:0 frame:0
	  TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
	  collisions:0 txqueuelen:1000
	  RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

user-laptop:/# iwlist scan
lo	  Interface doesn't support scanning.

eth0	  Interface doesn't support scanning.

wlan0	  Scan completed :
	  Cell 01 - Address: 00:0F:7D:09:93:D1
		    Channel:1
		    Frequency:2.412 GHz (Channel 1)
		    Quality=48/70  Signal level=-62 dBm
		    Encryption key:off
		    ESSID:"CMU"
		    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
			      11 Mb/s; 12 Mb/s; 18 Mb/s
		    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
		    Mode:Master
		    Extra:tsf=00000391bbb48fcb
		    Extra: Last beacon: 2940ms ago
		    IE: Unknown: 0003434D55
		    IE: Unknown: 010882848B0C12961824
		    IE: Unknown: 030101
		    IE: Unknown: 2A0102
		    IE: Unknown: 32043048606C
		    IE: Unknown: DD180050F2020101020003A5000027A5000042545E0062432F00
		    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: 3D1601080800000000000000000000000000000000000000
		    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: DD1A00904C3401080800000000000000000000000000000000000000
	  Cell 02 - Address: 00:0F:7D:1D:49:51
		    Channel:1
		    Frequency:2.412 GHz (Channel 1)
		    Quality=63/70  Signal level=-47 dBm
		    Encryption key:off
		    ESSID:"CMU"
		    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
			      11 Mb/s; 12 Mb/s; 18 Mb/s
		    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
		    Mode:Master
		    Extra:tsf=00000391bd402de7
		    Extra: Last beacon: 2930ms ago
		    IE: Unknown: 0003434D55
		    IE: Unknown: 010882848B0C12961824
		    IE: Unknown: 030101
		    IE: Unknown: 2A0102
		    IE: Unknown: 32043048606C
		    IE: Unknown: DD180050F2020101020003A5000027A5000042545E0062432F00
		    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: 3D1601001B00000000000000000000000000000000000000
		    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: DD1A00904C3401001B00000000000000000000000000000000000000
	  Cell 03 - Address: 00:0F:7D:09:93:F1
		    Channel:6
		    Frequency:2.437 GHz (Channel 6)
		    Quality=58/70  Signal level=-52 dBm
		    Encryption key:off
		    ESSID:"CMU"
		    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
			      11 Mb/s; 12 Mb/s; 18 Mb/s
		    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
		    Mode:Master
		    Extra:tsf=00000391bbb7ef85
		    Extra: Last beacon: 2740ms ago
		    IE: Unknown: 0003434D55
		    IE: Unknown: 010882848B0C12961824
		    IE: Unknown: 030106
		    IE: Unknown: 2A0102
		    IE: Unknown: 32043048606C
		    IE: Unknown: DD180050F2020101020003A5000027A5000042545E0062432F00
		    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: 3D1606080800000000000000000000000000000000000000
		    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: DD1A00904C3406080800000000000000000000000000000000000000
	  Cell 04 - Address: 00:0F:7D:1C:CA:F1
		    Channel:6
		    Frequency:2.437 GHz (Channel 6)
		    Quality=42/70  Signal level=-68 dBm
		    Encryption key:off
		    ESSID:"CMU"
		    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
			      11 Mb/s; 12 Mb/s; 18 Mb/s
		    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
		    Mode:Master
		    Extra:tsf=00000391bc70adb1
		    Extra: Last beacon: 2750ms ago
		    IE: Unknown: 0003434D55
		    IE: Unknown: 010882848B0C12961824
		    IE: Unknown: 030106
		    IE: Unknown: 2A0102
		    IE: Unknown: 32043048606C
		    IE: Unknown: DD180050F2020101020003A5000027A5000042545E0062432F00
		    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
		    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: DD1A00904C3406001B00000000000000000000000000000000000000
	  Cell 05 - Address: 00:0F:7D:1D:49:71
		    Channel:6
		    Frequency:2.437 GHz (Channel 6)
		    Quality=29/70  Signal level=-81 dBm
		    Encryption key:off
		    ESSID:"CMU"
		    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
			      11 Mb/s; 12 Mb/s; 18 Mb/s
		    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
		    Mode:Master
		    Extra:tsf=00000391bd44fc13
		    Extra: Last beacon: 2640ms ago
		    IE: Unknown: 0003434D55
		    IE: Unknown: 010882848B0C12961824
		    IE: Unknown: 030106
		    IE: Unknown: 2A0102
		    IE: Unknown: 32043048606C
		    IE: Unknown: DD180050F2020101020003A5000027A5000042545E0062432F00
		    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
		    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: DD1A00904C3406001B00000000000000000000000000000000000000
	  Cell 06 - Address: 00:0F:7D:1C:CA:D1
		    Channel:11
		    Frequency:2.462 GHz (Channel 11)
		    Quality=47/70  Signal level=-63 dBm
		    Encryption key:off
		    ESSID:"CMU"
		    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
			      11 Mb/s; 12 Mb/s; 18 Mb/s
		    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
		    Mode:Master
		    Extra:tsf=00000391bc735182
		    Extra: Last beacon: 2560ms ago
		    IE: Unknown: 0003434D55
		    IE: Unknown: 010882848B0C12961824
		    IE: Unknown: 03010B
		    IE: Unknown: 2A0102
		    IE: Unknown: 32043048606C
		    IE: Unknown: DD180050F2020101020003A5000027A5000042545E0062432F00
		    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: 3D160B080800000000000000000000000000000000000000
		    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: DD1A00904C340B080800000000000000000000000000000000000000
	  Cell 07 - Address: 00:0F:7D:09:93:91
		    Channel:11
		    Frequency:2.462 GHz (Channel 11)
		    Quality=63/70  Signal level=-47 dBm
		    Encryption key:off
		    ESSID:"CMU"
		    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
			      11 Mb/s; 12 Mb/s; 18 Mb/s
		    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
		    Mode:Master
		    Extra:tsf=00000391bbb7dad5
		    Extra: Last beacon: 2670ms ago
		    IE: Unknown: 0003434D55
		    IE: Unknown: 010882848B0C12961824
		    IE: Unknown: 03010B
		    IE: Unknown: 2A0102
		    IE: Unknown: 32043048606C
		    IE: Unknown: DD180050F2020101020003A5000027A5000042545E0062432F00
		    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
		    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: DD1A00904C340B001B00000000000000000000000000000000000000
	  Cell 08 - Address: 00:0F:7D:1D:49:11
		    Channel:11
		    Frequency:2.462 GHz (Channel 11)
		    Quality=69/70  Signal level=-41 dBm
		    Encryption key:off
		    ESSID:"CMU"
		    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
			      11 Mb/s; 12 Mb/s; 18 Mb/s
		    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
		    Mode:Master
		    Extra:tsf=00000391bd446943
		    Extra: Last beacon: 2600ms ago
		    IE: Unknown: 0003434D55
		    IE: Unknown: 010882848B0C12961824
		    IE: Unknown: 03010B
		    IE: Unknown: 2A0102
		    IE: Unknown: 32043048606C
		    IE: Unknown: DD180050F2020101020003A5000027A5000042545E0062432F00
		    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: 3D160B080800000000000000000000000000000000000000
		    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: DD1A00904C340B080800000000000000000000000000000000000000
	  Cell 09 - Address: 00:0F:7D:09:75:51
		    Channel:11
		    Frequency:2.462 GHz (Channel 11)
		    Quality=38/70  Signal level=-72 dBm
		    Encryption key:off
		    ESSID:"CMU"
		    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
			      11 Mb/s; 12 Mb/s; 18 Mb/s
		    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
		    Mode:Master
		    Extra:tsf=0000080327141e70
		    Extra: Last beacon: 2670ms ago
		    IE: Unknown: 0003434D55
		    IE: Unknown: 010882848B0C12961824
		    IE: Unknown: 03010B
		    IE: Unknown: 2A0102
		    IE: Unknown: 32043048606C
		    IE: Unknown: DD180050F2020101020003A5000027A5000042545E0062432F00
		    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
		    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: DD1A00904C340B001B00000000000000000000000000000000000000
	  Cell 10 - Address: 00:0F:7D:09:93:C1
		    Channel:36
		    Frequency:5.18 GHz (Channel 36)
		    Quality=31/70  Signal level=-79 dBm
		    Encryption key:off
		    ESSID:"CMU"
		    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
			      36 Mb/s; 48 Mb/s; 54 Mb/s
		    Mode:Master
		    Extra:tsf=00000391bbbccadb
		    Extra: Last beacon: 2390ms ago
		    IE: Unknown: 0003434D55
		    IE: Unknown: 01088C129824B048606C
		    IE: Unknown: 030124
		    IE: Unknown: DD180050F2020101020003A5000027A5000042545E0062432F00
		    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: 3D16240D0800000000000000000000000000000000000000
		    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: DD1A00904C34240D0800000000000000000000000000000000000000
	  Cell 11 - Address: 00:0F:7D:1D:49:61
		    Channel:36
		    Frequency:5.18 GHz (Channel 36)
		    Quality=41/70  Signal level=-69 dBm
		    Encryption key:off
		    ESSID:"CMU"
		    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
			      36 Mb/s; 48 Mb/s; 54 Mb/s
		    Mode:Master
		    Extra:tsf=00000391bd48a220
		    Extra: Last beacon: 2390ms ago
		    IE: Unknown: 0003434D55
		    IE: Unknown: 01088C129824B048606C
		    IE: Unknown: 030124
		    IE: Unknown: DD180050F2020101020003A5000027A5000042545E0062432F00
		    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: 3D16240D0800000000000000000000000000000000000000
		    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: DD1A00904C34240D0800000000000000000000000000000000000000
	  Cell 12 - Address: 00:0F:7D:1D:49:41
		    Channel:56
		    Frequency:5.28 GHz (Channel 56)
		    Quality=44/70  Signal level=-66 dBm
		    Encryption key:off
		    ESSID:"CMU"
		    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
			      36 Mb/s; 48 Mb/s; 54 Mb/s
		    Mode:Master
		    Extra:tsf=00000391bd4fb3d2
		    Extra: Last beacon: 1900ms ago
		    IE: Unknown: 0003434D55
		    IE: Unknown: 01088C129824B048606C
		    IE: Unknown: 030138
		    IE: Unknown: DD180050F2020101020003A5000027A5000042545E0062432F00
		    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: 3D16380F0800000000000000000000000000000000000000
		    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: DD1A00904C34380F0800000000000000000000000000000000000000
	  Cell 13 - Address: 00:0F:7D:09:93:81
		    Channel:60
		    Frequency:5.3 GHz (Channel 60)
		    Quality=37/70  Signal level=-73 dBm
		    Encryption key:off
		    ESSID:"CMU"
		    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
			      36 Mb/s; 48 Mb/s; 54 Mb/s
		    Mode:Master
		    Extra:tsf=00000391bbc3dade
		    Extra: Last beacon: 1870ms ago
		    IE: Unknown: 0003434D55
		    IE: Unknown: 01088C129824B048606C
		    IE: Unknown: 03013C
		    IE: Unknown: DD180050F2020101020003A5000027A5000042545E0062432F00
		    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: 3D163C0D0800000000000000000000000000000000000000
		    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: DD1A00904C343C0D0800000000000000000000000000000000000000
	  Cell 14 - Address: 00:0F:7D:1D:49:01
		    Channel:64
		    Frequency:5.32 GHz (Channel 64)
		    Quality=34/70  Signal level=-76 dBm
		    Encryption key:off
		    ESSID:"CMU"
		    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
			      36 Mb/s; 48 Mb/s; 54 Mb/s
		    Mode:Master
		    Extra:tsf=00000391bd5053aa
		    Extra: Last beacon: 1810ms ago
		    IE: Unknown: 0003434D55
		    IE: Unknown: 01088C129824B048606C
		    IE: Unknown: 030140
		    IE: Unknown: DD180050F2020101020003A5000027A5000042545E0062432F00
		    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: 3D16400F0800000000000000000000000000000000000000
		    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: DD1A00904C34400F0800000000000000000000000000000000000000
	  Cell 15 - Address: 00:0F:7D:09:93:A1
		    Channel:153
		    Frequency:5.765 GHz
		    Quality=30/70  Signal level=-80 dBm
		    Encryption key:off
		    ESSID:"CMU"
		    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
			      36 Mb/s; 48 Mb/s; 54 Mb/s
		    Mode:Master
		    Extra:tsf=00000391bbdbf780
		    Extra: Last beacon: 320ms ago
		    IE: Unknown: 0003434D55
		    IE: Unknown: 01088C129824B048606C
		    IE: Unknown: 030199
		    IE: Unknown: DD180050F2020101020003A5000027A5000042545E0062432F00
		    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: 3D16990F0800000000000000000000000000000000000000
		    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: DD1A00904C34990F0800000000000000000000000000000000000000
	  Cell 16 - Address: 00:0F:7D:1D:49:21
		    Channel:157
		    Frequency:5.785 GHz
		    Quality=35/70  Signal level=-75 dBm
		    Encryption key:off
		    ESSID:"CMU"
		    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
			      36 Mb/s; 48 Mb/s; 54 Mb/s
		    Mode:Master
		    Extra:tsf=00000391bd67ff0f
		    Extra: Last beacon: 280ms ago
		    IE: Unknown: 0003434D55
		    IE: Unknown: 01088C129824B048606C
		    IE: Unknown: 03019D
		    IE: Unknown: DD180050F2020101020003A5000027A5000042545E0062432F00
		    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: 3D169D0D0800000000000000000000000000000000000000
		    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: DD1A00904C349D0D0800000000000000000000000000000000000000
	  Cell 17 - Address: 00:0F:7D:09:93:E1
		    Channel:161
		    Frequency:5.805 GHz
		    Quality=33/70  Signal level=-77 dBm
		    Encryption key:off
		    ESSID:"CMU"
		    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
			      36 Mb/s; 48 Mb/s; 54 Mb/s
		    Mode:Master
		    Extra:tsf=00000391bbdef3f4
		    Extra: Last beacon: 170ms ago
		    IE: Unknown: 0003434D55
		    IE: Unknown: 01088C129824B048606C
		    IE: Unknown: 0301A1
		    IE: Unknown: DD180050F2020101020003A5000027A5000042545E0062432F00
		    IE: Unknown: 2D1A4E001BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: 3D16A10F0800000000000000000000000000000000000000
		    IE: Unknown: DD1E00904C334E001BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: DD1A00904C34A10F0800000000000000000000000000000000000000
	  Cell 18 - Address: 00:0F:7D:1C:CA:91
		    Channel:1
		    Frequency:2.412 GHz (Channel 1)
		    Quality=43/70  Signal level=-67 dBm
		    Encryption key:off
		    ESSID:"CMU"
		    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
			      11 Mb/s; 12 Mb/s; 18 Mb/s
		    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
		    Mode:Master
		    Extra:tsf=00000391bc6d4251
		    Extra: Last beacon: 2900ms ago
		    IE: Unknown: 0003434D55
		    IE: Unknown: 010882848B0C12961824
		    IE: Unknown: 030101
		    IE: Unknown: 2A0102
		    IE: Unknown: 32043048606C
		    IE: Unknown: DD180050F2020101020003A5000027A5000042545E0062432F00
		    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: 3D1601080800000000000000000000000000000000000000
		    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: DD1A00904C3401080800000000000000000000000000000000000000
	  Cell 19 - Address: 00:0F:7D:05:E2:F1
		    Channel:1
		    Frequency:2.412 GHz (Channel 1)
		    Quality=31/70  Signal level=-79 dBm
		    Encryption key:off
		    ESSID:"CMU"
		    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
			      11 Mb/s; 12 Mb/s; 18 Mb/s
		    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
		    Mode:Master
		    Extra:tsf=00000391bc722b03
		    Extra: Last beacon: 2910ms ago
		    IE: Unknown: 0003434D55
		    IE: Unknown: 010882848B0C12961824
		    IE: Unknown: 030101
		    IE: Unknown: 050B0001720000000000000000
		    IE: Unknown: 2A0102
		    IE: Unknown: 32043048606C
		    IE: Unknown: DD180050F2020101020003A5000027A5000042545E0062432F00
		    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: 3D1601080800000000000000000000000000000000000000
		    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: DD1A00904C3401080800000000000000000000000000000000000000
	  Cell 20 - Address: 00:0F:7D:09:75:11
		    Channel:1
		    Frequency:2.412 GHz (Channel 1)
		    Quality=33/70  Signal level=-77 dBm
		    Encryption key:off
		    ESSID:"CMU"
		    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
			      11 Mb/s; 12 Mb/s; 18 Mb/s
		    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
		    Mode:Master
		    Extra:tsf=00000803270f73b0
		    Extra: Last beacon: 2930ms ago
		    IE: Unknown: 0003434D55
		    IE: Unknown: 010882848B0C12961824
		    IE: Unknown: 030101
		    IE: Unknown: 2A0102
		    IE: Unknown: 32043048606C
		    IE: Unknown: DD180050F2020101020003A5000027A5000042545E0062432F00
		    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: 3D1601080800000000000000000000000000000000000000
		    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: DD1A00904C3401080800000000000000000000000000000000000000
	  Cell 21 - Address: 00:0F:7D:0A:DD:11
		    Channel:6
		    Frequency:2.437 GHz (Channel 6)
		    Quality=32/70  Signal level=-78 dBm
		    Encryption key:off
		    ESSID:"CMU"
		    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
			      11 Mb/s; 12 Mb/s; 18 Mb/s
		    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
		    Mode:Master
		    Extra:tsf=00000802fcef01b0
		    Extra: Last beacon: 2750ms ago
		    IE: Unknown: 0003434D55
		    IE: Unknown: 010882848B0C12961824
		    IE: Unknown: 030106
		    IE: Unknown: 2A0102
		    IE: Unknown: 32043048606C
		    IE: Unknown: DD180050F2020101020003A5000027A5000042545E0062432F00
		    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: 3D1606080800000000000000000000000000000000000000
		    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: DD1A00904C3406080800000000000000000000000000000000000000
	  Cell 22 - Address: 00:0F:7D:05:E2:D1
		    Channel:6
		    Frequency:2.437 GHz (Channel 6)
		    Quality=24/70  Signal level=-86 dBm
		    Encryption key:off
		    ESSID:"CMU"
		    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
			      11 Mb/s; 12 Mb/s; 18 Mb/s
		    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
		    Mode:Master
		    Extra:tsf=00000391bc727532
		    Extra: Last beacon: 2870ms ago
		    IE: Unknown: 0003434D55
		    IE: Unknown: 010882848B0C12961824
		    IE: Unknown: 030106
		    IE: Unknown: 050B0001520000000000000000
		    IE: Unknown: 2A0102
		    IE: Unknown: 32043048606C
		    IE: Unknown: DD180050F2020101020003A5000027A5000042545E0062432F00
		    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: 3D1606080800000000000000000000000000000000000000
		    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: DD1A00904C3406080800000000000000000000000000000000000000
	  Cell 23 - Address: 00:0F:7D:09:75:71
		    Channel:6
		    Frequency:2.437 GHz (Channel 6)
		    Quality=35/70  Signal level=-75 dBm
		    Encryption key:off
		    ESSID:"CMU"
		    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
			      11 Mb/s; 12 Mb/s; 18 Mb/s
		    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
		    Mode:Master
		    Extra:tsf=000008032712949c
		    Extra: Last beacon: 2800ms ago
		    IE: Unknown: 0003434D55
		    IE: Unknown: 010882848B0C12961824
		    IE: Unknown: 030106
		    IE: Unknown: 2A0102
		    IE: Unknown: 32043048606C
		    IE: Unknown: DD180050F2020101020003A5000027A5000042545E0062432F00
		    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: 3D1606001900000000000000000000000000000000000000
		    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: DD1A00904C3406001900000000000000000000000000000000000000
	  Cell 24 - Address: 00:0F:7D:05:E2:91
		    Channel:11
		    Frequency:2.462 GHz (Channel 11)
		    Quality=27/70  Signal level=-83 dBm
		    Encryption key:off
		    ESSID:"CMU"
		    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
			      11 Mb/s; 12 Mb/s; 18 Mb/s
		    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
		    Mode:Master
		    Extra:tsf=00000391bc784812
		    Extra: Last beacon: 2440ms ago
		    IE: Unknown: 0003434D55
		    IE: Unknown: 010882848B0C12961824
		    IE: Unknown: 03010B
		    IE: Unknown: 2A0102
		    IE: Unknown: 32043048606C
		    IE: Unknown: DD180050F2020101020003A5000027A5000042545E0062432F00
		    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: 3D160B080800000000000000000000000000000000000000
		    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: DD1A00904C340B080800000000000000000000000000000000000000
	  Cell 25 - Address: 00:0F:7D:0A:DD:51
		    Channel:11
		    Frequency:2.462 GHz (Channel 11)
		    Quality=25/70  Signal level=-85 dBm
		    Encryption key:off
		    ESSID:"CMU"
		    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
			      11 Mb/s; 12 Mb/s; 18 Mb/s
		    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
		    Mode:Master
		    Extra:tsf=00000802fcf38112
		    Extra: Last beacon: 2510ms ago
		    IE: Unknown: 0003434D55
		    IE: Unknown: 010882848B0C12961824
		    IE: Unknown: 03010B
		    IE: Unknown: 050B0001520000000000000000
		    IE: Unknown: 2A0102
		    IE: Unknown: 32043048606C
		    IE: Unknown: DD180050F2020101020003A5000027A5000042545E0062432F00
		    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: 3D160B080800000000000000000000000000000000000000
		    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
		    IE: Unknown: DD1A00904C340B080800000000000000000000000000000000000000

vboxnet0  Interface doesn't support scanning.

user-laptop:/# tail -n 30 -f /var/log/kern.log
user-laptop kernel: [  715.570124] ata2: SATA link down (SStatus 0 SControl 300)
user-laptop kernel: [  715.570159] ata5: SATA link down (SStatus 0 SControl 300)
user-laptop kernel: [  715.600152] PM: restore of drv:usb dev:usb1 complete after 255.312 msecs
user-laptop kernel: [  715.750103] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
user-laptop kernel: [  715.750124] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
user-laptop kernel: [  715.750156] PM: restore of drv:usb dev:usb2 complete after 149.987 msecs
user-laptop kernel: [  715.789650] ata6.00: configured for UDMA/100
user-laptop kernel: [  715.808421] ata1.00: configured for UDMA/100
user-laptop kernel: [  715.880099] usb 1-6: reset high speed USB device using ehci_hcd and address 2
user-laptop kernel: [  716.124703] PM: restore of drv:usb dev:1-6 complete after 358.123 msecs
user-laptop kernel: [  716.124720] sd 0:0:0:0: [sda] Starting disk
user-laptop kernel: [  716.184379] Registered led device: iwl-phy0::radio
user-laptop kernel: [  716.184399] Registered led device: iwl-phy0::assoc
user-laptop kernel: [  716.184419] Registered led device: iwl-phy0::RX
user-laptop kernel: [  716.184438] Registered led device: iwl-phy0::TX
user-laptop kernel: [  716.220161] PM: restore of devices complete after 1367.562 msecs
user-laptop kernel: [  716.220439] PM: Image restored successfully.
user-laptop kernel: [  716.220441] Restarting tasks ... done.
user-laptop kernel: [  716.221391] PM: Basic memory bitmaps freed
user-laptop kernel: [ 1121.080032] CE: hpet increasing min_delta_ns to 15000 nsec
user-laptop kernel: [ 3727.261825] [fglrx] IRQ 34 Disabled
user-laptop kernel: [ 3730.116379] fglrx_pci 0000:01:00.0: irq 34 for MSI/MSI-X
user-laptop kernel: [ 3730.116860] [fglrx] Firegl kernel thread PID: 3951
user-laptop kernel: [ 3730.117055] [fglrx] IRQ 34 Enabled
user-laptop kernel: [ 3730.321807] [fglrx] Gart USWC size:1236 M.
user-laptop kernel: [ 3730.321810] [fglrx] Gart cacheable size:491 M.
user-laptop kernel: [ 3730.321814] [fglrx] Reserved FB block: Shared offset:0, size:1000000
user-laptop kernel: [ 3730.321816] [fglrx] Reserved FB block: Unshared offset:fc21000, size:3df000
user-laptop kernel: [ 3730.321818] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000
user-laptop kernel: [ 3742.169520] lo: Disabled Privacy Extensions
^C
user-laptop:/# exit

Script done on Fri 22 Oct 2010 10:07:38 AM EDT

```

Keep in mind I'm in a university, so there are many access points. The connection is open.

---

### Post by utilitytrack on 2010-10-22
Next try this:

```
# iptables -F ; iptables -X ; iptables -P OUTPUT ACCEPT ; iptables -P INPUT ACCEPT ; iptables --list -n
# iwconfig wlan0 essid CMU mode Managed rate auto key off
# iwconfig
# dhclient wlan0
# tail -n 30 -f /var/log/kern.log
```

Don't forget: all of this from root only.

---

### Post by utilitytrack on 2010-10-22
It will be even better if you will use
```
# dmesg | grep -E 'iwl|KHz|wlan0'
```

instead of
```
# tail -n 30 -f /var/log/kern.log
```

---

### Post by erjoalgo on 2010-10-22
Note that I am currently on my dorm, where I dont have wireless problems. Let me know if I should run this where I do have the problem.
```
Script started on Fri 22 Oct 2010 10:53:46 AM EDT
CEPT-;aiptablesK--liste-n-F ; iptables -X ; iptables -P OUTPUT ACCEPT ; iptables -P INPUT AC
Chain INPUT (policy ACCEPT)
target       prot opt source         destination

Chain FORWARD (policy ACCEPT)
target       prot opt source         destination

Chain OUTPUT (policy ACCEPT)
target       prot opt source         destination
user-laptop:/# iwconfig wlan0 essid CMU mode Managed rate auto key off
user-laptop:/# KtKiwconfig
lo      no wireless extensions.

eth0      no wireless extensions.

wlan0      IEEE 802.11abgn  ESSID:"CMU"
      Mode:Managed    Frequency:2.412 GHz  Access Point: 00:0F:7D:09:93:D1
      Bit Rate=1 Mb/s   Tx-Power=15 dBm
      Retry  long limit:7    RTS thr:off   Fragment thr:off
      Encryption key:off
      Power Management:off
      Link Quality=57/70  Signal level=-53 dBm
      Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
      Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

user-laptop:/# dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/00:24:d6:0c:f2:44
Sending on   LPF/wlan0/00:24:d6:0c:f2:44
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 128.237.246.39 from 128.237.224.3
DHCPREQUEST of 128.237.246.39 on wlan0 to 255.255.255.255 port 67
DHCPACK of 128.237.246.39 from 128.237.224.2
bound to 128.237.246.39 -- renewal in 359 seconds.
user-laptop:/# dmesg | grep -E 'iwl|KHz|wlan0'
[   15.511929] 01;31mKiwlmKagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   15.511931] 01;31mKiwlmKagn: Copyright(c) 2003-2009 Intel Corporation
[   15.511995] 01;31mKiwlmKagn 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.512003] 01;31mKiwlmKagn 0000:08:00.0: setting latency timer to 64
[   15.512048] 01;31mKiwlmKagn 0000:08:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   15.580551] 01;31mKiwlmKagn 0000:08:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   15.580631] 01;31mKiwlmKagn 0000:08:00.0: irq 33 for MSI/MSI-X
[   15.585026]    (2402000 01;31mKKHzmK - 2472000 01;31mKKHzmK @ 40000 01;31mKKHzmK), (300 mBi, 2000 mBm)
[   15.585028]    (2457000 01;31mKKHzmK - 2482000 01;31mKKHzmK @ 20000 01;31mKKHzmK), (300 mBi, 2000 mBm)
[   15.585030]    (2474000 01;31mKKHzmK - 2494000 01;31mKKHzmK @ 20000 01;31mKKHzmK), (300 mBi, 2000 mBm)
[   15.585032]    (5170000 01;31mKKHzmK - 5250000 01;31mKKHzmK @ 40000 01;31mKKHzmK), (300 mBi, 2000 mBm)
[   15.585034]    (5735000 01;31mKKHzmK - 5835000 01;31mKKHzmK @ 40000 01;31mKKHzmK), (300 mBi, 2000 mBm)
[   15.586195] phy0: Selected rate control algorithm '01;31mKiwlmK-agn-rs'
[  155.885456] 01;31mKiwlmKagn 0000:08:00.0: firmware: requesting 01;31mKiwlmKwifi-5000-2.ucode
[  155.982493] 01;31mKiwlmKagn 0000:08:00.0: loaded firmware version 8.24.2.12
[  156.149684] Registered led device: 01;31mKiwlmK-phy0::radio
[  156.149722] Registered led device: 01;31mKiwlmK-phy0::assoc
[  156.149751] Registered led device: 01;31mKiwlmK-phy0::RX
[  156.149776] Registered led device: 01;31mKiwlmK-phy0::TX
[  156.183851] ADDRCONF(NETDEV_UP): 01;31mKwlan0mK: link is not ready
[  715.285849] 01;31mKiwlmKagn 0000:08:00.0: RF_KILL bit toggled to enable radio.
[  716.184379] Registered led device: 01;31mKiwlmK-phy0::radio
[  716.184399] Registered led device: 01;31mKiwlmK-phy0::assoc
[  716.184419] Registered led device: 01;31mKiwlmK-phy0::RX
[  716.184438] Registered led device: 01;31mKiwlmK-phy0::TX
[ 6723.731255] 01;31mKwlan0mK: direct probe to AP 00:0f:7d:09:93:d1 (try 1)
[ 6723.757469] 01;31mKwlan0mK: direct probe responded
[ 6723.757479] 01;31mKwlan0mK: authenticate with AP 00:0f:7d:09:93:d1 (try 1)
[ 6723.762224] 01;31mKwlan0mK: authenticated
[ 6723.762264] 01;31mKwlan0mK: associate with AP 00:0f:7d:09:93:d1 (try 1)
[ 6723.767383] 01;31mKwlan0mK: RX AssocResp from 00:0f:7d:09:93:d1 (capab=0x1 status=0 aid=656)
[ 6723.767389] 01;31mKwlan0mK: associated
[ 6723.779243] ADDRCONF(NETDEV_CHANGE): 01;31mKwlan0mK: link becomes ready
[ 6734.580119] 01;31mKwlan0mK: no IPv6 routers present
user-laptop:/# exit

Script done on Fri 22 Oct 2010 10:55:28 AM EDT

```

---

### Post by utilitytrack on 2010-10-22
Now let's continue:

```
$ ifconfig -a
$ ping -c 10 173.194.36.104
```

---

### Post by erjoalgo on 2010-10-22
Thank so much for bearing with my random delays, I've had to move to/from class etc. I will now be responding very quickly.

I am now in campus, where the wireless problem occurs. I repeated the 2nd to last steps you gave me, namely 
```

# iptables -F ; iptables -X ; iptables -P OUTPUT ACCEPT ; iptables -P INPUT ACCEPT ; iptables --list -n 
# iwconfig wlan0 essid CMU mode Managed rate auto key off 
# iwconfig 
# dhclient wlan0 
# tail -n 30 -f /var/log/kern.log 

```And the problem is showing. I will shortly post the output, but I noticed that:

iwconfig says "Access Point: Not-Associated"
dhclient says "No DHCPOFFERS received"

Clearly there's a problem here!

Here's the output:
```

Script started on Fri 22 Oct 2010 03:05:22 PM EDT
user-laptop:/# iptables -F ; iptables -X ;iptables -P OUTPUT ACCEPT ; iptables -P INPUT ACCEPT ; iptables --list -n
Chain INPUT (policy ACCEPT)
target       prot opt source         destination

Chain FORWARD (policy ACCEPT)
target       prot opt source         destination

Chain OUTPUT (policy ACCEPT)
target       prot opt source         destination
user-laptop:/# iwconfig wlan0 essid CMU mode Managed rate auto key off
user-laptop:/# iwconfig
lo      no wireless extensions.

eth0      no wireless extensions.

wlan0      IEEE 802.11abgn  ESSID:"CMU"
      Mode:Managed    Access Point: Not-Associated   Tx-Power=15 dBm
      Retry  long limit:7    RTS thr:off   Fragment thr:off
      Encryption key:off
      Power Management:off

vboxnet0  no wireless extensions.

user-laptop:/# dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/00:24:d6:0c:f2:44
Sending on   LPF/wlan0/00:24:d6:0c:f2:44
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 128.237.224.21 from 128.237.224.3
DHCPREQUEST of 128.237.224.21 on wlan0 to 255.255.255.255 port 67
DHCPREQUEST of 128.237.224.21 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
user-laptop:/# dmesg | grep -E 'iwl|KHz|wlan0'
[   15.592316]    (2402000 01;31mKKHzmK - 2472000 01;31mKKHzmK @ 40000 01;31mKKHzmK), (300 mBi, 2000 mBm)
[   15.592318]    (2457000 01;31mKKHzmK - 2482000 01;31mKKHzmK @ 20000 01;31mKKHzmK), (300 mBi, 2000 mBm)
[   15.592320]    (2474000 01;31mKKHzmK - 2494000 01;31mKKHzmK @ 20000 01;31mKKHzmK), (300 mBi, 2000 mBm)
[   15.592322]    (5170000 01;31mKKHzmK - 5250000 01;31mKKHzmK @ 40000 01;31mKKHzmK), (300 mBi, 2000 mBm)
[   15.592324]    (5735000 01;31mKKHzmK - 5835000 01;31mKKHzmK @ 40000 01;31mKKHzmK), (300 mBi, 2000 mBm)
[   15.730923] 01;31mKiwlmKagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   15.730925] 01;31mKiwlmKagn: Copyright(c) 2003-2009 Intel Corporation
[   15.730990] 01;31mKiwlmKagn 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.730998] 01;31mKiwlmKagn 0000:08:00.0: setting latency timer to 64
[   15.731072] 01;31mKiwlmKagn 0000:08:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   15.775460] 01;31mKiwlmKagn 0000:08:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   15.775544] 01;31mKiwlmKagn 0000:08:00.0: irq 33 for MSI/MSI-X
[   15.779469] phy0: Selected rate control algorithm '01;31mKiwlmK-agn-rs'
[  501.993394] 01;31mKiwlmKagn 0000:08:00.0: firmware: requesting 01;31mKiwlmKwifi-5000-2.ucode
[  502.053398] 01;31mKiwlmKagn 0000:08:00.0: loaded firmware version 8.24.2.12
[  502.207845] Registered led device: 01;31mKiwlmK-phy0::radio
[  502.207892] Registered led device: 01;31mKiwlmK-phy0::assoc
[  502.207931] Registered led device: 01;31mKiwlmK-phy0::RX
[  502.207969] Registered led device: 01;31mKiwlmK-phy0::TX
[  502.241854] ADDRCONF(NETDEV_UP): 01;31mKwlan0mK: link is not ready
[  505.097018] 01;31mKwlan0mK: direct probe to AP 00:1a:1e:90:ea:20 (try 1)
[  505.290279] 01;31mKwlan0mK: direct probe to AP 00:1a:1e:90:ea:20 (try 2)
[  505.490168] 01;31mKwlan0mK: direct probe to AP 00:1a:1e:90:ea:20 (try 3)
[  505.493763] 01;31mKwlan0mK: direct probe responded
[  505.493775] 01;31mKwlan0mK: authenticate with AP 00:1a:1e:90:ea:20 (try 1)
[  505.497826] 01;31mKwlan0mK: authenticated
[  505.497881] 01;31mKwlan0mK: associate with AP 00:1a:1e:90:ea:20 (try 1)
[  505.502128] 01;31mKwlan0mK: RX AssocResp from 00:1a:1e:90:ea:20 (capab=0x421 status=0 aid=3)
[  505.502138] 01;31mKwlan0mK: associated
[  505.504308] ADDRCONF(NETDEV_CHANGE): 01;31mKwlan0mK: link becomes ready
[  515.770048] 01;31mKwlan0mK: no IPv6 routers present
user-laptop:/# exit

Script done on Fri 22 Oct 2010 03:12:16 PM EDT


```

---

### Post by utilitytrack on 2010-10-22
> **erjoalgo said:**
> Thank so much for bearing with my random delays

It's not a problem.

> **erjoalgo said:**
> 
dhclient says "No DHCPOFFERS received"
Clearly there's a problem here!

Yes, I'm trying to understand this. But you rush. What with pings, that I asked before? It's need to know for me. If you can, please go to dorm and try to connect. Don't forget before:
```
# killall -v dhclient
# ifconfig wlan0 down
# ifconfig wlan0 up
```

And post here the results. After that (if I will not be banned on this forum for some reason) we will to continue.

PS
Please again give here
```
$ ps waux
```

and
```
$ modinfo iwlagn | grep -E 'version\:|srcversion'
```

---

### Post by erjoalgo on 2010-10-22
Why would you be banned?
I am now in my dorm, everything is working:
```

      [LEFT]Script started on Fri 22 Oct 2010 04:32:33 PM EDT[/LEFT]
    [LEFT]user-laptop:~/wifiProblem# ^C[/LEFT]
    [LEFT]user-laptop:~/wifiProblem# iptables -F ; iptables -X ; iptables -P OUTPUT ACCEPT ; iptables -P INPUT ACCEPT ; iptables --list -n[/LEFT]
    [LEFT]Chain INPUT (policy ACCEPT)[/LEFT]
    [LEFT]target       prot opt source      destination[/LEFT]
    
    [LEFT]Chain FORWARD (policy ACCEPT)[/LEFT]
    [LEFT]target       prot opt source      destination[/LEFT]
    
    [LEFT]Chain OUTPUT (policy ACCEPT)[/LEFT]
    [LEFT]target       prot opt source      destination[/LEFT]
    [LEFT]user-laptop:~/wifiProblem# iwconfig wlan0 essid CMU mode Managed rate auto key off[/LEFT]
    [LEFT]user-laptop:~/wifiProblem# iwconfig[/LEFT]
    [LEFT]lo      no wireless extensions.[/LEFT]
    
    [LEFT]eth0      no wireless extensions.[/LEFT]
    
    [LEFT]wlan0      IEEE 802.11abgn  ESSID:"CMU"[/LEFT]
    [LEFT]      Mode:Managed    Access Point: Not-Associated   Tx-Power=15 dBm[/LEFT]
    [LEFT]      Retry  long limit:7    RTS thr:off   Fragment thr:off[/LEFT]
    [LEFT]      Encryption key:off[/LEFT]
    [LEFT]      Power Management:off[/LEFT]
    
    [LEFT]vboxnet0  no wireless extensions.[/LEFT]
    
    [LEFT]user-laptop:~/wifiProblem# dhclient wlan0[/LEFT]
    [LEFT]Internet Systems Consortium DHCP Client V3.1.3[/LEFT]
    [LEFT]Copyright 2004-2009 Internet Systems Consortium.[/LEFT]
    [LEFT]All rights reserved.[/LEFT]
    [LEFT]For info, please visit https://www.isc.org/software/dhcp/[/LEFT]
    
    [LEFT]Listening on LPF/wlan0/00:24:d6:0c:f2:44[/LEFT]
    [LEFT]Sending on   LPF/wlan0/00:24:d6:0c:f2:44[/LEFT]
    [LEFT]Sending on   Socket/fallback[/LEFT]
    [LEFT]DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7[/LEFT]
    [LEFT]DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10[/LEFT]
    [LEFT]DHCPOFFER of 128.237.252.51 from 128.237.224.2[/LEFT]
    [LEFT]DHCPREQUEST of 128.237.252.51 on wlan0 to 255.255.255.255 port 67[/LEFT]
    [LEFT]DHCPREQUEST of 128.237.252.51 on wlan0 to 255.255.255.255 port 67[/LEFT]
    [LEFT]DHCPACK of 128.237.252.51 from 128.237.224.3[/LEFT]
    [LEFT]bound to 128.237.252.51 -- renewal in 447 seconds.[/LEFT]
    [LEFT]user-laptop:~/wifiProblem# tail -n 30 -f /var/log/kern.log[/LEFT]
    [LEFT]user-laptop kernel: [  570.838713] sd 7:0:0:0: [sdb] Assuming drive cache: write through[/LEFT]
    [LEFT]user-laptop kernel: [  570.838722]  sdb: sdb1[/LEFT]
    [LEFT]user-laptop kernel: [  570.869223] sd 7:0:0:0: [sdb] 19488471 4096-byte logical blocks: (79.8 GB/74.3 GiB)[/LEFT]
    [LEFT]user-laptop kernel: [  570.869732] sd 7:0:0:0: [sdb] Assuming drive cache: write through[/LEFT]
    [LEFT]user-laptop kernel: [  570.869741] sd 7:0:0:0: [sdb] Attached SCSI removable disk[/LEFT]
    [LEFT]user-laptop kernel: [ 1860.209912] ip_tables: (C) 2000-2006 Netfilter Core Team[/LEFT]
    [LEFT]user-laptop kernel: [ 1955.799509] iwlagn 0000:08:00.0: firmware: requesting iwlwifi-5000-2.ucode[/LEFT]
    [LEFT]user-laptop kernel: [ 1955.848123] iwlagn 0000:08:00.0: loaded firmware version 8.24.2.12[/LEFT]
    [LEFT]user-laptop kernel: [ 1956.020788] Registered led device: iwl-phy0::radio[/LEFT]
    [LEFT]user-laptop kernel: [ 1956.020834] Registered led device: iwl-phy0::assoc[/LEFT]
    [LEFT]user-laptop kernel: [ 1956.020884] Registered led device: iwl-phy0::RX[/LEFT]
    [LEFT]user-laptop kernel: [ 1956.020929] Registered led device: iwl-phy0::TX[/LEFT]
    [LEFT]user-laptop kernel: [ 1956.053338] ADDRCONF(NETDEV_UP): wlan0: link is not ready[/LEFT]
    [LEFT]user-laptop kernel: [ 1956.724774] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0[/LEFT]
    [LEFT]user-laptop kernel: [ 1956.907527] cfg80211: Found new beacon on frequency: 5220 MHz (Ch 44) on phy0[/LEFT]
    [LEFT]user-laptop kernel: [ 1956.990046] cfg80211: Found new beacon on frequency: 5240 MHz (Ch 48) on phy0[/LEFT]
    [LEFT]user-laptop kernel: [ 1958.610192] cfg80211: Found new beacon on frequency: 5745 MHz (Ch 149) on phy0[/LEFT]
    [LEFT]user-laptop kernel: [ 1958.732294] cfg80211: Found new beacon on frequency: 5765 MHz (Ch 153) on phy0[/LEFT]
    [LEFT]user-laptop kernel: [ 1958.778795] cfg80211: Found new beacon on frequency: 5785 MHz (Ch 157) on phy0[/LEFT]
    [LEFT]user-laptop kernel: [ 1958.895511] cfg80211: Found new beacon on frequency: 5805 MHz (Ch 161) on phy0[/LEFT]
    [LEFT]user-laptop kernel: [ 1959.035456] wlan0: direct probe to AP 00:0f:7d:05:c5:51 (try 1)[/LEFT]
    [LEFT]user-laptop kernel: [ 1959.230305] wlan0: direct probe to AP 00:0f:7d:05:c5:51 (try 2)[/LEFT]
    [LEFT]user-laptop kernel: [ 1959.235258] wlan0: direct probe responded[/LEFT]
    [LEFT]user-laptop kernel: [ 1959.235270] wlan0: authenticate with AP 00:0f:7d:05:c5:51 (try 1)[/LEFT]
    [LEFT]user-laptop kernel: [ 1959.254419] wlan0: authenticated[/LEFT]
    [LEFT]user-laptop kernel: [ 1959.254470] wlan0: associate with AP 00:0f:7d:05:c5:51 (try 1)[/LEFT]
    [LEFT]user-laptop kernel: [ 1959.260398] wlan0: RX AssocResp from 00:0f:7d:05:c5:51 (capab=0x1 status=0 aid=656)[/LEFT]
    [LEFT]user-laptop kernel: [ 1959.260406] wlan0: associated[/LEFT]
    [LEFT]user-laptop kernel: [ 1959.262894] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready[/LEFT]
    [LEFT]user-laptop kernel: [ 1969.950247] wlan0: no IPv6 routers present[/LEFT]
    [LEFT]^C[/LEFT]
    [LEFT]user-laptop:~/wifiProblem# ifconfig -a[/LEFT]
    [LEFT]eth0      Link encap:Ethernet  HWaddr 00:24:e8:d0:6f:8b[/LEFT]
    [LEFT]      UP BROADCAST MULTICAST  MTU:1500  Metric:1[/LEFT]
    [LEFT]      RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/LEFT]
    [LEFT]      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/LEFT]
    [LEFT]      collisions:0 txqueuelen:1000[/LEFT]
    [LEFT]      RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/LEFT]
    [LEFT]      Interrupt:32 Base address:0xc000[/LEFT]
    
    [LEFT]eth0:avahi Link encap:Ethernet    HWaddr 00:24:e8:d0:6f:8b[/LEFT]
    [LEFT]      inet addr:169.254.9.216  Bcast:169.254.255.255  Mask:255.255.0.0[/LEFT]
    [LEFT]      UP BROADCAST MULTICAST  MTU:1500  Metric:1[/LEFT]
    [LEFT]      Interrupt:32 Base address:0xc000[/LEFT]
    
    [LEFT]lo      Link encap:Local Loopback[/LEFT]
    [LEFT]      inet addr:127.0.0.1  Mask:255.0.0.0[/LEFT]
    [LEFT]      inet6 addr: ::1/128 Scope:Host[/LEFT]
    [LEFT]      UP LOOPBACK RUNNING  MTU:16436  Metric:1[/LEFT]
    [LEFT]      RX packets:41 errors:0 dropped:0 overruns:0 frame:0[/LEFT]
    [LEFT]      TX packets:41 errors:0 dropped:0 overruns:0 carrier:0[/LEFT]
    [LEFT]      collisions:0 txqueuelen:0[/LEFT]
    [LEFT]      RX bytes:4224 (4.2 KB)  TX bytes:4224 (4.2 KB)[/LEFT]
    
    [LEFT]vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00[/LEFT]
    [LEFT]      BROADCAST MULTICAST  MTU:1500  Metric:1[/LEFT]
    [LEFT]      RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/LEFT]
    [LEFT]      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/LEFT]
    [LEFT]      collisions:0 txqueuelen:1000[/LEFT]
    [LEFT]      RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/LEFT]
    
    [LEFT]wlan0      Link encap:Ethernet  HWaddr 00:24:d6:0c:f2:44[/LEFT]
    [LEFT]      inet addr:128.237.252.51  Bcast:128.237.255.255  Mask:255.255.224.0[/LEFT]
    [LEFT]      inet6 addr: fe80::224:d6ff:fe0c:f244/64 Scope:Link[/LEFT]
    [LEFT]      UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/LEFT]
    [LEFT]      RX packets:442 errors:0 dropped:0 overruns:0 frame:0[/LEFT]
    [LEFT]      TX packets:32 errors:0 dropped:0 overruns:0 carrier:0[/LEFT]
    [LEFT]      collisions:0 txqueuelen:1000[/LEFT]
    [LEFT]      RX bytes:30583 (30.5 KB)  TX bytes:6732 (6.7 KB)[/LEFT]
    
    [LEFT]user-laptop:~/wifiProblem# pinKg -c 4K42 173.194.K36.104[/LEFT]
    [LEFT]PING 173.194.36.104 (173.194.36.104) 56(84) bytes of data.[/LEFT]
    [LEFT]64 bytes from 173.194.36.104: icmp_seq=1 ttl=51 time=84.1 ms[/LEFT]
    [LEFT]64 bytes from 173.194.36.104: icmp_seq=2 ttl=51 time=83.6 ms[/LEFT]
    [LEFT]64 bytes from 173.194.36.104: icmp_seq=3 ttl=51 time=83.5 ms[/LEFT]
    [LEFT]64 bytes from 173.194.36.104: icmp_seq=4 ttl=51 time=84.4 ms[/LEFT]
    [LEFT]64 bytes from 173.194.36.104: icmp_seq=5 ttl=51 time=84.4 ms[/LEFT]
    [LEFT]64 bytes from 173.194.36.104: icmp_seq=6 ttl=51 time=84.3 ms[/LEFT]
    [LEFT]64 bytes from 173.194.36.104: icmp_seq=7 ttl=51 time=86.7 ms[/LEFT]
    [LEFT]64 bytes from 173.194.36.104: icmp_seq=8 ttl=51 time=89.9 ms[/LEFT]
    [LEFT]64 bytes from 173.194.36.104: icmp_seq=9 ttl=51 time=84.8 ms[/LEFT]
    [LEFT]64 bytes from 173.194.36.104: icmp_seq=10 ttl=51 time=88.2 ms[/LEFT]
    [LEFT]64 bytes from 173.194.36.104: icmp_seq=11 ttl=51 time=83.7 ms[/LEFT]
    [LEFT]64 bytes from 173.194.36.104: icmp_seq=12 ttl=51 time=85.8 ms[/LEFT]
    [LEFT]64 bytes from 173.194.36.104: icmp_seq=13 ttl=51 time=83.8 ms[/LEFT]
    [LEFT]64 bytes from 173.194.36.104: icmp_seq=14 ttl=51 time=86.2 ms[/LEFT]
    [LEFT]64 bytes from 173.194.36.104: icmp_seq=15 ttl=51 time=85.8 ms[/LEFT]
    [LEFT]64 bytes from 173.194.36.104: icmp_seq=16 ttl=51 time=83.9 ms[/LEFT]
    [LEFT]64 bytes from 173.194.36.104: icmp_seq=17 ttl=51 time=84.1 ms[/LEFT]
    [LEFT]64 bytes from 173.194.36.104: icmp_seq=18 ttl=51 time=84.0 ms[/LEFT]
    [LEFT]64 bytes from 173.194.36.104: icmp_seq=19 ttl=51 time=84.4 ms[/LEFT]
    [LEFT]64 bytes from 173.194.36.104: icmp_seq=20 ttl=51 time=84.8 ms[/LEFT]
    [LEFT]64 bytes from 173.194.36.104: icmp_seq=21 ttl=51 time=85.8 ms[/LEFT]
    [LEFT]64 bytes from 173.194.36.104: icmp_seq=22 ttl=51 time=84.3 ms[/LEFT]
    [LEFT]64 bytes from 173.194.36.104: icmp_seq=23 ttl=51 time=84.2 ms[/LEFT]
    [LEFT]64 bytes from 173.194.36.104: icmp_seq=24 ttl=51 time=85.7 ms[/LEFT]
    [LEFT]64 bytes from 173.194.36.104: icmp_seq=25 ttl=51 time=84.6 ms[/LEFT]
    [LEFT]64 bytes from 173.194.36.104: icmp_seq=26 ttl=51 time=84.1 ms[/LEFT]
    [LEFT]64 bytes from 173.194.36.104: icmp_seq=27 ttl=51 time=85.6 ms[/LEFT]
    [LEFT]64 bytes from 173.194.36.104: icmp_seq=28 ttl=51 time=83.9 ms[/LEFT]
    [LEFT]^C[/LEFT]
    [LEFT]--- 173.194.36.104 ping statistics ---[/LEFT]
    [LEFT]28 packets transmitted, 28 received, 0% packet loss, time 27025ms[/LEFT]
    [LEFT]rtt min/avg/max/mdev = 83.526/84.996/89.988/1.453 ms[/LEFT]
    [LEFT]user-laptop:~/wifiProblem# exit[/LEFT]
    
    [LEFT]Script done on Fri 22 Oct 2010 04:35:58 PM EDT[/LEFT]
    
   
  
```

---

### Post by utilitytrack on 2010-10-22
> I am now in my dorm, everything is working
> 0% packet loss

It's good news **for you and I**. 

Now I ask you to go in campus or any other place where you experience problems with wireless. As you ready, we will accurately continue. Bear in mind that you will should to completely turn off wired network during the experiments.  I will tell how to do that. Also if you **can please tell me how** to work wireless on campus when you use Default OS.

PS 
Please provide what I asked
```
$ ps waux
$ modinfo iwlagn | grep -E 'version\:|srcversion'
```

---

### Post by erjoalgo on 2010-10-22
Sorry again, I wrote a script to do this more quickly. I am now on campus, where the problem is.
> Bear in mind that you will should to completely turn off wired network during the experiments.  I will tell how to do that.
There is no ethernet cable attached to the machine.
> 
Also if you can please say me how to work wireless on campus when you use Default OS.

Hmm what do you want to know about it?
It works with no problem using the default GUI to connect to an open network.
I can give more details if need.
Since you are helping me with this I should help you with your english. It should be "can please 'tell' me how...".
Also, 
> It's good news for my and you. 
Should be, "it's good news for you and I" or "its good news for both of us".
Ha. Here is the output.
                       ```


user-laptop:/$ killall -v dhclient
dhclient: no process found
user-laptop:/$ ifconfig wlan0 down
user-laptop:/$ ifconfig wlan0 up
user-laptop:/$ ps waux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0  23684  1952 ?        Ss   17:33   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    17:33   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    17:33   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S    17:33   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S    17:33   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S    17:33   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S    17:33   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S    17:33   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S    17:33   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S    17:33   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S    17:33   0:00 [cpuset]
root        12  0.0  0.0      0     0 ?        S    17:33   0:00 [khelper]
root        13  0.0  0.0      0     0 ?        S    17:33   0:00 [netns]
root        14  0.0  0.0      0     0 ?        S    17:33   0:00 [async/mgr]
root        15  0.0  0.0      0     0 ?        S    17:33   0:00 [pm]
root        17  0.0  0.0      0     0 ?        S    17:33   0:00 [sync_supers]
root        18  0.0  0.0      0     0 ?        S    17:33   0:00 [bdi-default]
root        19  0.0  0.0      0     0 ?        S    17:33   0:00 [kintegrityd/0]
root        20  0.0  0.0      0     0 ?        S    17:33   0:00 [kintegrityd/1]
root        21  0.0  0.0      0     0 ?        S    17:33   0:00 [kblockd/0]
root        22  0.0  0.0      0     0 ?        S    17:33   0:00 [kblockd/1]
root        23  0.0  0.0      0     0 ?        S    17:33   0:00 [kacpid]
root        24  0.0  0.0      0     0 ?        S    17:33   0:00 [kacpi_notify]
root        25  0.0  0.0      0     0 ?        S    17:33   0:00 [kacpi_hotplug]
root        26  0.0  0.0      0     0 ?        S    17:33   0:00 [ata/0]
root        27  0.0  0.0      0     0 ?        S    17:33   0:00 [ata/1]
root        28  0.0  0.0      0     0 ?        S    17:33   0:00 [ata_aux]
root        29  0.0  0.0      0     0 ?        S    17:33   0:00 [ksuspend_usbd]
root        30  0.0  0.0      0     0 ?        S    17:33   0:00 [khubd]
root        31  0.0  0.0      0     0 ?        S    17:33   0:00 [kseriod]
root        32  0.0  0.0      0     0 ?        S    17:33   0:00 [kmmcd]
root        35  0.0  0.0      0     0 ?        S    17:33   0:00 [khungtaskd]
root        36  0.0  0.0      0     0 ?        S    17:33   0:00 [kswapd0]
root        37  0.0  0.0      0     0 ?        SN   17:33   0:00 [ksmd]
root        38  0.0  0.0      0     0 ?        S    17:33   0:00 [aio/0]
root        39  0.0  0.0      0     0 ?        S    17:33   0:00 [aio/1]
root        40  0.0  0.0      0     0 ?        S    17:33   0:00 [ecryptfs-kthrea]
root        41  0.0  0.0      0     0 ?        S    17:33   0:00 [crypto/0]
root        42  0.0  0.0      0     0 ?        S    17:33   0:00 [crypto/1]
root        54  0.0  0.0      0     0 ?        S    17:33   0:00 [kstriped]
root        55  0.0  0.0      0     0 ?        S    17:33   0:00 [kmpathd/0]
root        56  0.0  0.0      0     0 ?        S    17:33   0:00 [kmpathd/1]
root        57  0.0  0.0      0     0 ?        S    17:33   0:00 [kmpath_handlerd]
root        58  0.0  0.0      0     0 ?        S    17:33   0:00 [ksnapd]
root        59  0.0  0.0      0     0 ?        S    17:33   0:00 [kondemand/0]
root        60  0.0  0.0      0     0 ?        S    17:33   0:00 [kondemand/1]
root        61  0.0  0.0      0     0 ?        S    17:33   0:00 [kconservative/0]
root        62  0.0  0.0      0     0 ?        S    17:33   0:00 [kconservative/1]
root       222  0.0  0.0      0     0 ?        S    17:33   0:00 [scsi_eh_0]
root       254  0.0  0.0      0     0 ?        S    17:33   0:00 [scsi_eh_1]
root       276  0.0  0.0      0     0 ?        S    17:33   0:00 [scsi_eh_2]
root       283  0.0  0.0      0     0 ?        S    17:33   0:00 [scsi_eh_3]
root       284  0.0  0.0      0     0 ?        S    17:33   0:00 [scsi_eh_4]
root       285  0.0  0.0      0     0 ?        S    17:33   0:00 [khpsbpkt]
root       286  0.0  0.0      0     0 ?        S    17:33   0:00 [scsi_eh_5]
root       302  0.0  0.0      0     0 ?        S    17:33   0:00 [knodemgrd_0]
root       321  0.0  0.0      0     0 ?        S    17:33   0:00 [jbd2/sda6-8]
root       322  0.0  0.0      0     0 ?        S    17:33   0:00 [ext4-dio-unwrit]
root       323  0.0  0.0      0     0 ?        S    17:33   0:00 [ext4-dio-unwrit]
root       356  0.0  0.0      0     0 ?        S    17:33   0:00 [flush-8:0]
root       382  0.0  0.0  17036   976 ?        S    17:34   0:00 upstart-udev-bridge --daemon
root       384  0.0  0.0  17096   968 ?        S<s  17:34   0:00 udevd --daemon
root       700  0.0  0.0      0     0 ?        S    17:34   0:00 [kpsmoused]
root       755  0.0  0.0      0     0 ?        S    17:34   0:00 [hd-audio0]
root       757  0.0  0.0      0     0 ?        S    17:34   0:01 [iwlagn]
root       758  0.0  0.0      0     0 ?        S    17:34   0:03 [phy0]
root       781  0.0  0.0      0     0 ?        S    17:34   0:00 [hd-audio1]
root       827  0.0  0.1  94296  4540 ?        Ss   17:34   0:00 smbd -F
syslog     838  0.0  0.0 126616  2256 ?        Sl   17:34   0:00 rsyslogd -c4
102        839  0.0  0.0  24292  1724 ?        Ss   17:34   0:00 dbus-daemon --system --fork
user-laptop.local]
avahi      861  0.0  0.0  33928   580 ?        Ss   17:34   0:00 avahi-daemon: chroot helper
root       889  0.0  0.0  94296  1360 ?        S    17:34   0:00 smbd -F
root       933  0.0  0.0   6080   648 tty4     Ss+  17:34   0:00 /sbin/getty -8 38400 tty4
root       938  0.0  0.0   6080   644 tty5     Ss+  17:34   0:00 /sbin/getty -8 38400 tty5
root       945  0.0  0.0   6080   644 tty2     Ss+  17:34   0:00 /sbin/getty -8 38400 tty2
root       947  0.0  0.0   6080   648 tty3     Ss+  17:34   0:00 /sbin/getty -8 38400 tty3
root       950  0.0  0.0   6080   648 tty6     Ss+  17:34   0:00 /sbin/getty -8 38400 tty6
root       954  0.0  0.0   4428  1140 ?        Ss   17:34   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root       991  0.0  0.0  21076  1020 ?        Ss   17:34   0:00 cron
daemon     992  0.0  0.0  18884   464 ?        Ss   17:34   0:00 atd
root      1029  0.0  0.0  76592  3480 ?        Ssl  17:34   0:00 gdm-binary
root      1038  0.0  0.0 120464  3644 ?        Sl   17:34   0:00 /usr/sbin/console-kit-daemon --no-daemon
root      1111  0.0  0.1  93496  4196 ?        Sl   17:34   0:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1
root      1155  1.4  3.3 246652 134564 tty7    Ss+  17:34   0:47 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-BTHF8I/database -nolisten tcp vt7
root      1158  0.0  0.0  37208  2244 ?        Ss   17:34   0:00 /usr/lib/postfix/master
root      1200  0.0  0.0  65724  1524 ?        Ss   17:34   0:00 /usr/sbin/winbindd
root      1224  0.0  0.0  75404  3044 ?        Ss   17:34   0:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
root      1225  0.0  0.0      0     0 ?        S    17:34   0:00 [firegl]
root      1316  0.0  0.0  65832  1680 ?        S    17:34   0:00 /usr/sbin/winbindd
root      1330  0.0  0.0   6080   644 tty1     Ss+  17:34   0:00 /sbin/getty -8 38400 tty1
gdm       1349  0.0  0.0  26260   828 ?        S    17:34   0:00 /usr/bin/dbus-launch --exit-with-session
root      1363  0.0  0.1 145972  5404 ?        Sl   17:34   0:00 /usr/lib/gdm/gdm-session-worker
root      1365  0.0  0.3  65700 13036 ?        S    17:34   0:01 /usr/lib/upower/upowerd
root      1388  0.0  0.1  54276  4316 ?        S    17:34   0:00 /usr/lib/policykit-1/polkitd
gdm       1410  0.0  0.1 159024  4960 ?        Ss   17:34   0:00 /usr/bin/gnome-screensaver
root      1416  0.0  0.0  65844  2040 ?        S    17:34   0:00 /usr/sbin/winbindd
user  1419  0.0  0.0  69764  2780 ?        Sl   17:34   0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
user  1437  0.0  0.2 169656  8168 ?        Ssl  17:34   0:00 gnome-session
user  1473  0.0  0.0  11936   412 ?        Ss   17:34   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session
user  1476  0.0  0.0  26260   820 ?        S    17:34   0:00 /usr/bin/dbus-launch --exit-with-session gnome-session
user  1477  0.0  0.0  24344  1812 ?        Ss   17:34   0:00 /bin/dbus-daemon --fork --print-pid 5 --print-address 9 --session
user  1480  0.0  0.1  46184  5760 ?        S    17:34   0:00 /usr/lib/libgconf2-4/gconfd-2
user  1487  0.0  0.4 324760 16740 ?        Ss   17:34   0:01 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
user  1489  0.0  0.0  47996  2576 ?        S    17:34   0:00 /usr/lib/gvfs/gvfsd
user/.gvfs
user  1500  0.1  0.8 246112 33200 ?        S    17:34   0:03 compiz --sm-client-id 10d27bada0d37c609112856275701095000000015200036
user  1507  0.0  0.2 182548  8716 ?        S    17:34   0:00 /usr/lib/vino/vino-server --sm-disable
user  1508  0.0  0.1 164140  7308 ?        S    17:34   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
user  1509  0.0  1.7 519532 71064 ?        Sl   17:34   0:00 /usr/bin/google-chrome
user  1510  0.0  0.3 220092 12460 ?        S    17:34   0:00 gnome-power-manager
user  1514  0.1  2.3 751340 96656 ?        SLl  17:34   0:06 rhythmbox --sm-client-id 102febfafc987e97d7128746253749691300000015240001
user/.config/session-state/nautilus-1287756274.desktop
user  1516  0.0  0.2 231012  8792 ?        S    17:34   0:00 /usr/bin/google-chrome
user/.config/session-state/evince-1287756274.desktop
user/.config/session-state/evince-1287756273.desktop
user  1520  0.0  0.3 243588 13868 ?        S    17:34   0:00 /opt/google/chrome/chrome --type=zygote
user  1522  0.0  0.4 270876 18312 ?        S    17:34   0:00 gnome-panel --sm-client-id 1061ce56e6664eb5ea128402576278095600000014910033
user  1525  0.0  0.0   4096   620 ?        S    17:34   0:00 /bin/sh /usr/bin/gnome-do
user  1532  0.0  0.9 359116 38388 ?        Sl   17:34   0:02 /usr/bin/cli /usr/lib/gnome-do/Do.exe
user  1540  0.0  0.1 212996  4964 ?        S<sl 17:34   0:00 /usr/bin/pulseaudio --start --log-target=syslog
rtkit     1545  0.0  0.0  43640  1280 ?        SNl  17:34   0:00 /usr/lib/rtkit/rtkit-daemon
user  1554  0.0  0.0 153924  3888 ?        S    17:34   0:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
root      1556  0.0  0.0  65788  3704 ?        Sl   17:34   0:00 /usr/lib/udisks/udisks-daemon
root      1557  0.0  0.0  46696  1076 ?        S    17:34   0:00 udisks-daemon: polling /dev/sr0 /dev/sdb
user  1574  0.0  0.0  52736  3436 ?        S    17:34   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.6 /org/gtk/gvfs/exec_spaw/0
user  1584  0.0  0.1 183332  8048 ?        Ss   17:34   0:00 /usr/bin/gnome-screensaver
user  1586  0.0  0.0  69216  2704 ?        Sl   17:34   0:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
user  1589  0.0  0.0  55252  2684 ?        S    17:34   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
user  1591  0.0  0.0  96652  3496 ?        S    17:34   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
user  1593  0.0  0.1 152848  4140 ?        Ssl  17:34   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=19
user  1594  0.0  0.0   4096   592 ?        Ss   17:34   0:00 /bin/sh -c /usr/bin/compiz-decorator
user  1596  0.0  0.2 179340 12148 ?        S    17:34   0:00 /usr/bin/gtk-window-decorator
user  1606  0.0  0.3 267940 15252 ?        S    17:34   0:00 /usr/lib/gnome-panel/wnck-applet --oaf-activate-iid=OAFIID:GNOME_Wncklet_Factory --oaf-ior-fd=18
user  1607  0.0  0.3 252032 13292 ?        S    17:34   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=24
user  1609  0.0  0.0  44096  2184 ?        S    17:34   0:00 /usr/lib/evince/evinced
user  1612  0.0  0.5 846280 21824 ?        Sl   17:34   0:00 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtest=ConnCountImpact/conn_count_6/ConnnectBackupJobs/ConnectBackupJobsEnabled/DnsImpact/default_enabled_prefetch/GlobalSdch/global_enable_sdch/IdleSktToImpact/idle_timeout_60/Prefetch/ContentPrefetchDisabled/ProxyConnectionImpact/proxy_connections_32/SpdyImpact/npn_with_spdy/ --channel=1509.0x5fd0000.1489684897
user  1616  0.0  0.5 848908 21664 ?        Sl   17:34   0:00 /opt/google/chrome/chrome --type=extension --lang=en-US --force-fieldtest=ConnCountImpact/conn_count_6/ConnnectBackupJobs/ConnectBackupJobsEnabled/DnsImpact/default_enabled_prefetch/GlobalSdch/global_enable_sdch/IdleSktToImpact/idle_timeout_60/Prefetch/ContentPrefetchDisabled/ProxyConnectionImpact/proxy_connections_32/SpdyImpact/npn_with_spdy/ --channel=1509.0x5ac4600.516594690
user  1633  0.0  0.0  29104  1236 ?        S    17:34   0:01 syndaemon -i 0.5 -k
user  1638  0.0  0.4 846508 20056 ?        Sl   17:34   0:00 /opt/google/chrome/chrome --type=extension --lang=en-US --force-fieldtest=ConnCountImpact/conn_count_6/ConnnectBackupJobs/ConnectBackupJobsEnabled/DnsImpact/default_enabled_prefetch/GlobalSdch/global_enable_sdch/IdleSktToImpact/idle_timeout_60/Prefetch/ContentPrefetchDisabled/ProxyConnectionImpact/proxy_connections_32/SpdyImpact/npn_with_spdy/ --channel=1509.0x5ac4000.728478569
user  1662  0.0  0.3 251308 12360 ?        S    17:34   0:00 /usr/lib/gnome-power-manager/gnome-inhibit-applet --oaf-activate-iid=OAFIID:GNOME_InhibitApplet_Factory --oaf-ior-fd=22
user  1674  0.0  0.3 345812 15576 ?        S    17:34   0:00 /usr/lib/indicator-applet/indicator-applet-session --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=25
user  1676  0.0  0.4 397112 16988 ?        S    17:34   0:00 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=OAFIID:GNOME_ClockApplet_Factory --oaf-ior-fd=31
user  1677  0.0  0.3 282364 15340 ?        S    17:34   0:00 /usr/lib/indicator-applet/indicator-applet --oaf-activate-iid=OAFIID:GNOME_IndicatorApplet_Factory --oaf-ior-fd=43
user  1678  0.0  0.2 210460 10808 ?        S    17:34   0:00 /usr/lib/gnome-panel/notification-area-applet --oaf-activate-iid=OAFIID:GNOME_NotificationAreaApplet_Factory --oaf-ior-fd=37
user  1697  0.0  0.0  42084  2680 ?        S    17:34   0:00 /usr/lib/gvfs/gvfsd-metadata
user  1699  0.0  0.1 143844  5660 ?        S    17:34   0:00 /usr/lib/indicator-me/indicator-me-service
user  1701  0.0  0.1 140908  5520 ?        S    17:34   0:00 /usr/lib/indicator-session/indicator-session-service
user  1706  0.0  0.1 138108  4964 ?        S    17:34   0:00 /usr/lib/indicator-messages/indicator-messages-service
user  1707  0.0  0.1 146900  4892 ?        S    17:34   0:00 /usr/lib/indicator-application/indicator-application-service
user  1708  0.0  0.1 219020  5344 ?        S    17:34   0:00 /usr/lib/indicator-sound/indicator-sound-service
user  1750  0.0  0.2 178784  8536 ?        S    17:34   0:00 /usr/lib/gnome-disk-utility/gdu-notification-daemon
user  1762  0.0  0.0  47864  2600 ?        S    17:34   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.6 /org/gtk/gvfs/exec_spaw/1
user  1779  0.3  0.7 208824 31296 ?        SLl  17:34   0:10 /usr/bin/python /usr/lib/ubuntuone-client/ubuntuone-syncdaemon
user  1786  0.0  0.7 287928 28588 ?        S    17:34   0:00 python /usr/share/system-config-printer/applet.py
user  1788  0.0  0.3 432272 14088 ?        Sl   17:34   0:00 /usr/lib/evolution/2.28/evolution-alarm-notify --sm-config-prefix /evolution-alarm-notify-BYeWcQ/ --sm-client-id 105e5870eadd88e473128775148374089400000014680008 --screen 0
user  1798  0.0  0.3 429344 13936 ?        Sl   17:35   0:00 /usr/lib/evolution/2.28/evolution-exchange-storage --oaf-activate-iid=OAFIID:GNOME_Evolution_Exchange_Connector_CalFactory:1.2 --oaf-ior-fd=35
user  1803  0.0  0.2 390764 10836 ?        Sl   17:35   0:00 /usr/lib/evolution/evolution-data-server-2.28 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2 --oaf-ior-fd=36
103       1813  0.0  0.0  14528   872 ?        S    17:35   0:00 avahi-autoipd: [eth0] bound 169.254.9.216
root      1814  0.0  0.0   6100   412 ?        Ss   17:35   0:00 avahi-autoipd: [eth0] callout dispatcher
root      1850  0.0  0.0   6556   568 ?        Ss   17:35   0:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
user  1887  0.0  0.3 217032 13944 ?        S    17:35   0:00 update-notifier
root      1892  0.0  0.2  78768 10708 ?        S    17:35   0:00 /usr/bin/python /usr/lib/system-service/system-service-d
root      1917  0.0  0.0  49260  1048 ?        Ss   17:35   0:00 /usr/sbin/sshd
postfix   1939  0.0  0.0  39272  2180 ?        S    17:35   0:00 pickup -l -t fifo -u -c
postfix   1940  0.0  0.0  39432  2228 ?        S    17:35   0:00 qmgr -l -t fifo -u
root      1954  0.0  0.0  60520  1756 ?        Ss   17:35   0:00 nmbd -D
user/
user  2015  0.0  0.0  14488   812 ?        S    17:40   0:00 gnome-pty-helper
user  2016  0.0  0.1  21408  4248 pts/0    Ss   17:40   0:00 bash
user  2093  0.0  0.1  21396  4248 pts/1    Ss   17:41   0:00 bash
root      2994  0.0  0.0      0     0 ?        S    18:11   0:00 [scsi_eh_7]
root      2995  0.0  0.0      0     0 ?        S    18:11   0:00 [usb-storage]
root      3015  0.0  0.0      0     0 ?        S    18:11   0:00 [flush-8:16]
user  3106  0.0  0.2  76828 12096 pts/0    T    18:18   0:00 emacs -nw -nw logBash.sh
user  3128  0.0  0.2  76880 12028 pts/1    T    18:18   0:00 emacs -nw -nw logBash.sh
root      3453  0.0  0.0  17092   928 ?        S<   18:27   0:00 udevd --daemon
root      3454  0.0  0.0  17092   928 ?        S<   18:27   0:00 udevd --daemon
user  3463  0.5  0.2  76788 11888 pts/1    S+   18:28   0:00 emacs -nw -nw ../ipod/lastOut.final
root      3466  0.5  0.0   4096   632 pts/0    S+   18:28   0:00 /bin/sh ./logBash.sh ../ipod/commands ../ipod/lastOut
root      3472  0.0  0.0  17092   928 ?        S<   18:28   0:00 udevd --daemon
root      3473  0.0  0.0  17092   928 ?        S<   18:28   0:00 udevd --daemon
root      3479  0.0  0.0  15268  1224 pts/0    R+   18:28   0:00 ps waux

```

---

### Post by utilitytrack on 2010-10-22
Ok. If you wrote some script it's very good. But now please don't do nothing except what I asked. Also: if you on campus please stay there.

Well, let's begin.

Kick off all this stuff:
```
# killall -v dhclient3 ; killall -v dhclient
# service avahi-daemon stop
# rm /etc/network/if-up.d/avahi-daemon
# rm /etc/network/if-post-down.d/avahi-daemon
# killall -v avahi-daemon && killall -v avahi-daemon ; killall -v avahi-autoipd && killall -v avahi-autoipd
```
Twice, yes. Strike Avahi with a hammer.

Clean all DHCP pid's and leases
```
# rm /var/run/dhclient*
# rm /var/lib/dhcp3/dhclient*
```

Next disconnect from wired network and unload a r8169 kernel module. If you don't have any other computer with internet, you will be in offline some time.

```
# ifconfig eth0 down
# rmmod -v r8169
```

Next turn off wlan0 interface and unload (yes, again) and load back all wireless modules:
```
# ifconfig wlan0 down
# rmmod -v iwlagn ; rmmod -v iwlcore ; rmmod -v mac80211 ; rmmod -v cfg80211 ; rmmod -v rfkill
# modprobe -v iwlagn
```

Next bring up the interface. 
```
# ip link set wlan0 up
```

Wait one minute. Make snapshot of the log and save it.
```
$ dmesg | grep -i -E 'Kill|80211|wlan|iwl|KHz|r8169'
```

Next check that device is present in list of active interfaces
```
# ifconfig
```

Next check state of wireless interface. You know how it look like.
```
# iwconfig wlan0
```

Next scan available Wifi networks for to check is the device properly turned on. You know what we should get. Provide output here.
```
# iwlist wlan0 scanning
```

Next try configure the interface (I assume that ESSID is "CMU", and network is insecure):
```
# iwconfig wlan0 essid CMU 
# iwconfig wlan0 mode Managed 
# iwconfig wlan0 rate auto 
# iwconfig wlan0 key off
# iwconfig wlan0 retry 30
```

Pay attention on the last line. If you get some error message, try [FONT="Courier New"]retry long 30[/FONT] or [FONT="Courier New"]retry lifetime 300m[/FONT] or, if no success, ignore last line at all.

Next
```
# dhclient wlan0
```

So, on this stage DHCPOFFER should be received, my congratulations.
Check the connection:
```
# ping -c 10 173.194.36.104
```


***


If not received, try again many times: first, shut down ANY instance of DHCP client
```
# killall -v dhclient3 ; killall -v dhclient
```
Look carefully that client is dead.

Clean all DHCP pid's and leases
```
# rm /var/run/dhclient*
# rm /var/lib/dhcp3/dhclient*
```

Then again try and so on to victory...
```
# ifconfig wlan0 down
# ifconfig wlan0 up
# iwconfig (as above)
# dhclient wlan0
```


Good luck you.



***



Copy on forum
```
$ dmesg | grep -i -E 'Kill|80211|wlan|iwl|KHz|r8169'
```

and please attach full output of dmesg in file:
```
$ dmesg > dmesg.log
```

***

PS
For to get wired network working again, try this:
```
# load r8169
# ifup -v eth0
```

But it will be better if you leave it unconfigured.

PPS
I hasten to bring you good news. On this stage you get first step in knowledge of Linux internals. Keep it up!

PPPS
It seems that it's my longest message on this forum. I congratulate myself.

---

### Post by utilitytrack on 2010-10-22
> **erjoalgo said:**
> Since you are helping me with this I should help you with your english. It should be "can please 'tell' me how...".

Ok, let's you open a new thread where you will teach me English :)

> **erjoalgo said:**
> Excuse the delay, I had class.

Yes, I feel it.


Now the heart of the matter: 
1) if you don't get any success in previous time, try load [FONT="Courier New"]iwlagn[/FONT] module like
```
# modprobe iwlagn 11n_disable=1
```

And test again.

2) try to choose other channel (if the AP accept this). For example
```
# iwconfig eth0 channel 6
``` 
See output of [FONT="Courier New"]iwlist[/FONT] for to find appropriate values for each AP, also see [FONT="Courier New"]$ man iwconfig[/FONT]

And test again.

I wait for your impressions.

---

### Post by erjoalgo on 2010-10-23
No luck!
No luck, no luck.
Such bad luck.
I wish ubuntu was a few years into the future, past all these nuisance so users can actually use their computers.
I love ubuntu, but it needs major improvements in terms of hardware.

You've helped me enough, if you don't have any more ideas, I understand.
I appreciate your help!
How do you know so much? Your knowledge is great.
Just for the record, I attach the log you asked, but I dont expect any more solutions, I don't wanna suck any more of your time.
But if you do, or anyone else, happens to find a solution, Im still looking for it.
Thanks so much.

```


dmesg | grep -i -E 'Kill|80211|wlan|iwl|KHz|r8169'
[    2.011408] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.011442] r8169 0000:20:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.011534] r8169 0000:20:00.0: setting latency timer to 64
[    2.011717] r8169 0000:20:00.0: irq 32 for MSI/MSI-X
[   15.288815] cfg80211: Calling CRDA to update world regulatory domain
[   15.446693] cfg80211: World regulatory domain updated:
[   15.446698]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.446700]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.446702]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.446704]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.446706]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.468431] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   15.468433] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   15.468559] iwlagn 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.468615] iwlagn 0000:08:00.0: setting latency timer to 64
[   15.468745] iwlagn 0000:08:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   15.547393] iwlagn 0000:08:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   15.547471] iwlagn 0000:08:00.0: irq 33 for MSI/MSI-X
[   15.620126] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   16.656239] r8169: eth0: link down
[ 3079.702610] r8169 0000:20:00.0: PCI INT A disabled
[ 3113.493226] iwlagn 0000:08:00.0: PCI INT A disabled
[ 3158.671067] cfg80211: Calling CRDA to update world regulatory domain
[ 3158.700975] cfg80211: World regulatory domain updated:
[ 3158.700981]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3158.700983]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3158.700985]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3158.700987]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3158.700989]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3158.714045] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[ 3158.714048] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[ 3158.714114] iwlagn 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 3158.714125] iwlagn 0000:08:00.0: setting latency timer to 64
[ 3158.714177] iwlagn 0000:08:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[ 3158.756242] iwlagn 0000:08:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 3158.756320] iwlagn 0000:08:00.0: irq 32 for MSI/MSI-X
[ 3158.757828] phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 3166.201660] iwlagn 0000:08:00.0: firmware: requesting iwlwifi-5000-2.ucode
[ 3166.238729] iwlagn 0000:08:00.0: loaded firmware version 8.24.2.12
[ 3166.389379] Registered led device: iwl-phy0::radio
[ 3166.389717] Registered led device: iwl-phy0::assoc
[ 3166.389784] Registered led device: iwl-phy0::RX
[ 3166.390286] Registered led device: iwl-phy0::TX
[ 3166.430727] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3611.941035] iwlagn 0000:08:00.0: PCI INT A disabled
[ 3617.051488] cfg80211: Calling CRDA to update world regulatory domain
[ 3617.063530] cfg80211: World regulatory domain updated:
[ 3617.063536]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3617.063538]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3617.063540]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3617.063542]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3617.063544]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3617.091518] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[ 3617.091521] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[ 3617.091599] iwlagn 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 3617.091610] iwlagn 0000:08:00.0: setting latency timer to 64
[ 3617.091666] iwlagn 0000:08:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[ 3617.133830] iwlagn 0000:08:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 3617.133908] iwlagn 0000:08:00.0: irq 32 for MSI/MSI-X
[ 3617.134262] phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 3635.474017] iwlagn 0000:08:00.0: firmware: requesting iwlwifi-5000-2.ucode
[ 3635.481969] iwlagn 0000:08:00.0: loaded firmware version 8.24.2.12
[ 3635.624781] Registered led device: iwl-phy0::radio
[ 3635.624971] Registered led device: iwl-phy0::assoc
[ 3635.625145] Registered led device: iwl-phy0::RX
[ 3635.625317] Registered led device: iwl-phy0::TX
[ 3635.653245] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3713.056730] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[ 3713.157409] cfg80211: Found new beacon on frequency: 5220 MHz (Ch 44) on phy0
[ 3715.005947] cfg80211: Found new beacon on frequency: 5745 MHz (Ch 149) on phy0
[ 3715.055419] cfg80211: Found new beacon on frequency: 5785 MHz (Ch 157) on phy0
[ 3727.032227] wlan0: direct probe to AP 00:1a:1e:19:1c:00 (try 1)
[ 3727.230036] wlan0: direct probe to AP 00:1a:1e:19:1c:00 (try 2)
[ 3727.235613] wlan0: direct probe responded
[ 3727.235616] wlan0: authenticate with AP 00:1a:1e:19:1c:00 (try 1)
[ 3727.244668] wlan0: authenticated
[ 3727.244682] wlan0: associate with AP 00:1a:1e:19:1c:00 (try 1)
[ 3727.251850] wlan0: RX AssocResp from 00:1a:1e:19:1c:00 (capab=0x421 status=0 aid=1)
[ 3727.251852] wlan0: associated
[ 3727.260846] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3737.871757] wlan0: no IPv6 routers present
[ 3926.962550] wlan0: deauthenticating from 00:1a:1e:19:1c:00 by local choice (reason=3)
[ 3929.409091] Registered led device: iwl-phy0::radio
[ 3929.409109] Registered led device: iwl-phy0::assoc
[ 3929.409123] Registered led device: iwl-phy0::RX
[ 3929.409136] Registered led device: iwl-phy0::TX
[ 3929.433122] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4016.913656] wlan0: direct probe to AP 00:1a:1e:19:1c:00 (try 1)
[ 4016.921767] wlan0: direct probe responded
[ 4016.921769] wlan0: authenticate with AP 00:1a:1e:19:1c:00 (try 1)
[ 4016.933075] wlan0: authenticated
[ 4016.933087] wlan0: associate with AP 00:1a:1e:19:1c:00 (try 1)
[ 4016.944029] wlan0: RX AssocResp from 00:1a:1e:19:1c:00 (capab=0x421 status=0 aid=1)
[ 4016.944031] wlan0: associated
[ 4016.949562] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4027.822532] wlan0: no IPv6 routers present

```(also, ubuntu forum's stupid rules dont allow a text file of more than 20KB, so I had to name the extension .doc, its stupid, I know. Its just a regular text file :confused:)

---

### Post by utilitytrack on 2010-10-23
> **erjoalgo said:**
> ...you don't have any more ideas, I understand.

Don't rush with conclusions.

**1)** Where the outputs that I asked? Only dmesg is here. For to clarify the trouble, I need all information what I requested.

**2)** Did you tried tips from my last post?

**3)** As I see, most simple solution on your case (if still you did everything correctly, which I doubt) it's install latest kernel 2.6.36 (from source, yes). And try again. So, if we can't get wireless working also in this case, my congratulations: we both found Kernel Bug. It's great honor. 

**4)** > **erjoalgo said:**
> But if you do, or anyone else, happens to find a solution, Im still looking for it.

You really believe that somebody found a solution? I tried, but without success on this time :) I noticed that on this forum and around the Internet a lot of reports about problems similar to your, somehow associated with drivers from ex-iwlwifi project, which are not resolved. 

Look in here:
[http://www.google.com/search?hl=en&newwindow=1&safe=off&q=%22No+DHCPOFFERS+received%22+%2Biwlagn&btnG=Search]("http://www.google.com/search?hl=en&newwindow=1&safe=off&q=%22No+DHCPOFFERS+received%22+%2Biwlagn&btnG=Search")

**5)** Finally, I think that this driver needed deep debugging with one of such problem AP. Because the problem and in it too. And your case it's very good testbed :)

So, don't worry, and try again all the same. But with a fresh mind.

**PS**
One thing: when you will test wireless, before you run DHCP client execute this:
```
# iw dev wlan0 scan > iwscan_campus.log
# iw dev wlan0 scan > iwscan_dorm.log
```

I need the results from two different places. Thanks.

---

### Post by utilitytrack on 2010-10-23
Here the continuation of my thoughts from previous post.

**6)** As I suspect (may be groundlessly), there is some difference in configuration of one AP (which on dorm) and other AP (wich on campus). So, it will be cool if we could to get access to their configs... 

You should to quickly get friendship with sysadmins of your University :) Think about it.

If it's some misconfiguration one of two this AP's, then we must to clarify what exactly it. For to check we must have access to configuration of these AP's. 

**7)** On the other hand, may be it's really only our driver bug? To check this are more easily. I already suggest to upgrade kernel. Here is some other thought. 

As I understand, in your Carnegie Mellon University all people are not rabid fanatics of Default OS? At least I hope on this. So, what if you will find somebody (I wish say: geeks) with Linux? I believe, these geeks will glad to help you. Show them this thread. They will have other hardware, obviously. But this is what we need! Ask them about wireless troubles in your dorm and on campus. Try to test the connection on their machines and check what the driver they use. At least half of questions will disappear at once! 

**8)** And finally, you should try to check wireless working everywhere outside your University. I hope that wireless networking are good developed in Pittsburgh. And you can connect to it for testing purposes.

You comments and notes are welcome, because I'm wondering your opinion.

---

### Post by erjoalgo on 2010-10-23
> (if still you did everything correctly, which I doubt)Yes Im pretty sure I did everything correctly, I was looking at the outputs. I just dont get an IP assigned. dhclient always says nodhcpoffers received...

> it's install latest kernel 2.6.36 (from source, yes).that seems waay out of my level right now...

> One thing: when you will test wireless, before you run DHCP client execute this:
# iw dev wlan0 scan > iwscan_campus.log # iw dev wlan0 scan > iwscan_dorm.logOk I will do that, and keep posting all results to this thread. But just sparingly, as Im pretty busy this week (I imagine you are too). Ill keep trying whenever I get a chance.
> 
So, if we can't get wireless working also in this case, my congratulations: we both found Kernel Bug. It's great honor. Lol, I dont doubt it, but I dont think its such an honor because they aren't rare at all. I had problems with sound, with hibernation, lots of bugs that I've spent countless hours trying to fish for a solution. Ubuntu has a lot of hardware problems I think; in general at least.
Yea man, thanks for your support.

---

### Post by rekkoo on 2010-10-24
Respect man! You are great anyway! There are lot of forums on internet and i never see even one where posting all your configuration and hundred of logs resolve any problem. That's because people just try, they never experience that type of problem but try to help and need all that stuff (logs) because MAYBE somewhere in logs will be "error - here is a bug!". It's something like trying to repair a car by replacing all elements - your car will work (of course this will be brand new car if you replace everything, but this is not important) and man who helps you will be satisfied and feels better then answering "I don't know". :) But real help you can get only from someone who has similar problem before and CAN resolve without asking for thousand questions. So if you describe your problem - look only for specific answers, do not feed log-hungry specialists.

---

### Post by utilitytrack on 2010-10-25
> **rekkoo said:**
> There are lot of forums on internet and i never see even one where posting all your configuration and hundred of logs resolve any problem.

Man, may be did you simply looking bad?

---

### Post by rekkoo on 2010-10-25
Maybe. Who knows, there is impossible to find all available forums. Then ok, 95% sounds better? But man, just plain answer - do you really need all configuration info and logs to find most possible reason and solution for problem if you have xx years experience?

---

### Post by utilitytrack on 2010-10-25
Man, if you have some good thought wich can solve the problems described in this thread, you are welcome.

---

### Post by rekkoo on 2010-10-26
My problem was that I have the same (or similar) problem as desribed in this thread and while looking for solution i found only standard asking for logs on every possible forums and no solution (and even silence after posting last log). I'm just sick of that asking for configuration and logs everywhere. Many times when I read some threads on other forums, I know solution even without asking for logs and configurations, but of course today every even small forum requires complex registration instead of moderation (people and scripts). Anyway - I know a solution, problem is simply (for example) and what I see? Of course asking for gfx card, processor, version of os, asking for hijackthis log (if this is windows forum), and good advices like "reinstall system" or "check system for viruses" in best case. This typical way of "helping" should be replaced by real help made by real computer-freaks, not people who trying. I can try to fix spaceship even if I don't know anything about that - is that good and someone should praise me just for trying? No, this is wasting of time and can be dangerous (in computer software case - can be destructive). As long as people will agree with that lame method of helping ("Let me try! Let me try!") every even simply problem will be difficult to resolve and internet will be full of garbage. Try to find typical blackout situation in specific gfx card - you'll find thousand of forums that people are forced to show their config (that contains gfx card of course) even if they have questions about mouse or keyboard.

I hope I'm not offensive. Criticism is positive. :)

---

### Post by utilitytrack on 2010-10-26
> **rekkoo said:**
> My problem was that I have the same (or similar) problem as desribed in this thread and while looking for solution i found only standard asking for logs on every possible forums and no solution (and even silence after posting last log). I'm just sick of that asking for configuration and logs everywhere. Many times when I read some threads on other forums, I know solution even without asking for logs and configurations, but of course today every even small forum requires complex registration instead of moderation (people and scripts). Anyway - I know a solution, problem is simply (for example) and what I see? Of course asking for gfx card, processor, version of os, asking for hijackthis log (if this is windows forum), and good advices like "reinstall system" or "check system for viruses" in best case. This typical way of "helping" should be replaced by real help made by real computer-freaks, not people who trying. I can try to fix spaceship even if I don't know anything about that - is that good and someone should praise me just for trying? No, this is wasting of time and can be dangerous (in computer software case - can be destructive). As long as people will agree with that lame method of helping ("Let me try! Let me try!") every even simply problem will be difficult to resolve and internet will be full of garbage. Try to find typical blackout situation in specific gfx card - you'll find thousand of forums that people are forced to show their config (that contains gfx card of course) even if they have questions about mouse or keyboard.

**rekkoo**,

May be I will be banned for this, but I tell: you are foolish troll.

---

### Post by grahammechanical on 2010-10-26
Utilitytrack

May I commend you for your persistence in trying to help erjoalgo with his wireless problem. I have not experienced any problems in using wireless in Ubuntu except recently when I began to test Ubuntustudio. It is very frustrating not being able to solve the problem. 

I have also tried in a small way to help on this forum. I feel concerned for those who ask for help but do not get any replies. I have little experience. I can only give simple suggestions. I sense also the frustration of those, like you, who are trying to help. Incomplete information makes it difficult to suggest a solution. Has the other person read the trouble shooting guides? Have they tried the suggestions listed there? We do not know unless we ask for logs. I just wish that I understood what the logs were saying and how they help to point to the answer.

You have dealt with erjoalgo in a kindly way. You have reassured him or her that you will continue to help. You set an example in how to assist from a distance someone solve a problem. Well done.

Regards - from an interested onlooker.

---

### Post by rekkoo on 2010-10-26
To utilitytrack: Over 90% of your post is my quoted text, answer for my opinion and arguments is just short message written only for offend me, all your "arguments" are short sentences like "foolish troll" or "may be did you simply looking bad". After that I must say that if I am a troll then is no words to describe who you are.

To grahammechanical: i respect that if someone trying to help, but after all I expect that if someone ask for logs and specifications, will have enough skill to help, not just collecting logs for sport. And people are trained to ask for logs every time. A small example - one person says that he has artefacts on his gfx card. I know what games he plays so I don't need to know what exactly model of gfx card he has. I has the same problems on few games so I can suspect that is probably lot of dust in radiator. And my suggestion is to remove card, use sticks and air to clean radiator and install one program that is simply for everyone, work with all cards that can show temperature and fan speed and, additionaly, can underclock a overheat gfx card. I do not need logs for that! I can suspect viruses, system, power suppply, memory, hard drive, dirt on slot, voltage - everything, but my experience tells me that my first solution was right. And I don't need for that any logs, system spec etc. Not at the beginning.

PS. Sorry for my english. I described a hypothetical situation above that show my point of view. I hope that someone will understand me instead of insult.

---

