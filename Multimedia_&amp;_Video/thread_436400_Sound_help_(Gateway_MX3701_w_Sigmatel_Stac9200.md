---
title: "Sound help (Gateway MX3701 w/ Sigmatel Stac9200"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by Micam93 on 2007-05-07
I have read this in many other places, and many people have fixed it, but no matter what methods I have tried, I cannot get it to work. I am new to Ubuntu. And hopefully I can get this fixed.
I have a Gateway MX3701 notebook
The sound is a Sigmatel Stac9200

any other information you need, I will be happy to provide, because I really don't like having to boot into windows  just for my music / video.
As a side note, if anyone can help me with my inverted mouse problem on my Wacom Graphire4 Tablet.

Thanks in advance.

---

### Post by Micam93 on 2007-05-08
Bump

---

### Post by Micam93 on 2007-05-09
Can no one help? This is my only problem with Ubuntu.

---

### Post by Micam93 on 2007-05-10
Bump...

---

### Post by Micam93 on 2007-05-12
Bump :(

---

### Post by Micam93 on 2007-05-14
Bump...

---

### Post by johntkucz on 2007-06-21
YES! (sort of), I'm in the exact same boat.  Same mx3701, same sound problems.  Been trying everything.  
I tried the 
mask=8 thing with the alsa-base file (which produced more errors, 222: devices not found)

Our aplay -l shows:
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and I think the Modem is scrambled in and identified by linux as the soundcard, don't know how to remedy that though.  When you solve, i'll solve it; and vice versa

---

### Post by superhaus on 2007-06-21
Tagging this thread.

I have a Gateway with no sound too.

---

### Post by johntkucz on 2007-08-01
not much action here, but I still have the same problem.  I FINALLY (YES!) got dual-boot to work and can boot into windows xp with sound. funny, I had to download the xp driver (not a good sign for ubuntu if windows xp needs special driver to download, too!). 

I put a ton of time into this but new a lot less about linux.  we'll see what happens.

---

### Post by rkrisher on 2007-10-16
While I was searching around for modem drivers to work on my MT3705 I saw it stated a few places that the MX3701 has the same motherboard and components.  Try the instructions for sound I posted here: [http://ubuntuforums.org/showthread.php?p=3524207](http://ubuntuforums.org/showthread.php?p=3524207)

Maybe it will work for your laptop

---

