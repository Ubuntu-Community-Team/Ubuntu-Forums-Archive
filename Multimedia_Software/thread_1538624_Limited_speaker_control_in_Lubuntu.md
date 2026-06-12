---
title: "Limited speaker control in Lubuntu"
date: 2010-07-25
forum: Multimedia Software
---

### Post by gonzofan on 2010-07-25
I recently switched from Ubuntu to Lubuntu on my Acer Aspire netbook. When I had Ubuntu, in System Preferences I had a Sound mixer that would allow me to set the volume beyond 100%. It simply said "Sound" and was different than the applet feature. Both were preinstalled. With Lubuntu, I seem to have lost this option. I went through and installed Gnome ALSA Mixer along with Pulse Audio Control, but neither does what this simple volume control feature on Ubuntu did. My speakers are horrible, and the previous "Sound" feature really let me crank it up a bit. I'm not trying to blow my speakers out or anything; I would just like to be able to hear what I'm trying to listen to! Any help would be great! Thanks!

---

### Post by gonzofan on 2010-07-25
bump!;)

---

### Post by cavalier911 on 2010-07-25
Open lxterminal 
```
alsamixer
```

---

### Post by gonzofan on 2010-07-25
Alsa mixer isn't doing it. I have everything set as high as it will go there. I believe the control I was using in Ubuntu was gnome-volume-control, but it's not here in Lubuntu. There's nothing for volume control in System Preferences--everything is in Sound & Video. I just would like to have my volume go up as high as I was able to get it to go while in Ubuntu. I'd hate to have to switch back to it just to have my volume control back, but I can't figure out what else to do!

---

### Post by Mozak on 2010-09-09
try sudo apt-get install gnome-media

and than press alt+f2 and type gnome-volume-control it worked 4 me

---

### Post by lindolo on 2011-11-01
To solve my Lubuntu 11.10 USB speaker not working I installed the PulseAudio Volume Control. You can set your preferences with a GUI installed to the Sound & Video menu. I am using a GE soundbar model # 98930 that I am satisfied with.

---

