---
title: "Soundcard 'Asus Xonar' with 9.04"
date: 2009-09-11
forum: Multimedia Software
---

### Post by Bekul on 2009-09-11
Hi all, having trouble getting any sound at all from my computer running Ubuntu 9.04, using an Asus Xonar soundcard.

This guy can, apparantly: [http://www.amazon.com/Asus-Xonar-Sound-Card-Black/product-reviews/B001EZQ8YC](http://www.amazon.com/Asus-Xonar-Sound-Card-Black/product-reviews/B001EZQ8YC)

But I can't - what should I do to troubleshoot? I've set everything in prefs-> sound to all be alsa, and yes the volume is turned up. :)

*edit*

Just wanted to mention, I /can/ get sound using Vista (bleh), so the soundcard does actually work. :)

---

### Post by Bekul on 2009-09-18
Just a bump from a week later!

I understand that diagnosing sound problems in Ubuntu can be a pain, but...

Right now I'm dual booting between Ubuntu and Vista, and I really don't like Vista - but I /need sound/.

Is anyone please willing to help me diagnose why I'm not getting sound in Ubuntu, and how I can make sound work?

---

### Post by kostkon on 2009-09-18
First of all, could you open a terminal, give
```
aplay -l
```
and post the output here?

---

### Post by Bekul on 2009-09-18
> **kostkon said:**
> First of all, could you open a terminal, give
```
aplay -l
```
and post the output here?

Yes! I can, and just did. With uh, little to show for it:

b@Monster-B:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
b@Monster-B:~$

---

### Post by Bekul on 2009-09-20
Anyone else? The soundcard comes with a CD, that in Vista installed a program that controls the sound levels - I tried running this with WINE in Ubuntu, but the 'autorun.inf' on the CD doesn't seem to want to run.

---

### Post by slimsbims on 2009-10-07
Hello Bekul,
 
did you try to set the soundcard to OSS instead of ALSA ( -> System - Settings - Audio). I have got the D2X, and it works perfectly fine this way.

---

### Post by iranai on 2009-10-11
I had the same issue with my Xonar DX at first.  Note, I am using S/PDIF and not analog outputs. I use the alsa dirvers on 32bit Jaunty.  

Make sure on the volume controls (next to the clock on the task bar) that the device is set to something that says Xonar.  Mine is set to, "playback: Simultaneous output to Xonar DX - Multichannel..." 

If that is selected properly, go to applications>sound & video> and open Gnome Alsa Mixer (or install if non existant).  Click the correct tab, for example AV200, as the default tab may be the hdmi on your video card.  Make sure the Master and Analog volumes are turned up.  Since I am using S/PDIF check the box that says IEC958.  It then works for me.  Good luck.

---

