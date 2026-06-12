---
title: "Recommend Nvidia  GDDR5 video card"
date: 2012-06-30
forum: Multimedia Software
---

### Post by hannuh on 2012-06-30
Could somebody confirm if this video card is going to get detected and work with 12.04 64-bit: 

EVGA GeForce GTX 560 Ti FPB 1024MB GDDR5 (01G-P3-1561-KR)

I have already two high end video cards that don't work with Ubuntu and don't want to buy a third one.
If you have recommendations for a Nvidia based GDDR5 video card, I'd like to hear about it.
Thank you for your help,
Hannu

---

### Post by 3Miro on 2012-06-30
Which video cards don't work? Nvidia has great support for their video cards for Ubuntu, you should hardly ever see an Nvidia not working. AMD has improved a lot too. I am surprised there are any video cards that don't work under Desktop Linux.

---

### Post by hannuh on 2012-06-30
> **3Miro said:**
> Which video cards don't work? Nvidia has great support for their video cards for Ubuntu, you should hardly ever see an Nvidia not working. AMD has improved a lot too. I am surprised there are any video cards that don't work under Desktop Linux.

These two do not work:

PNY VCQ2000-PB Quadro 2000 1024MB GDDR5, PCI Express 2.0 x16, Dual Display Port, DVI
- cannot even get to the installation prompt. blinking cursor.

ATI Radeon HD 5770 GDDR5 PCI Express
- allows installation, but won't work 3D acceleration no matter what you try, including the driver from ATI

Hannu

---

### Post by hannuh on 2012-07-01
I figured out my problem with video cards.
It turns out that the problem is the monitor I am using for this computer.
The Ubuntu installer will not run in a Samsumg SyncMaster P770 27 inch monitor. When I switch the monitor to a 24 inch SyncMaster SA350 (24 inc) the installer will run. However, once the installation is complete, including the nvidia driver installed, I can switch to the 27 inch and Ubuntu will run just fine.
The splash screen will run in a reduced size, but once the login screen comes up, Ubuntu begins to use full screen.
Both monitors have native resolution of 1920x1080, but the problem seems to be physical dimensions of the screen. 
I don't know if this is the case with all 27 inch monitors, or just the Samsung SyncMaster P770.
So, the workaround is:
- install Ubuntu with a monitor with a smaller monitor, but same resolution
- once nvidia drivers have been installed, you can switch to the 27 inch.
Hannu

---

### Post by 3Miro on 2012-07-01
This is odd indeed, I have never seen a monitor dependent behavior like this. Glad you resolved the problem, if you have no more questions, you can mark this thread as "Solved".

---

### Post by efflandt on 2012-07-02
For 64-bit 12.04 with GTX 550 Ti on HDTV, I had to use **nomodeset** kernel boot parameter during install iso booted from USB.  Without that, after purple screen with symbols at bottom I got blinking cursor forever (past drum roll).  After install, no boot parameters needed.

Maybe that would have helped hannuh.

---

