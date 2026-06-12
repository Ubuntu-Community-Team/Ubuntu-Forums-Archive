---
title: "[Challange, very weird] Internet connection problem on wired ubuntu 10.4"
date: 2012-02-28
forum: Networking &amp; Wireless
---

### Post by matismasters on 2012-02-28
Problem:
My internet connection its not working properly, maybe 1 of 5 requests I made works, the behaviour its that I try a few times going for a URL in the browser, and it doesn't work, but then like the third or fourth it works, I follow 2 or 3 links, and still works, but then again the invalid requests.

My guess given the little I know:
After running some commands, that I will copy paste at the bottom of this post, I found out that the connection was kind of reestablished several times per minute, so my guess is that I don't know why the connection keeps reconnecting again.

Scenario:
I have installed Ubuntu 10.4 on my desktop PC, via Wubi, over Windows 7. In windows the connection works perfectly well, with the same hardware, this leaves rolls out bad cable, etc. 
I also took my PC to my office, where I have the same set up, but with a different router, and the problem still persists, on windows fine, on ubuntu not working properly.
Its a wired connection, an ethernet cable connected directly to the router.
I'm using DHCP, getting my IP and DNS automatically from the router, for configuring that I've used gnome-network-admin, the applet at the right top corner of ubuntu 10.4, I've never touched a file called interface (that I see at some posts around that was being used.
Activating and deactivating IPv6 doesn't work, its deactivated right now through gnome-network-admin.
The problem is not only on web browsing, also using git, or irc, or anything internet related.
Its also not a bandwidth problem since when I do the ping command, its most of the time the same response time, but at some point, its delay, and then it throws an "unkown host", so badwidth availability varying is not an option.

Hardware and configuration commands:
Here I'll list the commands I ran and the result.


$ lspci
```

00:00.0 Host bridge: Advanced Micro Devices [AMD] Device 1705
00:02.0 PCI bridge: Advanced Micro Devices [AMD] Device 1707
00:10.0 USB Controller: Advanced Micro Devices [AMD] Device 7812 (rev 03)
00:10.1 USB Controller: Advanced Micro Devices [AMD] Device 7812 (rev 03)
00:11.0 SATA controller: Advanced Micro Devices [AMD] Device 7800 (rev 40)
00:12.0 USB Controller: Advanced Micro Devices [AMD] Device 7807 (rev 11)
00:12.2 USB Controller: Advanced Micro Devices [AMD] Device 7808 (rev 11)
00:13.0 USB Controller: Advanced Micro Devices [AMD] Device 7807 (rev 11)
00:13.2 USB Controller: Advanced Micro Devices [AMD] Device 7808 (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Device 780b (rev 13)
00:14.1 IDE interface: Advanced Micro Devices [AMD] Device 780c
00:14.2 Audio device: Advanced Micro Devices [AMD] Device 780d (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Device 780e (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Device 780f (rev 40)
00:14.5 USB Controller: Advanced Micro Devices [AMD] Device 7809 (rev 11)
00:15.0 PCI bridge: Advanced Micro Devices [AMD] Device 43a0
00:15.1 PCI bridge: Advanced Micro Devices [AMD] Device 43a1
00:18.0 Host bridge: Advanced Micro Devices [AMD] Device 1700 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Device 1701
00:18.2 Host bridge: Advanced Micro Devices [AMD] Device 1702
00:18.3 Host bridge: Advanced Micro Devices [AMD] Device 1703
00:18.4 Host bridge: Advanced Micro Devices [AMD] Device 1704
00:18.5 Host bridge: Advanced Micro Devices [AMD] Device 1718
00:18.6 Host bridge: Advanced Micro Devices [AMD] Device 1716
00:18.7 Host bridge: Advanced Micro Devices [AMD] Device 1719
01:00.0 VGA compatible controller: ATI Technologies Inc Device 6759
01:00.1 Audio device: ATI Technologies Inc Device aa90
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

```

$ ifconfig

