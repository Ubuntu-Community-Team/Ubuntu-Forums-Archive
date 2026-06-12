---
title: "No voice via speakers but there via headphones"
date: 2013-01-01
forum: Multimedia Software
---

### Post by gonzoks on 2013-01-01
Okay, I am a bit baffled.  This is also my first post so bear with me.  Ill post what I think will be helpful, and feel free to ask for more details.  The short story:

On certain video files (no real pattern, doesn't seem dependent on video file type, etc) I have all of the sound effects but no voices.  So, I can hear everything going on but cannot hear people talking.  However, on the same video, if I plug my headphones in, all works like it should.  Note - It does not matter if I plug in the front of rear of my pc.  Another note, everything works fine via Win7 on the same box.  I have been googling to no avail.  

12.04 64b
Card: HDA Intel
Chip:  Realtek ALC889A
Integrated motherboard audio - Gigabyte X38-DQ6 - Most recent (still older) BIOS.
alsamixer = nothing muted or low - all full.
gnome-alsamixer =  nothing muted or low - all full.

When I run aplay -l I get the following.  Does it strike anyone as odd that it shows up the same twice?
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


It almost makes me think there is something blocking my system from processing the voice channel and perhaps I have a missing or conflicting package.  Is this possible?

Has anyone run across this?

Thanks in advance!

---

### Post by gonzoks on 2013-01-01
[http://www.alsa-project.org/db/?f=6d5a663acbef209bb9892d0a55c83e4bc4997475](http://www.alsa-project.org/db/?f=6d5a663acbef209bb9892d0a55c83e4bc4997475)

---

### Post by gonzoks on 2013-01-03
Was curious if anyone had any ideas on a direction to take this??? ):P

---

