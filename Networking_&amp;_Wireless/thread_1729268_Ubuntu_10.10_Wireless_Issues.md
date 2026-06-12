---
title: "Ubuntu 10.10 Wireless Issues"
date: 2011-04-14
forum: Networking &amp; Wireless
---

### Post by staind94 on 2011-04-14
Hi everyone, I am having two issues with Ubuntu 10.10. 

First issue:  I am able to connect to the Internet via ethernet cable, but not wirelessly.  I have tried everything I could think of(inexpirenced with Ubuntu).  

Second issue: In the network manager, I am not able to pick up any wireless signal what-so-ever.  It actually does not show an option to connect to a wireless signal.

My laptop model is: Compaq Presario V5306US and the wireless card is a Broadcom 4318. Other system specs are as follows: 2GB RAM, Single-Core CPU @ 1.8GHz, and 250GB Hard Drive.

I am also very willing to help with information as much as I can give.

---

### Post by Draven844 on 2011-04-14
Doesn't connect for you either? Try logging on with a second guest profile, or, if you know what you're connecting to, do it manually by entering the target, and whatever passwords that may be needed. See if this works.

---

### Post by staind94 on 2011-04-14
> **Draven844 said:**
> Doesn't connect for you either? Try logging on with a second guest profile, or, if you know what you're connecting to, do it manually by entering the target, and whatever passwords that may be needed. See if this works.

I tried logging in as guest and it is the same on that profile.

---

### Post by josephmills on 2011-04-14
Hi there Could you please press ctrl+alt+t a box will come up please type ```
lspci -vnn | grep 14e4
``` in the box. then press enter then copy what you get then paste it here. thanks

---

### Post by NFblaze on 2011-04-14
Have you tried System > Administration > Hardware Drivers first?

That may allow you to automatically install your drivers.

---

### Post by staind94 on 2011-04-14
> **josephmills said:**
> Hi there Could you please press ctrl+alt+t a box will come up please type ```
lspci -vnn | grep 14e4
``` in the box. then press enter then copy what you get then paste it here. thanks

It gives me this: 06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

---

### Post by staind94 on 2011-04-14
> **NFblaze said:**
> Have you tried System > Administration > Hardware Drivers first?

That may allow you to automatically install your drivers.

I have but the only driver that comes up is Software Modem.  There was(I think) a Broadcom driver that would show up.. but now it is no where to be found.

---

### Post by NFblaze on 2011-04-14
Hey run

```
lshw -C network
```

We want to make sure that you network status?

Also, do you run Windows on this? Sometimes the wifi cards come with a software switch that if used in Windows will disable the wifi card from working in Windows until re-enabled in Windows

---

### Post by staind94 on 2011-04-14
> **NFblaze said:**
> Hey run

```
lshw -C network
```

We want to make sure that you network status?

Also, do you run Windows on this? Sometimes the wifi cards come with a software switch that if used in Windows will disable the wifi card from working in Windows until re-enabled in Windows

This is what was listed in Terminal: 
*-network:0             
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       logical name: wlan0
       version: 02
       serial: 00:14:a5:a9:a9:b2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.56+Broadcom,12/17/2005, 4.10.4 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: irq:21 memory:c0200000-c0201fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:41:d8:62
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.67 latency=128 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:22 ioport:a000(size=256) memory:c0202000-c02020ff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

Also, I don't have a Windows partition or anything relating to it.  But when I did fight this battle a while back I did and something else got in the way(just can't remember what though).

Edit: I got a little further ahead now. I installed Ndisgtk and got the Windows driver for the Wireless card.  Also at the moment.. I think the wireless just connected.. let me test it out.

Edit 2: Its working! :) Thank you everyone for all of your support!

---

### Post by josephmills on 2011-04-14
take a look at this [https://www.youtube.com/watch?v=hAHN-YnmrLw](https://www.youtube.com/watch?v=hAHN-YnmrLw)

---