```

eth0      Link encap:Ethernet  addressHW 14:da:e9:15:44:92  
          Address. inet:192.168.1.2  Broadcast.:192.168.1.255  Mask:255.255.255.0
          Address inet6: fe80::16da:e9ff:fe15:4492/64 Reach:Link
          ACTIVE BROADCAST WORKING MULTICAST  MTU:1500  Métrica:1
          Packages RX:3840 errors:0 lost:3840 overruns:0 frame:3840
          Packages TX:2531 errors:0 lost:9 overruns:0 carrier:0
          collitions:0 long.colaTX:1000 
          Bytes RX:4451627 (4.4 MB)  TX bytes:212964 (212.9 KB)
          Interruptions:27 Base address: 0xa000 

lo        Link encap:Loop local  
          Address inet:127.0.0.1  Mask:255.0.0.0
          Address inet6: ::1/128 Reach:Host
          ACTIVE LOOP WORKING  MTU:16436  Métrica:1
          Packages RX:48 errors:0 lost:0 overruns:0 frame:0
          Packages TX:48 errors:0 lost:0 overruns:0 carrier:0
          collitions:0 long.colaTX:0 
          Bytes RX:3874 (3.8 KB)  TX bytes:3874 (3.8 KB)


```
I translated word by word from spanish to english, because my ubuntu is installed in spanish. 
$ ping google.com


```

64 bytes from 173.194.76.138: icmp_seq=22 ttl=48 time=171 ms
64 bytes from 173.194.76.138: icmp_seq=23 ttl=47 time=172 ms
64 bytes from 173.194.76.138: icmp_seq=24 ttl=48 time=171 ms
64 bytes from 173.194.76.138: icmp_seq=25 ttl=48 time=175 ms
64 bytes from 173.194.76.138: icmp_seq=26 ttl=48 time=177 ms
From ubuntu.local (192.168.1.2) icmp_seq=68 Destination Host Unreachable
From ubuntu.local (192.168.1.2) icmp_seq=69 Destination Host Unreachable
From ubuntu.local (192.168.1.2) icmp_seq=70 Destination Host Unreachable
From ubuntu.local (192.168.1.2) icmp_seq=71 Destination Host Unreachable
From 192.168.1.2 (192.168.1.2) icmp_seq=72 Destination Host Unreachable
From 192.168.1.2 (192.168.1.2) icmp_seq=73 Destination Host Unreachable
From 192.168.1.2 (192.168.1.2) icmp_seq=74 Destination Host Unreachable
64 bytes from 173.194.76.138: icmp_seq=75 ttl=48 time=182 ms
64 bytes from 173.194.76.138: icmp_seq=76 ttl=48 time=174 ms

```

$ tail /var/log/messages

```

Feb 28 13:34:18 ubuntu kernel: [ 3264.082912] r8169: eth0: link up
Feb 28 13:34:26 ubuntu kernel: [ 3272.410427] r8169: eth0: link up
Feb 28 13:34:31 ubuntu kernel: [ 3277.970408] r8169: eth0: link up
Feb 28 13:34:40 ubuntu kernel: [ 3286.960420] r8169: eth0: link up
Feb 28 13:34:49 ubuntu kernel: [ 3295.380420] r8169: eth0: link up
Feb 28 13:35:12 ubuntu kernel: [ 3318.090412] r8169: eth0: link up
Feb 28 13:35:18 ubuntu kernel: [ 3324.870420] r8169: eth0: link up
Feb 28 13:44:00 ubuntu kernel: [ 3846.094161] r8169: eth0: link up
Feb 28 14:00:39 ubuntu kernel: [ 4845.620409] r8169: eth0: link up
Feb 28 14:06:39 ubuntu kernel: [ 5205.680407] r8169: eth0: link up

```

$ ip addr

```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 14:da:e9:15:44:92 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.2/24 brd 192.168.1.255 scope global eth0
    inet6 fe80::16da:e9ff:fe15:4492/64 scope link 
       valid_lft forever preferred_lft forever

```

$ ip route show table all

