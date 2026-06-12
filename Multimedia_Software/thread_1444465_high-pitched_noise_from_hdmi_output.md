---
title: "high-pitched noise from hdmi output"
date: 2010-04-01
forum: Multimedia Software
---

### Post by jure1873 on 2010-04-01
I've got my LCD TV connected to my ubuntu laptop (hdmi cable) and when there is no sound coming out I hear a high pitched noise. If I've got a movie playing or something else everything is ok. The funny thing is that when I rebooted into windows yesterday there was no such noise, so it's definitely a software problem. I've tried commenting out the intel power saving option (modprobe snd-hda-intel power_save=0 power_save_controller=Y) but it didn't help. I don't know what to do.

---

### Post by chkneater on 2010-04-01
I had a similar problem that was extremely intermittent and took me forever to figure out that it was the small fan on my video card.  Even though it was brand new, some little speck or something got into the bearings and it has a VERY annoying whine that goes away after a little while.  Also check for wires next to your power supply or processor fans.  Noise is most likely a physical disturbance, not related to software.

---

### Post by chkneater on 2010-04-01
Oh, and another thing, sometimes the power saving options need to be changed in the BIOS also.  Windows may ignore the BIOS settings, hence the reason the noise is gone when booted in Windows.  Now that I paid attention to it, my monitor seems to be making noise too, but it's an old POS anyways!

---

