---
title: "Wireless disappeared ubuntu 9.04 64 bit Athros"
date: 2009-09-21
forum: Networking &amp; Wireless
---

### Post by prylux on 2009-09-21
Installed fresh version 9.04 from live CD. Wireless network was working. Then it disappeared and came back during a session. Now I can not find it.
I have been looking on google and the forums but have not found a solution. I used to use a wrapper when I was using 8.10 but was happy not to have to use it anymore.

When I try to run RutilT I get this message

[INDENT]"Critical error :
Can't find any wireless network interface.
Code : -3"[/INDENT]

After it stopped working I tried to use the madwifi driver that was in
*System--> Administration--> Hardware Drivers*
That didn't help

I then deactivated it and it still has not worked.

Wicd (I just installed it to see if it would help as I was using "Network Manager") doesn't show any wifi at all

I pushed the wifi button on the laptop to see if it was off. It seems to have no effect.

This happened after I upgraded from 8.10LTS so I thought it was from the upgrade, thus the fresh install. I really do not want to reinstall nor do I wish to use a wrapper.

Please help...[-o<

This is a Presario C700 laptop

Here is some info
[INDENT]
user@Ubuntu-laptop:~$ lshw -C network

WARNING: you should run this program as super-user.
*_**  *-network UNCLAIMED     **_*
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1b:38:f3:27:14
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.189 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 16:98:58:25:a3:44
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes[/INDENT]

[INDENT]user@Ubuntu-laptop:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1b:38:f3:27:14  
          inet addr:192.168.0.189  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fef3:2714/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1679 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2208928 (2.2 MB)  TX bytes:290075 (290.0 KB)
          Interrupt:16 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)
[/INDENT]

[INDENT]user@Ubuntu-laptop:~$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

pan0      no wireless extensions.[/INDENT]

---

