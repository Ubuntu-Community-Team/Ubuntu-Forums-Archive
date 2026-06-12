---
title: "[SOLVED] Cannot play multiple video file simultaneously"
date: 2008-08-13
forum: Multimedia Software
---

### Post by BugBuster on 2008-08-13
Today I tried to play more than one video files simultaneously and somehow the second video file that i opened did not play well and would play like an image slide show..and no audio as well.

I opened first file in VLC and the second in Totem using Gstreamer..

But when i opened first file in Totem and the other in VLC both worked fine..so just wondering if there is something that i have missed out on my Ubuntu 8.04 clean install..

Also tried using the same application for both files as well..but in vain.

I tried several file formats..but each time the same results.

So how do i play multiple videos simultaneously without any hitches...would greatly appreciate any help..

My Config:
Ubuntu 8.04 Desktop, AMD X2 4000+, 2GBDDR2 800MHz,ATI Radeon X1250 onboard with proprietary drivers(fglrx),1400x900@75Hz..19" Acer AL1916w TFT monitor.

---

### Post by tuxxy on 2008-08-13
Have you tried setting up ALSA? system > prefs > sound

---

### Post by BugBuster on 2008-08-13
> **tuxxy said:**
> Have you tried setting up ALSA? system > prefs > sound

Hey..I tried that and already the things are looking better..however please give me some time to try a few more combinations before I close the thread

Thanks tuxxy..that was real quick..:)

---

### Post by tuxxy on 2008-08-13
No problem, if you need anything else bump the thread :)

---

### Post by bellis on 2008-09-06
I have the exact same problem as this guy has posted and I have tried as many combination as possible as I can think of and I am not having any luck with this.

lspci

> 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

Have a Dell Inspiron E1405
+ if you look at the drivers I can download for Windows OS for that laptop, they only mention
> 
SIGMATEL STAC 92XX C-Major HD Audio - 5.10.0.5515_RC22-WHQL, A11
Creative Labs Integrated Sound Blaster Audigy ADVANCED HD Audio - RC6, 44.1K A02

So I highly dont think i have Install Drivers... This might by my problem. any Ideas?

---

