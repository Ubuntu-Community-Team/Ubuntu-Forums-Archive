---
title: "I have no wirless after update to 11.04 please help"
date: 2011-04-29
forum: Networking &amp; Wireless
---

### Post by Funbob235 on 2011-04-29
Ok, I'm green behind the ears and dont know much about the whole computer thing, but what I do know is that I did the whole update and no I have no wireless at all. I had to hook a cable straight to my lab top to get on the Internet.

I am running a Dell Inspiron E1705.

I did the update from the update manager screen that pops up when updates are avaible. CAN SOMEONE HELP, but put it in simple words because again I'm still new to the using Linux. Thanks:)

Bobby-

---

### Post by TBABill on 2011-04-29
Plug into ethernet, click the upper left global icon, search for additional drivers in the search box, click it and then enable the proper driver for your device. 

This assumes you need a proprietary driver and since it's a Dell it is very likely a Broadcom device. If you paste back here the output from typing ```
lspci
``` into a terminal we can know for sure what you need.

---

### Post by Funbob235 on 2011-04-29
I did the lspci:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

---

### Post by TBABill on 2011-04-29
Did you plug into ethernet and follow the prompts via "additional drivers"? If so, what was the result?

---

### Post by TBABill on 2011-04-29
Heading to bed. If you need additional help, see [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by MrD_scifi on 2011-04-30
I have a Dell Inspiron 1520 with exactly the same wifi card in it (BCM4401-B0) and have no wifi at all with 11.04 either.

I have tried all the fixes that are listed in plethora for 43xx wifi cards but no joy.  I'm not an absolute novice here so believe I've followed all the fixes correctly.

When I go for additional drivers I am faced with STA only, no B43.  I try to manually install B43 but still have no option for them in additional drivers.

---

### Post by TBABill on 2011-04-30
The BCM4401 is an ethernet card, not wireless. Did you run lspci in a terminal to find out which wireless device you have? If you know what it is, post back your info from /etc/modules and /etc/modprobe.d/blacklist.conf and we can take a look at which drivers are in use, firmware installed, etc. 

If you do have a BCM4311, the STA driver should work fine for it. No need for the b43 and you cannot have both. They conflict. It's one or the other. B43 doesn't work for all cards that the STA works for so you have to know which you need (or want in the cases where both can work).

---

### Post by MrD_scifi on 2011-04-30
> **TBABill said:**
> The BCM4401 is an ethernet card, not wireless. Did you run lspci in a terminal to find out which wireless device you have? If you know what it is, post back your info from /etc/modules and /etc/modprobe.d/blacklist.conf and we can take a look at which drivers are in use, firmware installed, etc. 

If you do have a BCM4311, the STA driver should work fine for it. No need for the b43 and you cannot have both. They conflict. It's one or the other. B43 doesn't work for all cards that the STA works for so you have to know which you need (or want in the cases where both can work).

oops, I was using Ailurus to tell me and I thought that was the wifi card.  Lspci comes up with the same model wifi card as the thread starter

> Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

and I tried everything and couldn't get it to work.  If this is going to be some mega advanced fixing job, then you've lost virtually every laptop owner with this wifi card, because as Unity is designed for beginners, fixing this sort of thing isn't.  Why is there a change from 10.10 to 11.04 that stops this wifi card working?  B43 and STA both work in 10.10 on my card.

---

### Post by Funbob235 on 2011-04-30
> **TBABill said:**
> Did you plug into ethernet and follow the prompts via "additional drivers"? If so, what was the result?



This is what it says:
This package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-basedhardware.

---

### Post by Funbob235 on 2011-04-30
Who do I need to talk to , to fix this?? Like really come on I should have never updated this darn thing if I knew this was going to happen... again I'll post this.. I'm not very Linux / computer smart... I know how to get around, but this is starting to P me off.. really?   ANYONE HELP AND OR PUT THIS IS NON COMPUTER / EASY TERMS??!!!  PLEASE HELP

---

### Post by MrD_scifi on 2011-04-30
here's a fix I have successfully tried:

0n the main ubuntu site, download version 10.10 of the operating system, or go grab Mint 10 instead (very user friendly flavour of Ubuntu), install over what you just installed and get on with computing until the powers that be fix this glaring regression error which has hit so many people. (this forum is full of frustrated people right now)

If you chose to have 3 partitions, "/"  "/home" and "swap" then reselect the first two partitions for use as ext4, select to format only the "/" partition (to protect your user data and settings in "/home")

Keep watching these forums and certain blogs (like OMGubuntu and UbuntuHQ) for when they fix this, then have another go at installing 11.04.  Could you imagine if windoze users had no wifi when they installed that OS?

---

### Post by TBABill on 2011-04-30
Strange your BCM4311 isn't working with the exact same driver my BCM4312 works perfectly with. All I did was activate it in the live session before installing Ubuntu 11.04 by going to additional drivers, activating it, then INSTEAD OF RESTARTING just ```
sudo modprobe wl
``` and it should pick up networks. You never even have to plug into ethernet. Firmware and driver are on the LiveCD.

Maybe that's the difference? I got it working from the live session so it automatically set it up identically during install. Is that an option to try? Select the STA, let it install the driver and right when it says to restart, instead do the modprobe and connect to your router, then install Ubuntu.

---

### Post by MrD_scifi on 2011-05-01
I'll give that a try when I'm back in tonight.  

So, boot from live, select STA, use that command before restart, check wifi works and immediately install 11.04?

---

### Post by MrD_scifi on 2011-05-01
Okay, booted into live and chose to install STA.  When installed I had a popup saying wifi was on, all looked normal, but when I clicked the icon in topright in the taskbar there was no evidence of wifi working.  When I used that "sudo modprobe wl" command in terminal, nothing happened.

I am now removing STA and going to attempt to install B43 (cutter?) again to give this one more shot.

EDIT: went in sympatic, searched on "broadcom" installed both entries, closed synaptic, went to additional drivers and still no B43 available.  STA does not work for me.  Interestingly, STA is saying it is installed now, but I didn't install it.  Went back in synaptic after removing STA and now find that one of the two entries, "bcmwl-kernel-source" is now removed.  was that STA?   "b43-fcutter" still showing installed

---

### Post by TBABill on 2011-05-01
Yes, bcmwl is the proprietary STA driver. b43 is open source.

---

### Post by MrD_scifi on 2011-05-07
Okay, I copied every fix there was into a file I saved in my /home folder and then reinstalled 11.04 and this sorted me out.

1) attach ethernet lead
2) in "additional drivers", turn off STA driver that was auto installed after vanilla 11.04 install
3) in synaptic package manager, remove bcmwl-kernel-source, every b43/broadcom entry, finding them by using the "search" button on those two terms and not the "quick filter"
4) restart computer
5) open terminal,"sudo apt-get install bcmwl-kernel-source"
6) restart computer and enjoy your wifi finally.

what a mess about!   hopefully canonical respin the image they are using to sort this mess for anyone downloading the image from herein.

---

### Post by inearlygaveup on 2011-05-07
I also cannot directly connect to my wifi unless -

I have to either connect first with my Ethernet cable and wait for my wireless connection to connect, only a few seconds. 
Then I can unplug the Ethernet and move the laptop to any room as normal. 
The system will also pick up my wireless connection without the cable connection as long as I am very close (about a meter) to my router.

***Strange how I can move away once connected with no problem but I can't connect unless I am stood next to the router.***

_**I will reinstall 10.10 if its not fixed next week.**_
I am on an Acer Aspire 5102WLMi with AR2413.

---

