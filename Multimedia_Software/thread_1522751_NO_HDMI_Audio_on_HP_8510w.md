---
title: "NO HDMI Audio on HP 8510w"
date: 2010-07-02
forum: Multimedia Software
---

### Post by yahoorkc on 2010-07-02
Hi,

There is no HDMI Audio on my HP 8510w laptop.

Its current running Lucid 10.04 64-bit...running default on gnome.

Video is great. i have to press fn+f4 to get video displayed...thats fine...
but no audio...audio still plays out of my laptop speakers.

some things i tried,
-rebooting after hooking up the HDMI cable
- update my alsa drivers
  cat /proc/asound/version
  Advanced Linux Sound Architecture Driver Version 1.0.23.
  Compiled on Jun 28 2010 for kernel 2.6.32-22-generic (SMP).

..no luck.

Screen-shot of my nvidia driver settings...

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=162205&stc=1&d=1278097475[/IMG]


" aplay -l "..gives the following output...

*** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


anyone got this same problem and got around it?...i really appreciate your help !

thanks!
rk

---

