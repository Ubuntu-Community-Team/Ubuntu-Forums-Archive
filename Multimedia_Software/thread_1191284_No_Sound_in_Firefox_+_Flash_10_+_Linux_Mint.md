---
title: "No Sound in Firefox + Flash 10 + Linux Mint"
date: 2009-06-18
forum: Multimedia Software
---

### Post by Keith Fox on 2009-06-18
I'm not sure why, but I thought this OS was fine out of the box.  Turns out my flash 10 sound doesn't work.  I'm new to Linux, and not sure if the kernel version matters, but I don't know how to get the kernel version.  I have tried some commands with Root Terminal, don't know the commands off the top of my head right now, but those commands returned errors saying something like, parameters not defined.. something like that.  Any other sound seems to work.  Also I do not understand the difference between the standard desktop and Gnome?  I don't know but I am using Knome.  Any other sounds seem to work, like Linux sounds, and Rhythmbox Music Player.  What is weird though is my sounds stop working when returning from idle/hibernate mode, and I have to re-login to fix the sound again.  What's up with this sweet OS, that seems rough around the edges.  I thought this was supposed to be way better than Microsoft OS's?  Seems complicating in some areas like sound issues and Aircrack, I have still yet to understand that.

---

### Post by Therion on 2009-06-18
Let me see if I understand things correctly here.  

1.  You're not getting sound along with flash.  So you go to, for instance [www.albinoblacksheep.com](www.albinoblacksheep.com) and you can SEE the videos play, but you can't hear them, is that correct?  Assuming so...

Could you please tell me 

A. How did you install Flashplayer and 

B. Could you please paste the output of this command from the Terminal:```
lspci
```


2.  You are unclear about the different desktop environments, or DE's as they're called.  Those being KDE and Gnome (there is Knome that I am aware of) and the "standard" desktop is the DE that came with your install whether it be KDE or Gnome.  There ARE other DE's (like Xfce and Fluxbox) but KDE and Gnome are the two "biggies".  

You can research the differences by looking here 

All about the Gnome DE: [http://library.gnome.org/misc/release-notes/2.26/](http://library.gnome.org/misc/release-notes/2.26/) 

And here - all about KDE:  [http://www.kde.org/screenshots/](http://www.kde.org/screenshots/)

---

### Post by Keith Fox on 2009-06-19
> **Therion said:**
> Let me see if I understand things correctly here.  

1.  You're not getting sound along with flash.  So you go to, for instance [www.albinoblacksheep.com]("http://www.albinoblacksheep.com") and you can SEE the videos play, but you can't hear them, is that correct?  Assuming so...

Could you please tell me 

A. How did you install Flashplayer and 

B. Could you please paste the output of this command from the Terminal:```
lspci
```
2.  You are unclear about the different desktop environments, or DE's as they're called.  Those being KDE and Gnome (there is Knome that I am aware of) and the "standard" desktop is the DE that came with your install whether it be KDE or Gnome.  There ARE other DE's (like Xfce and Fluxbox) but KDE and Gnome are the two "biggies".  

You can research the differences by looking here 

All about the Gnome DE: [http://library.gnome.org/misc/release-notes/2.26/](http://library.gnome.org/misc/release-notes/2.26/) 

And here - all about KDE:  [http://www.kde.org/screenshots/](http://www.kde.org/screenshots/)

1.Yes I was able to see the video from albinoblacksheep.com, but not the sound.
A: Flash came out of the box with Linux Mint (Gloria).
B:  I will paste the contents of this command below. (lscpi)

2.  Thank you for the DE information.  The standard with Mint, I believe was KDE and I changed in the control panel over to Gnome. (with the foot).  I wasn't sure what they were so I was just playing around with the controls to see if I noticed any differences visually.  Thanks for those links.



00:00.0 Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:06.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port C)
00:07.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port D)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:00.0 SATA controller: JMicron Technologies, Inc. JMB361 AHCI/IDE (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMB361 AHCI/IDE (rev 02)
04:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
04:06.0 Modem: Smart Link Ltd. SmartPCI2800 V.92 PCI Soft DFT (rev 02)

---

### Post by sonnyxleet on 2009-09-18
hey, all i'm really new to linux, and mint was recommended to me about 4 months ago. since i've been using it, i've only had this problem once. and it was about a month or so after i being using mint. so, i searched and searched, didn't find anything to fix it. so i tried my own solution, and it worked. i haven't had this problem since. not sure if it'll work for everyone else, though. 

in terminal run:

```
sudo apt purge flash*
```then run:

```
sudo apt-get update && sudo apt-get upgrade
```then finally run:

```
sudo apt-get install adobe-flashplugin
```again, i'm EXTREMELY new to linux, so not sure if this will work. hopefully it does.

---

