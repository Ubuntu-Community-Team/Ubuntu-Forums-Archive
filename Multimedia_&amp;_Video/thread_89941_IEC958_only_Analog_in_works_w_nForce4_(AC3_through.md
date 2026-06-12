---
title: "IEC958: only Analog in works w/ nForce4 (AC3 through S/PDIF)"
date: 2005-11-13
forum: Multimedia &amp; Video
---

### Post by blazko on 2005-11-13
Rehi,

Yeah, I know, the never ending story for many people.
Okay, I am having a nForce4 board (Abit AN8 SLI). All the stuff is working pretty fine except the IEC958 optical out. I can only get it working for stereo output, e.g. if i start mplayer with a stereo track.
In alsamixer I I have to enable "Analog in" and it works, but when I want AC3 through, there is nothing. I have set from "Analog in" to "PCM" accordingly, but nothing works. I played around with "mplayer -ac hwac3 dvd://" and the like, but...

Here is the output of aplay -l:
>>>
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
<<<

And I use this /etc/asound.conf:
[http://www.mythtv.info/moin.cgi/DigitalSoundHowTo](http://www.mythtv.info/moin.cgi/DigitalSoundHowTo)
Optimised for nForce2/4 (the BIG config at the end!).

I am really going crazy, got it working one year ago with another i8x0 easily on Debian sid.

Thanx for any hints,
Timo

---

### Post by teaker1s on 2005-11-13
I have a c-media card optical is only stereo optical or S/PDIF

---

### Post by zzzPOOHzzz on 2007-04-06
did you ever get this problem resolved? i am on the an8 sli as well and im getting no sound


using optical as well

---

