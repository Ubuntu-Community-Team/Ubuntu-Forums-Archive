---
title: "Broadcom  BCM4306"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by radioactiveman69 on 2008-12-14
Gents,

This is my first time using linux (Groan I know!) but I am having trouble with my wireless card.

Here is my information:

ryan@ubuntu:~$ sudo lshw -c network 
[sudo] password for ryan:  
  *-network:0              
       description: Network controller 
       product: BCM4306 802.11b/g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 2 
       bus info: pci@0000:02:02.0 
       version: 03 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master 
       configuration: driver=b43-pci-bridge latency=64 module=ssb 
  *-network:1 
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 3 
       bus info: pci@0000:02:03.0 
       logical name: eth0 
       version: 10 
       serial: 00:0f:b0:01:b8:6b 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s 
  *-network:0 DISABLED 
       description: Wireless interface 
       physical id: 2 
       logical name: wlan0 
       serial: 00:90:4b:58:70:f1 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg 
  *-network:1 DISABLED 
       description: Ethernet interface 
       physical id: 3 
       logical name: pan0 
       serial: 26:18:b3:f0:9c:86 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 



Could anyone give me some help and as I said I am really new

Cheers

Ryan

---

### Post by ieee488 on 2008-12-14
you need to use ndiswrapper and XP drivers
I just went through this yesterday with my laptop.

---

### Post by radioactiveman69 on 2008-12-14
awesome! I am going to need some help with that.. any thoughts?

---

### Post by ieee488 on 2008-12-14
I don't have the URL bookmarked, but Google on **ubuntu ndiswrapper**.

---

### Post by Enriquecaribe on 2008-12-14
Lol I use a HP laptop with Broadcom wireless drivers. I used this website for help. I'll see if I can find the thread that helped... give me some time to search...

Okay I'm back with this: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

But please read carefully, I made the mistake of skimming through it the first time quickly and messed up somewhere along the way. READ THE FILES WORD FOR WORD!!

---

### Post by Ayuthia on 2008-12-14
Before you try it, please see if you can use the open source version first!

If you have a working internet connection, please try going to System->Administration->Hardware Drivers and activating the Broadcom driver.  It might ask you if you want it to fetch the firmware for you.  Say yes.  Once it is done, it will ask you to reboot and it should be ready.

EDIT:
Here are instructions if you don't have a working internet connection:
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

---

### Post by radioactiveman69 on 2008-12-14
that worked!! as simple as plugging in my lan cable and updating.

Thanks so much!

---

