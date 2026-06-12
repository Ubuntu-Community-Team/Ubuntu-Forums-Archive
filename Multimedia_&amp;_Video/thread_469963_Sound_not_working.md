---
title: "Sound not working"
date: 2007-06-10
forum: Multimedia &amp; Video
---

### Post by HgBoy on 2007-06-10
Fresh install of edgy, no sound output through speakers or headphones. 

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:05.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
01:06.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
01:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

sound priveleges and all channels unmuted. I dont know what to check next.

---

### Post by Chappy7777 on 2007-06-10
Hi, I had the same problem last week, tho I am using Dapper 6.06 I installed the Gnome Device Manager using the Add/Remove program. It was ez enuf to do. There is already a Device Manager under Systems/Preferences. Look at it and see if your card is listed. When I installed that Gnome Device Manager, it showed my sound card. I clicked on a few boxes and had sound. Prior to that I had had the same as you, no sound. 
When you post a question like this you'll get more replies if you add some info. Sound card make? Etc.

---

### Post by HgBoy on 2007-06-10
the soundcard is an Intel Corp. 82801DB AC'97 Audio Controller. Apparently this works with  the ALSA module, called snd_intel8x0 module. How would I go about installing this?

---

### Post by Chappy7777 on 2007-06-10
Did you open up your Device Manager to see if Ubuntu is seeing the card? Is this an onboard card?

---

### Post by HgBoy on 2007-06-10
Yes, and yes. The card shows up, the drivers all seem to be installed. It just doesn't want to work. I have heard some of the intel cards just not working for no apparent reason, so I'm stumped.

---

### Post by burntcompletely on 2007-06-30
I had the similar issue. I have two sound cards one integrated with my motherboard. Try this 

go the bios and disable the integrated audio

reboot to ubuntu

see if the sound works(with the other audio card)

this sets the default(sound cards) in your ubuntu system properly

you should now be able to enable the integrated audio and through ubuntu configure the sound to any audio cards

---

