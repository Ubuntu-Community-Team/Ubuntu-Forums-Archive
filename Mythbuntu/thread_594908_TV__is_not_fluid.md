---
title: "TV  is not fluid"
date: 2007-10-28
forum: Mythbuntu
---

### Post by spoky99 on 2007-10-28
I installed the 7.10 rc and I had some problem
this is my hardware
Setup: Primary Backend/Frontend
Hardware
Motherboard: Mini-ITX Motherboard LV-671
CPU: Pentium Intel(R) Pentium(R) M processor 1.70GHz
RAM: 512 (work well also with only 256 Mb)
Video Card: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
Sound Card: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
HD: now only 40 Gb
Remote: grey hauppauge and M$ mce remote via USB
Tuners: 1 hauppauge PVR150 MCE and 1 hauppauge PVR150 (i tryed also one PVR350 but.. the tuner is less sensitive than the PVR150 I don't know is the hardware is damaged I buy it used)

If I don't use the fglx driver playng tv I hear sound but the video is a black screen, if I set the fglx driver in the mythbuntu-control-center  see the video and hear the sound but the movie was not fluid, there's a lot of stop and go.
Certanly the video driver don't work well, but is not possible use the mythtv without the advance grafic driver.
I made some mistake or.. it's a problem of other people?

---

### Post by Al_Vampyre on 2007-10-30
I have always found a slight judder in MythTV using the proprietary ATI drivers that I was never able to iron out, TV was just fine with opensource drivers though so I just used them.

---

### Post by mocha on 2007-11-06
PVR-250 user here.  I have an Nvidia 7600GS card and was connecting it to an LCD monitor with the DVI-D connection.  The monitor could only go to 60 Hz vertical refresh.  I finally determined after many months of thinking the problem was software or driver related, that the problem was actually the DVI connection and refresh rate.  As soon as I reconfigured X to use the VGA output at 75 Hz all of my judder problems disappeared.  Very disappointing that I cannot get 75 Hz on the DVI connection though.  Thought you might like to know this.  This was my first LCD, so I was not aware of the problems that can occur with LCD refresh rates.

---

