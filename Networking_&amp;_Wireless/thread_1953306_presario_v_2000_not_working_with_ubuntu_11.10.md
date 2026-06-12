---
title: "presario v 2000 not working with ubuntu 11.10"
date: 2012-04-06
forum: Networking &amp; Wireless
---

### Post by chomie on 2012-04-06
Hello

I'm an absolute beginner to Ubuntu. After initially installing Ubuntu, my computer worked perfectly and had no glitches with the wifi which lasted 1 week. Then my wifi had problems. Both my lan and wifi are not working when I'm using Ubuntu. I tried booting thru my windows and my wifi works perfectly.

I tried reading some threads but couldn't figure out which one to follow. I assume this is what you guys need to be able to help me. 

chomie@ubuntu:~$ sudo lshw -class network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:ab:96:8c
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:16 ioport:3000(size=256) memory:b0106000-b01060ff
  *-network:1 DISABLED
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:a4:d5:b2
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:b0107000-b0107fff
chomie@ubuntu:~$ sudo rfkill list all
0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes

Thanks

---

### Post by praseodym on 2012-04-06
Hi,

any button/switch/key/key combination? Tried to reset the BIOS?

---

### Post by owise1 on 2012-04-06
did you right click the wireless icon to see if wired and wireless are enabled?

---

### Post by chomie on 2012-04-06
Hi praseodym,

There is a wifi button, doesn't light up when I use Ubuntu but its ok when i use windows.

Don't know how to reset my bios

thanks

---

### Post by chomie on 2012-04-06
Hi owise1,

wifi is enabled same in your picture. but no signal couldn't even pick up any wireless signals

thanks

---

### Post by praseodym on 2012-04-07
Reboot, and look for whatever button to press to get into the BIOS. Mostly its F9 to reset and F10 to save&exit

---

### Post by chomie on 2012-04-07
Hi [praseodym]("http://ubuntuforums.org/member.php?u=1411497")

Thanks for your help wifi working fine

---

