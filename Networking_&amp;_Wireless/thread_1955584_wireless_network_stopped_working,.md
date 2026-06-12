---
title: "wireless network stopped working,"
date: 2012-04-09
forum: Networking &amp; Wireless
---

### Post by ph0852 on 2012-04-09
I have a Toshiba Satellite L655 running Ubuntu 10.04 LTS Lucid Lynx and dual booting Windows 7. Ubuntu connected to the internet via wireless for months. I'm not sure if the ethernet ever worked. Both wireless and ethernet connect via Windows. Suddenly the wireless stopped working, and that is when I found out the ethernet wasn't working either. Based on some of the searching I've done I'm including some diagnostic information from my system. 
&#12288;
$ uname -a
Linux topper 2.6.32-38-generic-pae #83-Ubuntu SMP Wed Jan 4 12:11:13 UTC 2012 i686 GNU/Linux
$ 
$ route
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
link-local * 255.255.0.0 U 0 0 0 wlan0
$ ping 192.168.1.1
connect: Network is unreachable
$ 
$ 
$ 
$ modinfo r8192se_pci
filename: /lib/modules/2.6.32-38-generic-pae/kernel/ubuntu/rtl8192se/r8192se_pci.ko
license: GPL
version: 0015.0127.2010
author: Copyright(c) 2008 - 2010 Realsil Semiconductor Corporation <wlanfae@realtek.com>
description: Linux driver for Realtek RTL819x WiFi cards
srcversion: 8EE3447BCD46102AE1B0943
alias: pci:v000010ECd00008174sv*sd*bc*sc*i*
alias: pci:v000010ECd00008173sv*sd*bc*sc*i*
alias: pci:v000010ECd00008172sv*sd*bc*sc*i*
alias: pci:v000010ECd00008171sv*sd*bc*sc*i*
depends: 
vermagic: 2.6.32-38-generic-pae SMP mod_unload modversions 586TSC 
parm: ifname: Net interface name, wlan%d=default (charp)
parm: hwwep: Try to use hardware WEP support(default use hw. set 0 to use software security) (int)
parm: channels: Channel bitmask for specific locales. NYI (int)
$ 
$ 
$ modinfo atl1c
filename: /lib/modules/2.6.32-38-generic-pae/kernel/drivers/net/atl1c/atl1c.ko
version: 1.0.0.1-NAPI
license: GPL
description: Atheros 1000M Ethernet Network Driver
author: Jie Yang <jie.yang@atheros.com>
srcversion: D9FBC84DA38EA0DA7672633
alias: pci:v00001969d00001062sv*sd*bc*sc*i*
alias: pci:v00001969d00001063sv*sd*bc*sc*i*
depends: 
vermagic: 2.6.32-38-generic-pae SMP mod_unload modversions 586TSC 
$ 
$ 
$ nm-tool
NetworkManager Tool
State: asleep
- Device: wlan0 ----------------------------------------------------------------
Type: 802.11 WiFi
Driver: rtl819xSE
State: unmanaged
Default: no
HW Address: 20:7C:8F:1E:CE:B2
Capabilities:
Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes
Wireless Access Points 
&#12288;
$ 
$ iwconfig
lo no wireless extensions.
wlan0 802.11bgn Nickname:"rtl8191SEVA2"
Mode:Managed Frequency=2.422 GHz Access Point: Not-Associated 
Bit Rate:300 Mb/s 
Retry:on RTS thr:off Fragment thr:off
Power Management:off
Link Quality=10/100 Signal level=0 dBm Noise level=-100 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
$ ifconfig 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:780 errors:0 dropped:0 overruns:0 frame:0
TX packets:780 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:62208 (62.2 KB) TX bytes:62208 (62.2 KB)
wlan0 Link encap:Ethernet HWaddr 20:7c:8f:1e:ce:b2 
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:16 Memory:f82d0000-f82d0100 
wlan0:avahi Link encap:Ethernet HWaddr 20:7c:8f:1e:ce:b2 
inet addr:169.254.9.167 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
Interrupt:16 Memory:f82d0000-f82d0100 
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
auto wlan0
iface wlan0 inet dhcp
$ 
$ lsmod | egrep "819|atl"
atl1c 28211 0 
r8192se_pci 448239 0 
$ lshw -C network
WARNING: you should run this program as super-user.
*-network 
description: Wireless interface
product: Realtek Semiconductor Co., Ltd.
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: wlan0
version: 10
serial: 20:7c:8f:1e:ce:b2
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=rtl819xSE driverversion=0015.0127.2010 firmware=62 latency=0 multicast=yes wireless=802.11bgn
resources: irq:16 ioport:3000(size=256) memory:d4400000-d4403fff
*-network UNCLAIMED
description: Ethernet controller
product: AR8152 v1.1 Fast Ethernet
vendor: Atheros Communications
physical id: 0
bus info: pci@0000:03:00.0
version: c1
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=0
resources: memory:d3400000-d343ffff ioport:2000(size=128)
$ sudo ifup eth0
[sudo] password for peter: 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
$ sudo ifup wlan0
ifup: interface wlan0 already configured
$ ip link show wlan0
2: wlan0: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
link/ether 20:7c:8f:1e:ce:b2 brd ff:ff:ff:ff:ff:ff
$ sudo ip link set wlan0 up
$ ip link show wlan0
2: wlan0: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
link/ether 20:7c:8f:1e:ce:b2 brd ff:ff:ff:ff:ff:ff
$ lspci | grep controller
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
03:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
$ lspci -n | grep ^0[23]:00
02:00.0 0280: 10ec:8172 (rev 10)
03:00.0 0200: 1969:2060 (rev c1)
&#12288;

