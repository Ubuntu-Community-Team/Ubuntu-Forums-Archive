---
title: "HDMI Audio problem, ATI onboard"
date: 2010-11-30
forum: Multimedia Software
---

### Post by KrisWragg on 2010-11-30
I have spent all day reading articles on how to try and get audio to work over HDMI and I am stumped!

I have tried:
[LIST]
[*]switching it in the sound preferences
[*]checking the mute status in alsamixer
[*]tried switching to radeonhd driver which then wrecked X11 and I had to use a live-CD to fix it, radeonhd doesn't appear to work with Maverick!
[*]tried "aplay -D plughw:1,3 test.wav" but nothing happened
[*]tried disabling onboard sound so HDMI is the only option
[/LIST]

Running a fully up to date Maverick Meercat, the motherboard has an ATI X1200 onboard graphics which works fine aside from no audio over the HDMI.  If I try and play a video in mplayer or music in Rhythmbox when HDMI output is selected then they just play silent but super fast for some reason. 

Any ideas?

```
kris@penguin:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by lidex on 2010-12-01
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by KrisWragg on 2010-12-04
Hi, here are the results:

[http://www.alsa-project.org/db/?f=688ad8e5ddd9ff43f9b80e3f3fa263a5774c4875](http://www.alsa-project.org/db/?f=688ad8e5ddd9ff43f9b80e3f3fa263a5774c4875)

---

### Post by lidex on 2010-12-04
> **KrisWragg said:**
> Hi, here are the results:

[http://www.alsa-project.org/db/?f=688ad8e5ddd9ff43f9b80e3f3fa263a5774c4875](http://www.alsa-project.org/db/?f=688ad8e5ddd9ff43f9b80e3f3fa263a5774c4875)

This should move you in the right direction:
[http://ubuntuforums.org/showpost.php?p=6690552&postcount=4](http://ubuntuforums.org/showpost.php?p=6690552&postcount=4)

---

### Post by KrisWragg on 2010-12-04
I read that one, the ATI proprietary drivers are not available for my system.  It has an X1200 onboard graphics and it isn't supported any more.

---

