---
title: "Karmic, Nvidia GTX 275 not recognized, no hdmi sound"
date: 2010-03-02
forum: Multimedia Software
---

### Post by wgw on 2010-03-02
I just downloaded Wubi 64 on a W7 box. The hdmi sound works on W7, but getting nothing from Karmic. And the graphics card is not recognized:

 bill@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I have the nvidia driver working, the image is fine, even suspend. Just no sound through HDMI. Also, alsamixer does not show it; only pcm, capture, and master. I can't say that alsa is working properly...

My next steps: log the bug on launchpad and try to download the newest nvidia drivers (190.53, .run file -- not sure how that works!).

But, before doing so, any suggestions?

---

### Post by farbird on 2010-03-03
try upgrading the alsa package...

via the script somewhere in this forum..

---

### Post by farbird on 2010-03-03
u may also wanna checkout some solutions at nvnews

---

### Post by wgw on 2010-03-03
Thanks for the suggestions. I did a modconf alsa<tab> and got nothing. That seems to say that the alsa drivers are not loading. Weird!

Will try a reinstall first. 

Thanks for the tips. It is just a question of time...something very obvious is missing.

---

### Post by wgw on 2010-03-03
Ok: only the internal sound card is being recognized. No GTX card listed. Could be that there are no alsa modules for that, and so the first step is to find out how to get that card recognized...

> cat /proc/asound/modules

0 snd_hda_intel


Need more than that!

---

