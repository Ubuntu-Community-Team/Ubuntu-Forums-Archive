---
title: "Trying to install webcam"
date: 2009-01-21
forum: Multimedia Software
---

### Post by Crazy K on 2009-01-21
I recently purchased a webcam from dealextreme.com for like $6. Anyways, there's no name on the cam, or the installation cd that it came with. The CD has a panda on it. That's all I can really get from it. When I put the webcam in, I can control the lighting on the camera itself (comes with a switch to do that) and it obviously gets power. I tried installing the gspca driver for it, but that also hasn't worked out for me. I checked the reviews of the product on Dealextreme, and it said that gspca is a supported driver.

Anyways I have no idea of how to install this webcam.

I also tried camorama and cheese, but neither recieved video. I also tried installing the installation disk through wine, but that too didn't work.

---

### Post by Crazy K on 2009-01-22
Also, the file that is on the CD is this: cam1210_1542_0528.exe

---

### Post by Crazy K on 2009-01-23
I also I don't know if I need to install Amcap.exe. It's not on the disc that is provided with the webcam.

This is the link to the webcam. It doesn't say what brand it is or anything. [http://www.dealextreme.com/details.dx/sku.13](http://www.dealextreme.com/details.dx/sku.13)

I just noticed that this webcam has a MICRODIA chip set, so idk if that helps out. I read it under one of the reviews.

Also, this might help out. It's another topic on the Ubuntu forums about the same cam. [http://ubuntuforums.org/showthread.php?t=375005](http://ubuntuforums.org/showthread.php?t=375005)

also if this helps, this is what I got under the terminal after typing in lsusb: 

> Bus 004 Device 009: ID 17a1:0118  
Bus 004 Device 006: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 004 Device 002: ID 05e3:0606 Genesys Logic, Inc. D-Link DUB-H4 USB 2.0 Hub
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 043d:0069 Lexmark International, Inc. X74/X75 Printer
Bus 002 Device 004: ID 043d:0060 Lexmark International, Inc. X74/X75 Scanner
Bus 002 Device 003: ID 04b3:310c IBM Corp. 
Bus 002 Device 002: ID 043d:0061 Lexmark International, Inc. X74 Hub
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 04f3:0103 Elan Microelectronics Corp. 
Bus 001 Device 001: ID 0000:0000 

---

### Post by Crazy K on 2009-03-14
So I take it no one's going to reply with any help?

---

### Post by edwinv on 2009-05-14
> **Crazy K said:**
> I also I don't know if I need to install Amcap.exe. It's not on the disc that is provided with the webcam.

This is the link to the webcam. It doesn't say what brand it is or anything. [http://www.dealextreme.com/details.dx/sku.13](http://www.dealextreme.com/details.dx/sku.13)

I just noticed that this webcam has a MICRODIA chip set, so idk if that helps out. I read it under one of the reviews.

Also, this might help out. It's another topic on the Ubuntu forums about the same cam. [http://ubuntuforums.org/showthread.php?t=375005](http://ubuntuforums.org/showthread.php?t=375005)

also if this helps, this is what I got under the terminal after typing in lsusb:


how did you get your lexmark x74 to work

i am trying to get it to work in ubuntu jaunty withour any success 

can you please explain step by step how to get it to work please

---

### Post by Crazy K on 2009-05-29
Sorry dude, but I was unable to get it to work myself. I don't even know why it showed up. I know i had it connected, but I was never able to get it to print. 

Also, is anyone going to help me out with my cam problems?

---

### Post by Arup on 2009-05-29
No drivers are needed in Linux, either its via modules or pre-compiled as in case of Jaunty so all you do is plugin to see if it works, if it doesn't, post the lspci

In case of Hardy Heron you might have to remove the camera driver module to let gspca load and not conflict.

My unknown cheap cam works like a charm in Ubuntu whereas in Windows there were no reliable drivers to make it work. The one that was provided didn't work for x64 and a beta one conked out leading me to believe that the cam had died till I plugged it into Ubuntu.

---

### Post by Crazy K on 2009-05-31
Here's the lspci:

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:0b.0 Communication controller: Agere Systems LT WinModem (rev 02)
01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by Crazy K on 2009-06-03
I'd also like to point out, that this camera here: [http://ubuntuforums.org/showthread.php?t=375005](http://ubuntuforums.org/showthread.php?t=375005) is basically the same as mine. So can anyone help me out? Because I went through that topic, and I couldn't figure anything out.

btw, just did an 'lsusb' and this has to be my cam: 

```
Bus 004 Device 010: ID 17a1:0118 
```

---

### Post by rob2uk on 2009-06-03
[http://ubuntuforums.org/showthread.php?t=586593]("http://ubuntuforums.org/showthread.php?t=586593") has a guy with the same problem as you...

In fact, [Googling 17a1:0118 Ubuntu]("http://www.google.co.uk/search?q=17a1%3A0118+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-GB:unofficial&client=firefox-a") comes up with a LOT of people having the same problems as you...

I had a [b]very[/] quick look through the results and there doesn't seem to be a solution, might be worth setting some time aside and trawling through them properly though :)

---

