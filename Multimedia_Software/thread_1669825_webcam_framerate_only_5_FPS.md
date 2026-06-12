---
title: "webcam framerate only 5 FPS"
date: 2011-01-18
forum: Multimedia Software
---

### Post by bugbear6502 on 2011-01-18
I'm aware that this is a common issue - I've spent "some time" googling. But I think my fault is not the common one.

I'm trying to set up my old-ish laptop as a Linux astronomy box.

I've installed Ubuntu 10.10 on my FujitsuSiemens AmiloPro V2000.

(details of machine:
[http://server/fujitsu/ds_amilo_pro_v_series_e.pdf](http://server/fujitsu/ds_amilo_pro_v_series_e.pdf)

Basically a 1.5 GHz, 3/4 Gb laptop 
)

I have a Philips spc880, flashed (on XP) to be a Philips spc900

[http://www.morgancomputers.co.uk/shop/detail.asp?ProductID=6313&CategoryID=452&SubCategoryID=522](http://www.morgancomputers.co.uk/shop/detail.asp?ProductID=6313&CategoryID=452&SubCategoryID=522)

This camera is very well known for astronomy. The camera is nicely detected by lsusb, cheese, wxAstroCapture and guvcview.

In all of these, I get 4-5 frames per second, regardless of settings.

In particular (following information found whilst googling) I have tried turning auto-expose on and off, and I have taken the resolution all the way down to 160x120.

Still 4-5 FPS.

The only variant I've spotted is that guvcview uses much less CPU and X server resource than the other apps.

I would welcome cures, or pointers to diagnostic paths I can follow.

Many astronomers use Windows, so I have recieved advice on astronomy forums to give up Linux and use Windows :-(

Edit; courtesy of a friend, I've now tried a couple more webcams (very cheap and low res); they show on lsusb as:

Bus 002 Device 008: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 Webcam

Bus 002 Device 009: ID 0ac8:307b Z-Star Microelectronics Corp. USB 1.1 Webcam

Both gave frame rates of around 25-30 on guvcview (and murdered my CPU!). So it looks like my issue either the spc990 camera or its drivers.

Edit; same camera on a windows XP machine showed 12-15 FPS under wxAstroCapture; box was [IMG]file:///tmp/moz-screenshot.png[/IMG]2.8 Ghz  Pentium 4 with 512 Mb RAM

    BugBear

---

### Post by no2498 on 2011-01-19
i have seen it has to do with the lighting/light
you need to turn something off
is all i remember

---

### Post by BicyclerBoy on 2011-01-19
From previous forums: auto-exposure dramatically effects frame rate.

Are you sure you refreshed your settings to the camera?

guvcview &
gstreamer-properties 

are useful for expting...(I see you tried guvcview)

Could be the driver is incomplete for that model webcam.

Webcams typically use jpeg compression so the quality control may have a big effect the fps.


Stellarium is well worth a look..in the 10.10 repos..

---

### Post by bugbear6502 on 2011-01-20
> **no2498 said:**
> i have seen it has to do with the lighting/light
you need to turn something off
is all i remember

Yeah - saw that. You're thinking of the slow shutter speed used for low light, and also the time taken for auto-expose.

At the moment, my lights are bright, and auto-expose disabled.

   BugBear

---

### Post by bugbear6502 on 2011-01-20
damn!

---

### Post by bugbear6502 on 2011-01-20
> **BicyclerBoy said:**
> From previous forums: auto-exposure dramatically effects frame rate.

Are you sure you refreshed your settings to the camera?

guvcview &
gstreamer-properties 

are useful for expting...(I see you tried guvcview)

Could be the driver is incomplete for that model webcam.

Webcams typically use jpeg compression so the quality control may have a big effect the fps.


Stellarium is well worth a look..in the 10.10 repos..

The driver "should" be OK. The SPC900 is the successor (and very similar) to the TouCam pro.

One guy, Luc Saillard essentially dedicated an entire project (pwc) to drivers for these cameras, and AFAIK pwc is part of Debian (amongst other things).

Further, I found some indications that the camera/drivers worked well in some 9.* versions of Ubuntu, but that many people are having trouble with 10.04 and later.

Further information; the camera gives almost exactly 10 FPS on my Fedora13 box, 
(Intel(R) Core(TM)2 Duo CPU     T5470  @ 1.60GHz).

Under Windows XP, another box (I'm at work!) gave 18 FPS (2.8 Ghz (2.79) Pentium 4 with 512 Mb RAM).

So the camera's clearly OK, and there is either a problem on Linux, or a problem with CPU load.

And yet, "top" doesn't show the CPU maxing out.

(I really have tried to find an answer myself before posting here!)

   BugBear

---

### Post by no2498 on 2011-01-20
look in the cheese help FAQ'S for the fix 

Edit; courtesy of a friend, I've now tried a couple more webcams (very cheap and low res); they show on lsusb as:

Bus 002 Device 008: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 Webcam

Bus 002 Device 009: ID 0ac8:307b Z-Star Microelectronics Corp. USB 1.1 Webcam

Both gave frame rates of around 25-30 on guvcview (and murdered my CPU!). So it looks like my issue either the spc990 camera or its drivers.

Edit; same camera on a windows XP machine showed 12-15 FPS under wxAstroCapture; box was [IMG]file:///tmp/moz-screenshot.png[/IMG]2.8 Ghz Pentium 4 with 512 Mb RAM

---

### Post by no2498 on 2011-01-20
look in the cheese help FAQ'S for the fix 

Edit; courtesy of a friend, I've now tried a couple more webcams (very cheap and low res); they show on lsusb as:

Bus 002 Device 008: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 Webcam

Bus 002 Device 009: ID 0ac8:307b Z-Star Microelectronics Corp. USB 1.1 Webcam

Both gave frame rates of around 25-30 on guvcview (and murdered my CPU!). So it looks like my issue either the spc990 camera or its drivers.

Edit; same camera on a windows XP machine showed 12-15 FPS under wxAstroCapture; box was [IMG]file:///tmp/moz-screenshot.png[/IMG]2.8 Ghz Pentium 4 with 512 Mb RAM

---

### Post by bugbear6502 on 2011-01-21
> **no2498 said:**
> look in the cheese help FAQ'S for the fix 


More "a fix" than "the fix", I'm afraid. Having messed with gstream-properties, I had to reboot to get the camera working at all!

   BugBear

---

### Post by no2498 on 2011-01-21
was for the other 2 cams sorry

---

