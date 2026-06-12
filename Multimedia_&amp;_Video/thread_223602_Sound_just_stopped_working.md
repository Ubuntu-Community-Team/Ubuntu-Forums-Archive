---
title: "Sound just stopped working"
date: 2006-07-26
forum: Multimedia &amp; Video
---

### Post by igsimon on 2006-07-26
I am new to UBUNTU and LINUX. I had sound working fine yesterday but today I did something and it stopped working I changed to the K7 kernal and downloaded a few programs. I get the following with aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

alsamixer seems to show good mix and volume controls are fine. 

I loaded sysv-rc-conf to look around but do not know enough to see a problem. 

Help please _ i do not wantto have to load from scratch:confused:

---

### Post by igsimon on 2006-07-26
Just to add - sound problem is all - videos, mp3, and DVD and CD

---

### Post by igsimon on 2006-07-26
I just found the answer in a related stop work - I right clocked on the sound slider and opened volume control - I found PCM set to mute.

---

