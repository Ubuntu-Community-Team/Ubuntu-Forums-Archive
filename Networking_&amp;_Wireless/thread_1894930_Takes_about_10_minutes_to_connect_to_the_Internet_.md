---
title: "Takes about 10 minutes to connect to the Internet after booting"
date: 2011-12-13
forum: Networking &amp; Wireless
---

### Post by JeyPeyy on 2011-12-13
Ever since I upgraded to 11.10 on my stationary PC I've had problems with connecting to the wired network. I have to wait about 10 minutes before I can get on the Internet or even my local network. The ethernet-port is showing no signal. I've tried both KDE and Gnome (with both Unity and GS) but none willl work. Windows 7 works nicely though.

ifconfig before access to the network: 
```
eth0 Link encap:Ethernet HWaddr 00:1d:92:f1:39:12
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:44 Base address:0xe000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:4 errors:0 dropped:0 overruns:0 frame:0
TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:240 (240.0 B) TX bytes:240 (240.0 B)
```

ifconfig when access to the network
```
eth0 Link encap:Ethernet HWaddr 00:1d:92:f1:39:12
inet addr:192.168.0.194 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::21d:92ff:fef1:3912/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:273 errors:0 dropped:0 overruns:0 frame:0
TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:28826 (28.8 KB) TX bytes:25003 (25.0 KB)
Interrupt:44 Base address:0xe000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:4 errors:0 dropped:0 overruns:0 frame:0
TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:240 (240.0 B) TX bytes:240 (240.0 B)
```

```

$ sudo lshw -c network; lspci -nnn | grep -i Ethernet; ifconfig -a; iwlist wlan0 scanning; rfkill list; lsb_release -a

*-network
description: Ethernet interface
product: RTL8111/8168B PCI Express Gigabit Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:04:00.0
logical name: eth0
version: 01
serial: 00:1d:92:f1:39:12
size: 100Mbit/s
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.0.194 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
resources: irq:44 ioport:d800(size=256) memory:feaff000-feafffff memory:feac0000-feadffff
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)
eth0 Link encap:Ethernet HWaddr 00:1d:92:f1:39:12
inet addr:192.168.0.194 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::21d:92ff:fef1:3912/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:654699 errors:0 dropped:0 overruns:0 frame:0
TX packets:550115 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:592143029 (592.1 MB) TX bytes:206730620 (206.7 MB)
Interrupt:44 Base address:0xe000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:836 errors:0 dropped:0 overruns:0 frame:0
TX packets:836 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:54232 (54.2 KB) TX bytes:54232 (54.2 KB)

wlan0 Interface doesn't support scanning.

No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 11.10
Release: 11.10
Codename: oneiric
```

I actually asked my local forum (ubuntu sweden) before posting here. They said it's a [known bug for 64-bit Ubuntu 11.10 ]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/889646") and asked me to try the 32-bit live cd. Sadly it didn't work, so I'm not sure if it's the same bug.

---

### Post by BC59 on 2011-12-13
I had a similar problem and I was trying every possible solution. The problem was solved when I had to reinstall the system. In the new installation the connection worked instantaneously.

---

### Post by JeyPeyy on 2011-12-13
> **BC59 said:**
> I had a similar problem and I was trying every possible solution. The problem was solved when I had to reinstall the system. In the new installation the connection worked instantaneously.

Well since the 32-bit live cd isn't working either I'm assuming reinstalling won't help. But maybe I should try it when my exams are done.

---

### Post by praseodym on 2011-12-13
Hi,

replace the driver r816[COLOR="Red"]9[/COLOR] with r816[COLOR="Red"]8[/COLOR]:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
wget http://r8168.googlecode.com/files/r8168-8.027.00.tar.bz2
tar xvf r8168-8.027.00.tar.bz2
cd r8168-8.027.00/
sudo sh ./autorun.sh
```
Install the metapackage of the kernel-headers suitable to your kernel architechture, too (e.g. linux-headers-generic, -generic-pae, whatever).

---

### Post by JeyPeyy on 2011-12-13
> **praseodym said:**
> Hi,

replace the driver r816[COLOR="Red"]9[/COLOR] with r816[COLOR="Red"]8[/COLOR]:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
wget http://r8168.googlecode.com/files/r8168-8.027.00.tar.bz2
tar xvf r8168-8.027.00.tar.bz2
cd r8168-8.027.00/
sudo sh ./autorun.sh
```
Install the metapackage of the kernel-headers suitable to your kernel architechture, too (e.g. linux-headers-generic, -generic-pae, whatever).

That worked! Thank you so much!

---

### Post by dandnsmith on 2011-12-13
There's a couple of threads relating to chipsets which use the r8169 driver giving trouble. One of them helped me to a solution by swapping (as previous post) the r8169 for the r8168 - which doesn't have the same problems. There were some ameliorative measures, mostly related to PCs which also used Windows - but they didn't work for me.
One bit of info related to replacing the driver used in the initramfs for the system - a process which I found useful.

A previous post of mine quotes the relative threads (which I don't have the links for to hand).

---

