---
title: "Alienware M15X Webcam Issues"
date: 2010-02-23
forum: Multimedia Software
---

### Post by Sl3uth on 2010-02-23
Hi, I just joined the forums, and I am a noob to Anything Linux related. I installed Ubuntu on my Alienware M15X Laptop, I had a few issues that I had a friend help me with, but I am stumped on getting my webcam to work. I already tryed two commands in the terminal, lsusb and lspci, and saw no recognition of a webcam, which is intergrated in the laptop.

Here is the lsusb output:

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 187c:0511  
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Any help would be greatly appreciated.

---

### Post by Sl3uth on 2010-02-24
I have it working in Cheese, but anything where it asks for access to the Microphone and Camera just becomes unclickable, but doesnt freeze, i.e stickam and chatroullete. 

I tryed gstreamer-properties in the terminal and tryed fiddling around with it, but no luck. I click test on the V4l2 driver, and get this error message

 "Video for Linux 2 (v4l2): Error getting capabilities for device '/dev/video0': It isn't a v4l2 driver. Check if it is a v4l1 driver."

If i test anything else, its just static with the Tv "Please Standby Image" (Assuming this means nothing detected.)

I also added me Lspci output:

cooper@Cooper-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8700M GT] (rev a1)
05:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 06)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
0a:09.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0a:09.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
0a:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
0a:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
cooper@Cooper-laptop:~$

---

### Post by tstrike on 2010-02-27
I am having the same issues...   After seeing my buddy on his Inspiron with Ubuntu and my numerous customers I decided to test drive Ubuntu on a Live CD with Karmic. It was a unmitigated disaster... I called my buddy and he said, "Dude go with Hardy Heron"  I CANT BELIEVE how GREAT Ubuntu is on this Alienware machine!!! It runs this Alienware machine EFFICENTLY... I am NEVER going back to Windows again as a native OS..  Now I have the issue of the Alienware integrated WebCam which also runs the freaking microphone... (physically colocated with the camera).  The USBID for the camera is 152d:0770 and I have spent exhaustive days and nights trying to pin this down (it is so identified as a JMicron vendor with a Omnivision manufacturer)...  Any one can point us in the right direction?

---

### Post by Sl3uth on 2010-02-28
I tryed the Adobe Flash Global Setting manager on the Adobe site, and that let me always allow access to my mic and cam, for sites I had already visited. This worked for a little on stickam, but for things like mebeam it hasnt. I've run out of ideas and searched for every possible solution with no luck. :/

---

### Post by tstrike on 2010-02-28
> **Sl3uth said:**
> I tryed the Adobe Flash Global Setting manager on the Adobe site, and that let me always allow access to my mic and cam, for sites I had already visited. This worked for a little on stickam, but for things like mebeam it hasnt. I've run out of ideas and searched for every possible solution with no luck. :/

  Skype 2.1 beta on Hardy Heron is broken too...  I was able to test the camera and it works but the damn microphone I havent the slightest clue.

---

### Post by tstrike on 2010-02-28
But you gotta admit, Ubuntu on Alienware M15X runs INCREDIBLY light years faster than Windows of any flavor (yes even Windows 7)  Its insane...! Best thing is its efficient use of resources... Ubuntu is so meticulous... it takes ONLY what it needs... Amazing!

---

### Post by tstrike on 2010-03-13
Update: The camera works, the sound card remains an issue, and you have to buy an external microphone as the integrated Digital one doesnt work with the camera.

With headphones and a microphone set, everything works well.

---

### Post by LiQuidAiR on 2010-06-16
> **tstrike said:**
> Update: The camera works, the sound card remains an issue, and you have to buy an external microphone as the integrated Digital one doesnt work with the camera.

With headphones and a microphone set, everything works well.


How did you get it work?  I'm waiting for my Alienware m15x..I'm sure i'm gonna have to try and put all these fixes in manually also.

Thank you

---

### Post by Thomas B. on 2010-06-17
I just suddenly started having trouble with my webcam. It's not longer working :/ However, I think it might be because I uninstalled something. Can anyone point me in the direction of what package I can download to get it working again?

---

### Post by LiQuidAiR on 2010-06-18
> **Thomas B. said:**
> I just suddenly started having trouble with my webcam. It's not longer working :/ However, I think it might be because I uninstalled something. Can anyone point me in the direction of what package I can download to get it working again?

I'm curious to how you got it working in the first place.  What are your tech specs for your Alienware?  Did the cam and mic "out of the box" after Ubuntu install?

---

### Post by no2498 on 2010-06-18
LiQuidAiR look in sound & video see if cheese webcam booth is installed 
try the cam in cheese first


see if this helps get the cam back up and running

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

---

### Post by LiQuidAiR on 2010-06-18
> **no2498 said:**
> LiQuidAiR look in sound & video see if cheese webcam booth is installed 
try the cam in cheese first


see if this helps get the cam back up and running

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

Thank you.

I haven't received my Alienware, yet.  I just figured I would ask questions since I'm sure I'll have problems.  Thank you.  I'll check on this once my Alienware arrives..

---

### Post by Thomas B. on 2010-06-18
It worked out of the box, but I got it in late 2008. They've most likely made  bunch of updates to it since then. Everything worked great out of the box for me, except for the sound driver which I quickly fixed, and the webcam's microphone. Not a big deal since I have an external one.

---