---

### Post by chili555 on 2012-04-10
Please let us see:```
rfkill list all
dmesg | grep -e 819 -e wlan
```Thanks.

---

### Post by ph0852 on 2012-04-10
Thank you for the help!  The rfkill came back empty.
 
$ rfkill list all 
$ dmesg | grep -e 819 -e wlan
[ 16.139957] Linux kernel driver for RTL8192 based WLAN cards
[ 16.140350] rtl819xSE 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 16.140552] rtl819xSE 0000:02:00.0: setting latency timer to 64
[ 16.141367] Adapter(8192SE) is found - DeviceID=8172
[ 16.422819] Info fld=0x0, ILI
[ 16.704819] Info fld=0x10, ILI
[ 16.781999] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 17.206802] rtl819xSE 0000:02:00.0: firmware: requesting RTL8192SE/rtl8192sfw.bin
[ 17.395815] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 17.405671] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 38.659902] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
&#12288;

---

### Post by chili555 on 2012-04-10
> $ cat /etc/network/interfaces
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
auto wlan0
iface wlan0 inet dhcpThis implies that you will manage the interfaces and *NOT *Network Manager; i.e. NM will sit quietly and do nothing. Is that what you intend? Moreover, with no ESSID and encryption details declared it will never connect. It doesn't know to whom to connect!

Did you compile this from a tarball from Realtek by chance?

---

### Post by ph0852 on 2012-04-10
OK, point taken on the interfaces file.  It was a desparate act.  I don't think I compiled a tarball from realtek.  Is there a way to confirm?   I have compiled some things for the system, but I think they were all application related.
 
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
$ ping 192.168.1.1
connect: Network is unreachable
$ route
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
$ iwconfig
lo no wireless extensions.
wlan0 802.11bg Nickname:"rtl8191SEVA2"
Mode:Managed Frequency=2.457 GHz Access Point: Not-Associated 
Bit Rate:1 Mb/s 
Retry:on RTS thr:off Fragment thr:off
Power Management:off
Link Quality=10/100 Signal level=0 dBm Noise level=-100 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
$ nm-tool
NetworkManager Tool
State: asleep
- Device: wlan0 ----------------------------------------------------------------
Type: 802.11 WiFi
Driver: rtl819xSE
State: unmanaged
Default: no
HW Address: 20:7C:8F:1E:CE:B2
Capabilities:
Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes
Wireless Access Points 
&#12288;
&#12288;
peter@topper:~$ iwconfig
lo no wireless extensions.
wlan0 802.11bg Nickname:"rtl8191SEVA2"
Mode:Managed Frequency=2.457 GHz Access Point: Not-Associated 
Bit Rate:1 Mb/s 
Retry:on RTS thr:off Fragment thr:off
Power Management:off
Link Quality=10/100 Signal level=0 dBm Noise level=-100 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
&#12288;
$ sudo iwlist wlan0 scan
[sudo] password for peter: 
wlan0 Interface doesn't support scanning : Network is down
&#12288;
&#12288;

