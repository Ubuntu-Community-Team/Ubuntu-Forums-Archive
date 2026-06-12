---
title: "Enable surround sound through HDMI"
date: 2011-03-20
forum: Multimedia Software
---

### Post by mwhwsmith on 2011-03-20
I have a Acer Aspire Revo R3600 running Ubuntu 10.10. Its a clean install, all I have done is update the NVidia drivers and ASLA.
 
The PC connects to my AV Receiver via HDMI and I have stereo sound but no surround sound. If I go to System > Preferences > Sound and look under the hardware tab I only have "Internal Audio Digital Stereo (HDMI) Output" and no mention of surround sound or 5.1 etc.
 
I assume this is part of the problem. Any suggestions on what I need to do to fix this please.
 
Thanks
- M

---

### Post by lidex on 2011-03-20
Have you tried selecting a different profile on that tab?

---

### Post by papibe on 2011-03-20
It is possible that some of the speakers are muted. Try:
```
$ alsamixer 
```
to check both the mute status and the volume of each output.  That is a text mode(curses) application. User the keyboard's arrows to move arround.

After that you could try:
```
$ speaker-test -Dsurround51 -c6 -twav
```
or
```
$ speaker-test -Dplug:surround51 -c6 -twav
```
to test each speaker individually.

Good luck!

---

