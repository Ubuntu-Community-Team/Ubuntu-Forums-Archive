---
title: "Wireless stopped working"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by james_fried on 2009-01-01
Hi all and happy new year!

The wireless on my kubuntu box recently stopped working.

The first I noticed was that the knetwork manager wasn't able to find any wireless networks and couldn't connect when I input my network's details manually. From some further investigation, I tried wicd which couldn't even find a wireless card to set up.

So then I started digging and this is what I've found - I'm very confused as to what to do next... any suggestions?

```
$ lspci
...
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
...

```

```
$ lsmod | grep b43
b43legacy             127776  0
mac80211              165652  1 b43legacy
ssb                    34308  1 b43legacy

```

only the wired connection I'm using to make this post shows up in ifconfig...

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:05:5d:6b:80:15
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::205:5dff:fe6b:8015/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4669 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4083 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5322384 (5.0 MB)  TX bytes:528756 (516.3 KB)
          Interrupt:17 Base address:0x4e00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5100 (4.9 KB)  TX bytes:5100 (4.9 KB)

```

```
$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

eth1      No scan results

```

```
$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:1
       description: Ethernet interface
       product: VT6105 [Rhine-III]
       vendor: VIA Technologies, Inc.
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth0
       version: 86
       serial: 00:05:5d:6b:80:15
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.1.3 latency=32 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:30:bd:95:34:92
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

I'm confused why there are two wireless cards appearing now.

```
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:05:5d:6b:80:15
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::205:5dff:fe6b:8015/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2208 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2258 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2223959 (2.1 MB)  TX bytes:306435 (299.2 KB)
          Interrupt:17 Base address:0x4e00

eth1      Link encap:Ethernet  HWaddr 00:30:bd:95:34:92
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2200 (2.1 KB)  TX bytes:2200 (2.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-30-BD-95-34-92-00-00-00-00-00-00-00-00-00-00
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Why is there eth1 and wmaster? I'm sure I haven't seen that before...?

Any help would be greatly appreciated, I'm really stuck with this one.

J

---

### Post by carml on 2009-01-01
[FONT="Times New Roman"]Have you tried the recovery mode?I mean the one you can see at startup,this way you can correct or exclude the presence of broken packages.[/FONT][SIZE="2"][/SIZE]

---

### Post by james_fried on 2009-02-01
hi carml,

thanks for your post - I've managed to solve the problem and get the linux box back on the internet!

Thanks to you - I tried booting into recovery mode, but was having trouble getting there because my bios / grub doesn't recognise the USB kbd... So while I was at a terminal trying to see how to get it into safe mode the following error popped up :

```
b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed. ... you must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).

```

From there I visited the [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) , installed the fwcutter and everything is working again!

Cheers,

J

---

