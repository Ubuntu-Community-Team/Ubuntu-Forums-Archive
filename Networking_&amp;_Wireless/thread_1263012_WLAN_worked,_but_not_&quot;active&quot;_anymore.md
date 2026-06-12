---
title: "WLAN worked, but not &quot;active&quot; anymore"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by Alexandre Charoy on 2009-09-10
Hello!

I'm new to Ubuntu, and the first thing I did, was installing a Windows driver for my WLAN with ndiswrapper. Everything went fine, and I could use WLAN without any problems. That was few days ago. I didn't notice it first, 'cause I'm using a wired connection most time, but now I can't connect to any Wifi network anymore, Ubuntu acts as I don't have a wlan connection.

When I click on the Network button in the top panel, I only get the options "Wired Network", "Connecto to 802.1X Protected Wired Network", and "Manual" Configuration".

In the Network Settings, under the Connections tab, there are only Wired connection and point to point connection listed.

In System/Administration/Wireless Network Drivers (I think this is part of ndiswrapper gui?) the installed wlan driver is listed, and says "Hardware present: yes." like before.
Output of ndiswrapper -l in the console:
[php]netw5v32 : driver installed
    device (8086:4237) present (alternate driver: iwlagn)[/php]Maybe there's a problem because of this alternate driver?

This is the output when I enter iwconfig in the console:
[php]lo        no wireless extensions.

eth0      no wireless extensions.[/php]Output of lshw -C network in the console:
[php]alex@alex-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:b1:e7:23
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.78 latency=0 module=r8169 multicast=yes[/php]Since the successful installation of the wlan driver, I didn't change anything concerning drivers, wlan, connection or whatever, so I suppose that wlan still works, but is somewhat not activated? Like when you disactivate your wireless connection on Windows?

Thanks for your time and help!
Mfg Alex

---

### Post by Alexandre Charoy on 2009-09-11
Any idea? I really need it, my wired connection is not working right too, and I don't progress, I have many problems, but without a stable internet connection, I will not find solutions... I think I'll go back to Windows, if this continues, nothing works as it should......

---

### Post by Alexandre Charoy on 2009-09-11
I have a new problem... everytime I search for updates (System/Administration/Update Manager), or everytime I try to upgrade my ubuntu distribution (8.04 -> 8.10), internet stops working (wired connection). Everytime I need to disable and then enable again networking, so it reconnects and Internet works fine again .......

---

