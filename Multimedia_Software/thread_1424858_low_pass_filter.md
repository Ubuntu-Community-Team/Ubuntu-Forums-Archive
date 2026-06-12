---
title: "low pass filter"
date: 2010-03-08
forum: Multimedia Software
---

### Post by marinero_arrr on 2010-03-08
I have a asus d2x audio card:
[in lspci] Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
connected to 7.1 audio sistem without a lowpass filter in it. 
yesterday I activated  the option 
enable-lfe-remixing = yes
in
/etc/pulse/daemon.conf
to get some artificial bass from in the stereo files.

I observed that I get a copy of the center channel on the surround channel. what i want it's to get the low freq audio form all the channels and send it to the LFE channel.

there is a way to make a software lowpass filter with pulseaudio?

---

