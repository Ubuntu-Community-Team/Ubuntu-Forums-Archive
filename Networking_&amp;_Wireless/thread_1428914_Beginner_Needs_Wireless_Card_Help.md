---
title: "Beginner Needs Wireless Card Help"
date: 2010-03-13
forum: Networking &amp; Wireless
---

### Post by Robin3531 on 2010-03-13
[SIZE=3]Hi all,

I'm new to Linux and have recently installed Ubuntu (Hardy Heron) on an old PC that I used to run Win XP.

[/SIZE]   [SIZE=3]I have a wireless card already installed (which works with windows) and is Broadcomm based (BCM4318 AirForce One 54g).

I've followed troubleshooter advice and having entered 'sudo lshw -C network' in Terminal, I get the following   [/SIZE] 
[FONT=Courier New][SIZE=3]
    *-network               
         description: Network controller 
         product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller 
         vendor: Broadcom Corporation 
         physical id: 3 
         bus info: pci@0000:01:03.0 
         version: 02 
         width: 32 bits 
         clock: 33MHz 
         capabilities: bus_master 
         configuration: driver=b43-pci-bridge latency=64 module=ssb 
    *-network DISABLED 
         description: Wireless interface 
         physical id: 1 
         logical name: wlan0 
         serial: 00:14:a4:69:d3:08 
         capabilities: ethernet physical wireless 
         configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g [/SIZE][/FONT]

[FONT=Verdana][SIZE=3]Can anyone point me in the right direction.  Is this a driver issue, or something else?[/SIZE][/FONT][SIZE=3]
[/SIZE] [FONT=Verdana][SIZE=3]
[/SIZE][/FONT][SIZE=3]
[/SIZE] [FONT=Verdana][SIZE=3]Thanks,

Robin[/SIZE][/FONT][SIZE=1]
[/SIZE]

---

### Post by soropi on 2010-03-13
> [FONT=Courier New][SIZE=3]*-network DISABLED 
         description: Wireless interface[/SIZE][/FONT]Is your wireless on?

---

### Post by Robin3531 on 2010-03-16
I think so.  When I go into Network Settings it shows 'Wireless connection Roaming mode enabled', although there is a - sign in the box to the left, is this relevant?

Thanks,

Robin

---

