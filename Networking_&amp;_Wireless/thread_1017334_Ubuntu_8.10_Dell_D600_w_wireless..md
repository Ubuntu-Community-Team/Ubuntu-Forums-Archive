---
title: "Ubuntu 8.10 Dell D600 w/ wireless."
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by ddecker03 on 2008-12-20
I am new to Ubuntu and trying to get my old laptop up and running.  I run off a usb drive and it boots fine, but it doesnt see any of the wireless I have in there.  I believe its a broadcom 94306mp. (thats what the device says on the back of the laptop.  I also have a linksys wmp54gs v1.  

Sorry but I am used to Windows, I am unsure of how to verify it see's the device's (1), and how to make sure it has the drivers (2).  

Any support would be appreciated.

Dave

---

### Post by Chew N Tobacca on 2008-12-21
I ran into the same problem with a Compaq c552us. If you check the Hardware Drivers (Applications -> system -> hardware drivers), does it show any drivers listed there? If so, then probably you need to first install the firmware for the drivers.

---

### Post by Chew N Tobacca on 2008-12-21
OK so I got to looking around for you, and it seems there are many pieces of hardware that use the same 94306mp chipset (e.g. Dell TrueMobile 1300). Try using the "lspci" command from the terminal and locate your wi-fi adapter. "lspci" will show you all devices and controllers in your computer. That will give you specifics on what you actually have. For more details, "lspci -v" will be more specific and easier to locate. Maybe you could post the section on your adapter?

---

### Post by ddecker03 on 2008-12-21
Thanks for the help, will look at it tonight (have to wait till kids are in bed to do "project" work.  

Dave

---

### Post by dad311 on 2008-12-21
Im using an Dell Latitude D600 everything worked great with no tinkering.

ATI 1400x1050 video resoultion, wireless, etc.  Simply no issues.  Accutally this is best support PC/laptop I have.

Below is my lspci:

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
darrell@darrell-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

---

### Post by gTinker on 2008-12-21
ddecker03,

There must be more than one "model" of Latitude D600. Mine is the same as yours with the Broadcom 4306 chipset. You will have to make sure the firmware is loaded for that chipset. Just a note, mine also has an LCD with 1024 x 768 native resolution.

If you do a forum search with the keywords Broadcom 4306, you will find directions. Lots of people had trouble with this.
[http://ubuntuforums.org/search.php?searchid=53427299](http://ubuntuforums.org/search.php?searchid=53427299)

---

### Post by Ayuthia on 2008-12-21
@dad311-
This looks like your wireless card:
> 02:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

You will want to look around and see if you can find some posts with the Intel 2100.  I am not for sure which driver you need.  If you can't find any info, please create another thread for this card since it is different than the original poster.  It will help you get more help for your card.

---

### Post by ddecker03 on 2008-12-23
I had to download the firmware, and the card is now active, but I cant connect to anything.  

My network is using WEP 128b.  I have tried using iwlist to see available networks (no scan results).  I think I have setup the card right, right now I am using my other machine to write this (xp).

Not sure what to do from here.  If you need anything further please let me know.

---