---

### Post by chili555 on 2012-04-10
> I don't think I compiled a tarball from realtek. Is there a way to confirm? Please try:```
sudo updatedb
locate rtl8192se.ko
```You will certainly find one in /lib/modules/.. but maybe another in something like:> rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192se/rtl8192se.koThe latter is the remainder from a compiled version.

What is Network Manager doing all this time? When you click the icon, do you see your network? What clues are here?```
sudo cat /var/log/syslog | grep -e wlan -e etwork | tail -n20
```

---

### Post by ph0852 on 2012-04-10
Re: wireless network stopped working, 
Quote: 

I don't think I compiled a tarball from realtek. Is there a way to confirm? 
Please try: 
Code:
sudo updatedb
locate rtl8192se.ko
You will certainly find one in /lib/modules/.. but maybe another in something like: 
Quote: 

rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192se/rtl8192se.ko 
The latter is the remainder from a compiled version.
peter@topper:~$ locate rtl8192se.ko
peter@topper:~$ locate rtl8192se
/lib/modules/2.6.32-24-generic-pae/kernel/ubuntu/rtl8192se
/lib/modules/2.6.32-24-generic-pae/kernel/ubuntu/rtl8192se/r8192se_pci.ko
/lib/modules/2.6.32-25-generic-pae/kernel/ubuntu/rtl8192se
/lib/modules/2.6.32-25-generic-pae/kernel/ubuntu/rtl8192se/r8192se_pci.ko
/lib/modules/2.6.32-26-generic-pae/kernel/ubuntu/rtl8192se
/lib/modules/2.6.32-26-generic-pae/kernel/ubuntu/rtl8192se/r8192se_pci.ko
/lib/modules/2.6.32-27-generic-pae/kernel/ubuntu/rtl8192se
/lib/modules/2.6.32-27-generic-pae/kernel/ubuntu/rtl8192se/r8192se_pci.ko
/lib/modules/2.6.32-28-generic-pae/kernel/ubuntu/rtl8192se
/lib/modules/2.6.32-28-generic-pae/kernel/ubuntu/rtl8192se/r8192se_pci.ko
/lib/modules/2.6.32-29-generic-pae/kernel/ubuntu/rtl8192se
/lib/modules/2.6.32-29-generic-pae/kernel/ubuntu/rtl8192se/r8192se_pci.ko
/lib/modules/2.6.32-30-generic-pae/kernel/ubuntu/rtl8192se
/lib/modules/2.6.32-30-generic-pae/kernel/ubuntu/rtl8192se/r8192se_pci.ko
/lib/modules/2.6.32-31-generic-pae/kernel/ubuntu/rtl8192se
/lib/modules/2.6.32-31-generic-pae/kernel/ubuntu/rtl8192se/r8192se_pci.ko
/lib/modules/2.6.32-32-generic-pae/kernel/ubuntu/rtl8192se
/lib/modules/2.6.32-32-generic-pae/kernel/ubuntu/rtl8192se/r8192se_pci.ko
/lib/modules/2.6.32-33-generic-pae/kernel/ubuntu/rtl8192se
/lib/modules/2.6.32-33-generic-pae/kernel/ubuntu/rtl8192se/r8192se_pci.ko
/lib/modules/2.6.32-34-generic-pae/kernel/ubuntu/rtl8192se
/lib/modules/2.6.32-34-generic-pae/kernel/ubuntu/rtl8192se/r8192se_pci.ko
/lib/modules/2.6.32-35-generic-pae/kernel/ubuntu/rtl8192se
/lib/modules/2.6.32-35-generic-pae/kernel/ubuntu/rtl8192se/r8192se_pci.ko
/lib/modules/2.6.32-36-generic-pae/kernel/ubuntu/rtl8192se
/lib/modules/2.6.32-36-generic-pae/kernel/ubuntu/rtl8192se/r8192se_pci.ko
/lib/modules/2.6.32-37-generic-pae/kernel/ubuntu/rtl8192se
/lib/modules/2.6.32-37-generic-pae/kernel/ubuntu/rtl8192se/r8192se_pci.ko
/lib/modules/2.6.32-38-generic-pae/kernel/ubuntu/rtl8192se
/lib/modules/2.6.32-38-generic-pae/kernel/ubuntu/rtl8192se/r8192se_pci.ko
/usr/src/linux-headers-2.6.32-24/ubuntu/rtl8192se
/usr/src/linux-headers-2.6.32-24/ubuntu/rtl8192se/Kconfig
/usr/src/linux-headers-2.6.32-24/ubuntu/rtl8192se/Makefile
/usr/src/linux-headers-2.6.32-24/ubuntu/rtl8192se/rtl8192s
/usr/src/linux-headers-2.6.32-24/ubuntu/rtl8192se/rtllib
/usr/src/linux-headers-2.6.32-24/ubuntu/rtl8192se/rtl8192s/Makefile
/usr/src/linux-headers-2.6.32-24/ubuntu/rtl8192se/rtllib/Makefile
/usr/src/linux-headers-2.6.32-24-generic-pae/include/config/rtl8192se.h
/usr/src/linux-headers-2.6.32-25/ubuntu/rtl8192se
/usr/src/linux-headers-2.6.32-25/ubuntu/rtl8192se/Kconfig
/usr/src/linux-headers-2.6.32-25/ubuntu/rtl8192se/Makefile
/usr/src/linux-headers-2.6.32-25/ubuntu/rtl8192se/rtl8192s
/usr/src/linux-headers-2.6.32-25/ubuntu/rtl8192se/rtllib
/usr/src/linux-headers-2.6.32-25/ubuntu/rtl8192se/rtl8192s/Makefile
/usr/src/linux-headers-2.6.32-25/ubuntu/rtl8192se/rtllib/Makefile
/usr/src/linux-headers-2.6.32-25-generic-pae/include/config/rtl8192se.h
/usr/src/linux-headers-2.6.32-26/ubuntu/rtl8192se
/usr/src/linux-headers-2.6.32-26/ubuntu/rtl8192se/Kconfig
/usr/src/linux-headers-2.6.32-26/ubuntu/rtl8192se/Makefile
/usr/src/linux-headers-2.6.32-26/ubuntu/rtl8192se/rtl8192s
/usr/src/linux-headers-2.6.32-26/ubuntu/rtl8192se/rtllib
/usr/src/linux-headers-2.6.32-26/ubuntu/rtl8192se/rtl8192s/Makefile
/usr/src/linux-headers-2.6.32-26/ubuntu/rtl8192se/rtllib/Makefile
/usr/src/linux-headers-2.6.32-26-generic-pae/include/config/rtl8192se.h
/usr/src/linux-headers-2.6.32-27/ubuntu/rtl8192se
/usr/src/linux-headers-2.6.32-27/ubuntu/rtl8192se/Kconfig
/usr/src/linux-headers-2.6.32-27/ubuntu/rtl8192se/Makefile
/usr/src/linux-headers-2.6.32-27/ubuntu/rtl8192se/rtl8192s
/usr/src/linux-headers-2.6.32-27/ubuntu/rtl8192se/rtllib
/usr/src/linux-headers-2.6.32-27/ubuntu/rtl8192se/rtl8192s/Makefile
/usr/src/linux-headers-2.6.32-27/ubuntu/rtl8192se/rtllib/Makefile
/usr/src/linux-headers-2.6.32-27-generic-pae/include/config/rtl8192se.h
/usr/src/linux-headers-2.6.32-28/ubuntu/rtl8192se
/usr/src/linux-headers-2.6.32-28/ubuntu/rtl8192se/Kconfig
/usr/src/linux-headers-2.6.32-28/ubuntu/rtl8192se/Makefile
/usr/src/linux-headers-2.6.32-28/ubuntu/rtl8192se/rtl8192s
/usr/src/linux-headers-2.6.32-28/ubuntu/rtl8192se/rtllib
/usr/src/linux-headers-2.6.32-28/ubuntu/rtl8192se/rtl8192s/Makefile
/usr/src/linux-headers-2.6.32-28/ubuntu/rtl8192se/rtllib/Makefile
/usr/src/linux-headers-2.6.32-28-generic-pae/include/config/rtl8192se.h
/usr/src/linux-headers-2.6.32-29/ubuntu/rtl8192se
/usr/src/linux-headers-2.6.32-29/ubuntu/rtl8192se/Kconfig
/usr/src/linux-headers-2.6.32-29/ubuntu/rtl8192se/Makefile
/usr/src/linux-headers-2.6.32-29/ubuntu/rtl8192se/rtl8192s
/usr/src/linux-headers-2.6.32-29/ubuntu/rtl8192se/rtllib
/usr/src/linux-headers-2.6.32-29/ubuntu/rtl8192se/rtl8192s/Makefile
/usr/src/linux-headers-2.6.32-29/ubuntu/rtl8192se/rtllib/Makefile
/usr/src/linux-headers-2.6.32-29-generic-pae/include/config/rtl8192se.h
/usr/src/linux-headers-2.6.32-30/ubuntu/rtl8192se
/usr/src/linux-headers-2.6.32-30/ubuntu/rtl8192se/Kconfig
/usr/src/linux-headers-2.6.32-30/ubuntu/rtl8192se/Makefile
/usr/src/linux-headers-2.6.32-30/ubuntu/rtl8192se/rtl8192s
/usr/src/linux-headers-2.6.32-30/ubuntu/rtl8192se/rtllib
/usr/src/linux-headers-2.6.32-30/ubuntu/rtl8192se/rtl8192s/Makefile
/usr/src/linux-headers-2.6.32-30/ubuntu/rtl8192se/rtllib/Makefile
/usr/src/linux-headers-2.6.32-30-generic-pae/include/config/rtl8192se.h
/usr/src/linux-headers-2.6.32-31/ubuntu/rtl8192se
/usr/src/linux-headers-2.6.32-31/ubuntu/rtl8192se/Kconfig
/usr/src/linux-headers-2.6.32-31/ubuntu/rtl8192se/Makefile
/usr/src/linux-headers-2.6.32-31/ubuntu/rtl8192se/rtl8192s
/usr/src/linux-headers-2.6.32-31/ubuntu/rtl8192se/rtllib
/usr/src/linux-headers-2.6.32-31/ubuntu/rtl8192se/rtl8192s/Makefile
/usr/src/linux-headers-2.6.32-31/ubuntu/rtl8192se/rtllib/Makefile
/usr/src/linux-headers-2.6.32-31-generic-pae/include/config/rtl8192se.h
/usr/src/linux-headers-2.6.32-32/ubuntu/rtl8192se
/usr/src/linux-headers-2.6.32-32/ubuntu/rtl8192se/Kconfig
/usr/src/linux-headers-2.6.32-32/ubuntu/rtl8192se/Makefile
/usr/src/linux-headers-2.6.32-32/ubuntu/rtl8192se/rtl8192s
/usr/src/linux-headers-2.6.32-32/ubuntu/rtl8192se/rtllib
/usr/src/linux-headers-2.6.32-32/ubuntu/rtl8192se/rtl8192s/Makefile
/usr/src/linux-headers-2.6.32-32/ubuntu/rtl8192se/rtllib/Makefile
/usr/src/linux-headers-2.6.32-32-generic-pae/include/config/rtl8192se.h
/usr/src/linux-headers-2.6.32-33/ubuntu/rtl8192se
/usr/src/linux-headers-2.6.32-33/ubuntu/rtl8192se/Kconfig
/usr/src/linux-headers-2.6.32-33/ubuntu/rtl8192se/Makefile
/usr/src/linux-headers-2.6.32-33/ubuntu/rtl8192se/rtl8192s
/usr/src/linux-headers-2.6.32-33/ubuntu/rtl8192se/rtllib
/usr/src/linux-headers-2.6.32-33/ubuntu/rtl8192se/rtl8192s/Makefile
/usr/src/linux-headers-2.6.32-33/ubuntu/rtl8192se/rtllib/Makefile
/usr/src/linux-headers-2.6.32-33-generic-pae/include/config/rtl8192se.h
/usr/src/linux-headers-2.6.32-34/ubuntu/rtl8192se
/usr/src/linux-headers-2.6.32-34/ubuntu/rtl8192se/Kconfig
/usr/src/linux-headers-2.6.32-34/ubuntu/rtl8192se/Makefile
/usr/src/linux-headers-2.6.32-34/ubuntu/rtl8192se/rtl8192s
/usr/src/linux-headers-2.6.32-34/ubuntu/rtl8192se/rtllib
/usr/src/linux-headers-2.6.32-34/ubuntu/rtl8192se/rtl8192s/Makefile
/usr/src/linux-headers-2.6.32-34/ubuntu/rtl8192se/rtllib/Makefile
/usr/src/linux-headers-2.6.32-34-generic-pae/include/config/rtl8192se.h
/usr/src/linux-headers-2.6.32-35/ubuntu/rtl8192se
/usr/src/linux-headers-2.6.32-35/ubuntu/rtl8192se/Kconfig
/usr/src/linux-headers-2.6.32-35/ubuntu/rtl8192se/Makefile
/usr/src/linux-headers-2.6.32-35/ubuntu/rtl8192se/rtl8192s
/usr/src/linux-headers-2.6.32-35/ubuntu/rtl8192se/rtllib
/usr/src/linux-headers-2.6.32-35/ubuntu/rtl8192se/rtl8192s/Makefile
/usr/src/linux-headers-2.6.32-35/ubuntu/rtl8192se/rtllib/Makefile
/usr/src/linux-headers-2.6.32-35-generic-pae/include/config/rtl8192se.h
/usr/src/linux-headers-2.6.32-36/ubuntu/rtl8192se
/usr/src/linux-headers-2.6.32-36/ubuntu/rtl8192se/Kconfig
/usr/src/linux-headers-2.6.32-36/ubuntu/rtl8192se/Makefile
/usr/src/linux-headers-2.6.32-36/ubuntu/rtl8192se/rtl8192s
/usr/src/linux-headers-2.6.32-36/ubuntu/rtl8192se/rtllib
/usr/src/linux-headers-2.6.32-36/ubuntu/rtl8192se/rtl8192s/Makefile
/usr/src/linux-headers-2.6.32-36/ubuntu/rtl8192se/rtllib/Makefile
/usr/src/linux-headers-2.6.32-36-generic-pae/include/config/rtl8192se.h
/usr/src/linux-headers-2.6.32-37/ubuntu/rtl8192se
/usr/src/linux-headers-2.6.32-37/ubuntu/rtl8192se/Kconfig
/usr/src/linux-headers-2.6.32-37/ubuntu/rtl8192se/Makefile
/usr/src/linux-headers-2.6.32-37/ubuntu/rtl8192se/rtl8192s
/usr/src/linux-headers-2.6.32-37/ubuntu/rtl8192se/rtllib
/usr/src/linux-headers-2.6.32-37/ubuntu/rtl8192se/rtl8192s/Makefile
/usr/src/linux-headers-2.6.32-37/ubuntu/rtl8192se/rtllib/Makefile
/usr/src/linux-headers-2.6.32-37-generic-pae/include/config/rtl8192se.h
/usr/src/linux-headers-2.6.32-38/ubuntu/rtl8192se
/usr/src/linux-headers-2.6.32-38/ubuntu/rtl8192se/Kconfig
/usr/src/linux-headers-2.6.32-38/ubuntu/rtl8192se/Makefile
/usr/src/linux-headers-2.6.32-38/ubuntu/rtl8192se/rtl8192s
/usr/src/linux-headers-2.6.32-38/ubuntu/rtl8192se/rtllib
/usr/src/linux-headers-2.6.32-38/ubuntu/rtl8192se/rtl8192s/Makefile
/usr/src/linux-headers-2.6.32-38/ubuntu/rtl8192se/rtllib/Makefile
/usr/src/linux-headers-2.6.32-38-generic-pae/include/config/rtl8192se.h
&#12288;
What is Network Manager doing all this time? When you click the icon, do you see your network? What clues are here? 
The icon is gone, disappeared. 
**How hard is it to get the Network Manager icon back?**
 
Code:
sudo cat /var/log/syslog | grep -e wlan -e etwork | tail -n20
__________________
udo cat /var/log/syslog | grep -e wlan -e etwork | tail -n20
Apr 10 19:51:39 topper NetworkManager: SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.4/0000:02:00.0/net/wlan0, iface: wlan0)
Apr 10 19:51:39 topper NetworkManager: SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.4/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Apr 10 19:51:39 topper NetworkManager: SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Apr 10 19:51:39 topper NetworkManager: SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Apr 10 19:51:39 topper NetworkManager: SCPlugin-Ifupdown: end _init.
Apr 10 19:51:39 topper NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd. To report bugs please use the NetworkManager mailing list.
Apr 10 19:51:39 topper NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc. To report bugs please use the NetworkManager mailing list.
Apr 10 19:51:39 topper NetworkManager: <info> WiFi enabled by radio killswitch; enabled by state file
Apr 10 19:51:39 topper NetworkManager: <info> WWAN enabled by radio killswitch; enabled by state file
Apr 10 19:51:39 topper NetworkManager: SCPlugin-Ifupdown: (154239216) ... get_connections.
Apr 10 19:51:39 topper NetworkManager: SCPlugin-Ifupdown: (154239216) connections count: 0
Apr 10 19:51:39 topper NetworkManager: <info> (wlan0): driver supports SSID scans (scan_capa 0x21).
Apr 10 19:51:39 topper NetworkManager: <info> (wlan0): new 802.11 WiFi device (driver: 'rtl819xSE')
Apr 10 19:51:39 topper NetworkManager: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 10 19:51:39 topper NetworkManager: <WARN> default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Apr 10 19:51:39 topper NetworkManager: <info> modem-manager is now available
Apr 10 19:51:39 topper NetworkManager: <info> Trying to start the supplicant...
Apr 10 19:51:39 topper NetworkManager: <info> (wlan0): supplicant manager state: down -> idle
Apr 10 19:51:39 topper kernel: [ 17.467949] type=1505 audit(1334105499.251:7): operation="profile_replace" pid=1076 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Apr 10 19:51:39 topper avahi-daemon[984]: Network interface enumeration completed.
&#12288;

---

### Post by chili555 on 2012-04-10
> The icon is gone, disappeared.
How hard is it to get the Network Manager icon back?This may be the root of the problem. In a terminal do:```
nm-applet &
```Leave the terminal open and running. See if the icon doesn't reappear. Can you click it, see networks and connect?

Off for the evening; see you tomorrow.

---

### Post by ph0852 on 2012-04-10
Nothing is showing on the display.  Does nm-applet have a log file?  Or can I turn on any diagnostics?
 
nm-applet &
[1] 1810
$ An instance of nm-applet is already running.
** (nm-applet:1810): WARNING **: <WARN> constructor(): Couldn't initialize the D-Bus manager.
&#12288;
[1]+ Exit 1 nm-applet
$ ps -ef | grep nm-applet
peter 1608 1537 0 21:03 ? 00:00:00 nm-applet --sm-disable
peter 1828 1727 0 21:04 pts/0 00:00:00 grep --color=auto nm-applet
$ kill -9 1608
$ ps -ef | grep nm-applet
peter 1830 1727 0 21:04 pts/0 00:00:00 grep --color=auto nm-applet
$ ps -ef | grep nm-applet
peter 1832 1727 0 21:04 pts/0 00:00:00 grep --color=auto nm-applet
$ cat /var/log/syslog | grep nm-applet
nm-applet &
[1] 1841
peter@topper:/media/PENDRIVE/wlan0$ ** (nm-applet:1841): DEBUG: old state indicates that this was not a disconnect 0
peter@topper:/media/PENDRIVE/wlan0$ ps -ef | grep nm-applet
peter 1841 1727 0 21:08 pts/0 00:00:00 nm-applet
peter 1844 1727 0 21:09 pts/0 00:00:00 grep --color=auto nm-applet
&#12288;

---

### Post by ph0852 on 2012-04-12
It started working.  No idea why, except that I left the case closed while I was at work.   When I reopened the case I sent a ping that was answered.

iwconfig
lo        no wireless extensions.

wlan0     802.11bg  ESSID:"BournAvenue"  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:16:B6:C5:8E:CA   
          Bit Rate=54 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management period:0us  mode:All packets received
          Link Quality=87/100  Signal level=-53 dBm  Noise level=-113 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

peter@topper:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:423 errors:0 dropped:0 overruns:0 frame:0
          TX packets:423 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:33627 (33.6 KB)  TX bytes:33627 (33.6 KB)

wlan0     Link encap:Ethernet  HWaddr 20:7c:8f:1e:ce:b2  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::227c:8fff:fe1e:ceb2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7665 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6657 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8256235 (8.2 MB)  TX bytes:1074082 (1.0 MB)
          Interrupt:16 Memory:f82a8000-f82a8100 

Thank you chili555 for looking at it.

---

