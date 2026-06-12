---
title: "Need help on how to add a driver to linux."
date: 2010-08-17
forum: Networking &amp; Wireless
---

### Post by Robdog69 on 2010-08-17
My laptop was on windows xp and when I installed ubuntu linux my NIC Card driver was gone (I think) and now I can't connect to the internet using an ethernet.

I have the driver on the desktop of my Linux laptop but I don't know how to add it using terminal or any other options.

Can I have some help please? I'm VERY new to linux. :(

---

### Post by cavalier911 on 2010-08-17
Practically all drivers for ethernet are either compiled into the linux kernel or are included as kernel modules which are loaded on an as needed basis on boot.
To see whether your ethernet hardware is installed: 
Open up the terminal and type ifconfig -a followed by enter,copy/paste the output.
Here is my ethernet:

rj@intrepid:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:1d:23:a1:db  
          inet addr:192.168.123.9  Bcast:192.168.123.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fe23:a1db/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7797162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11040590 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1277018378 (1.2 GB)  TX bytes:2727551074 (2.7 GB)
          Interrupt:252 Base address:0x4000 

If your ethernet adapter is installed it's a network connection problem.

If you see no ethernet type lspci ,unless it's a USB ethernet adapter in which case type lsusb,copy/paste ethernet listing in reply.

Here is mine:
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

---