```

192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.2  metric 1 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.1.1 dev eth0  proto static 
broadcast 192.168.1.0 dev eth0  table local  proto kernel  scope link  src 192.168.1.2 
broadcast 127.255.255.255 dev lo  table local  proto kernel  scope link  src 127.0.0.1 
local 192.168.1.2 dev eth0  table local  proto kernel  scope host  src 192.168.1.2 
broadcast 192.168.1.255 dev eth0  table local  proto kernel  scope link  src 192.168.1.2 
broadcast 127.0.0.0 dev lo  table local  proto kernel  scope link  src 127.0.0.1 
local 127.0.0.1 dev lo  table local  proto kernel  scope host  src 127.0.0.1 
local 127.0.0.0/8 dev lo  table local  proto kernel  scope host  src 127.0.0.1 
fe80::/64 dev eth0  proto kernel  metric 256  mtu 1500 advmss 1440 hoplimit 4294967295
unreachable default dev lo  table unspec  proto kernel  metric -1  error -101 hoplimit 255
local ::1 via :: dev lo  table local  proto none  metric 0  mtu 16436 advmss 16376 hoplimit 4294967295
local fe80::16da:e9ff:fe15:4492 via :: dev lo  table local  proto none  metric 0  mtu 16436 advmss 16376 hoplimit 4294967295
ff00::/8 dev eth0  table local  metric 256  mtu 1500 advmss 1440 hoplimit 4294967295
unreachable default dev lo  table unspec  proto kernel  metric -1  error -101 hoplimit 255

```

$ ip rule

```

0:	from all lookup local 
32766:	from all lookup main 
32767:	from all lookup default 

```

$ iwconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.

```

$ hwinfo --short

```

cpu:                                                            
                       AMD A8-3850 APU with Radeon(tm) HD Graphics, 800 MHz
                       AMD A8-3850 APU with Radeon(tm) HD Graphics, 800 MHz
                       AMD A8-3850 APU with Radeon(tm) HD Graphics, 800 MHz
                       AMD A8-3850 APU with Radeon(tm) HD Graphics, 800 MHz
keyboard:
  /dev/input/event3    KYE SlimStar 335
mouse:
  /dev/input/mice      Razer Abyssus
  /dev/input/mice      Macintosh mouse button emulation
graphics card:
                       ATI VGA compatible controller
sound:
                       AMD Audio device
                       ATI Audio device
storage:
                       AMD SATA controller
                       AMD IDE interface
network:
  eth0                 Realtek RTL8111/8168B PCI Express Gigabit Ethernet controller
network interface:
  lo                   Loopback network interface
  eth0                 Ethernet network interface
disk:
  /dev/sda             SAMSUNG HD103SJ
partition:
  /dev/sda1            Partition
  /dev/sda2            Partition
  /dev/sda3            Partition
  /dev/sda5            Partition
  /dev/sda6            Partition
  /dev/sda7            Partition
cdrom:
  /dev/sr0             LITE-ON DVDRW LH-20A1S
usb controller:
                       AMD USB Controller
                       AMD USB Controller
                       AMD USB Controller
                       AMD USB Controller
                       AMD USB Controller
                       AMD USB Controller
                       AMD USB Controller
bios:
                       BIOS
bridge:
                       AMD Host bridge
                       AMD PCI bridge
                       AMD ISA bridge
                       AMD PCI bridge
                       AMD PCI bridge
                       AMD PCI bridge
                       AMD Host bridge
                       AMD Host bridge
                       AMD Host bridge
                       AMD Host bridge
                       AMD Host bridge
                       AMD Host bridge
                       AMD Host bridge
                       AMD Host bridge
hub:
                       Linux 2.6.32-38-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.32-38-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.32-38-generic ohci_hcd OHCI Host Controller
                       Linux 2.6.32-38-generic ohci_hcd OHCI Host Controller
                       Linux 2.6.32-38-generic ohci_hcd OHCI Host Controller
                       Linux 2.6.32-38-generic xhci_hcd xHCI Host Controller
                       Linux 2.6.32-38-generic xhci_hcd xHCI Host Controller
memory:
                       Main Memory
unknown:
                       FPU
                       DMA controller
                       PIC
                       Timer
                       Keyboard controller
                       AMD SMBus
                       Serial controller
  /dev/input/event4    KYE SlimStar 335

```

Well thats all I can think of, this is a very weird problem I know, but please if you read it and don't know how to fix it, maybe you have an idea of who could help me. I really don't want be working on windows, or reinstalling again.

---

### Post by chili555 on 2012-02-28
Is the driver you are using r8169?```
lsmod | grep r816
```If so, please see here: [http://ubuntuforums.org/showthread.php?t=1834774](http://ubuntuforums.org/showthread.php?t=1834774) And here: [http://ubuntuforums.org/showthread.php?t=1022411&highlight=8168](http://ubuntuforums.org/showthread.php?t=1022411&highlight=8168)

Note well:> Just make sure that you have the kernel sources, make and gcc installedYou can do so with:```
sudo apt-get install linux-headers-generic build-essential
```

---

