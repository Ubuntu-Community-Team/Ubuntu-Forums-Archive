---
title: "Inspiron 6400 S/PDIF Dongle"
date: 2009-05-10
forum: Multimedia Software
---

### Post by fh_scott on 2009-05-10
I have the Component Video+S/PDIF dongle from Dell attached to my Inspiron 6400.  I've never used the video part but the digital audio port works perfectly in Windows.  PowerDVD sends raw AC3/DTS over the port and all other windows sounds are processed into stereo PCM.

I cannot get this thing to work with Jaunty to save my life.  I've never tried with previous versions.

The pulseaudio volume monitor thinks it's sending sound to the STAC92XX Digital port.  I've tried every iteration of "option snd-hda-intel model=dell-m2x" in /etc/modprobe.d/alsa.base.conf and various entries in /etc/asound.conf (including empty).

There just isn't anything being recognized by the receiver.

I know the hw works.  It's no fuss in Windows.  This is the first thing I've ever not been able to get to work.

Anyone had success with this?

---

### Post by macey on 2011-05-25
Hello, did you ever manage to get this working? I am trying to do the same.

---

