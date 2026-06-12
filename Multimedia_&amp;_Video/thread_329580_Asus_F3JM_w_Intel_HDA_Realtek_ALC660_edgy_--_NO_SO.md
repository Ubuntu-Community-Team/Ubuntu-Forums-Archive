---
title: "Asus F3JM w/ Intel HDA Realtek ALC660 edgy -- NO SOUND"
date: 2007-01-01
forum: Multimedia &amp; Video
---

### Post by Buggin on 2007-01-01
Clean install of edgy on Asus F3JM and I've got no sound. I've followed all the instructions I can find to get it working and haven't had any luck. I've been waiting to hear the login jingle and haven't been that lucky yet. I've followed the alsa instructions for a regular install, the alsa bugtracker instructions, the Intel HDA howto, and the F3Jc threads in these forums. None of these methods have fixed my problem... when I tried to patch alsa only 1 out of 4 dumps succeeded. Here's is the output from several of the usual asked for commands. Any help is greatly appreciated.


cat /proc/asound/version:
Advanced Linux Sound Architecture Driver Version 1.0.13.
Compiled on Jan  1 2007 for kernel 2.6.17-10-generic (SMP).

lspci:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)


cat /proc/asound/card0/codec#0:
Codec: Realtek ALC660

aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC861 Digital [ALC861 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and this is at the bottom of my /etc/modprobe.d/alsa-base file
options snd-hda-intel model=asus-laptop



thanks ahead of time for the effort
if you need anything else just ask

---

### Post by Buggin on 2007-01-02
I got it all straightened out.

First, I installed the linux drivers from Realtek.

Second, I installed the beta version of the alsa drivers 1.0.14rc1 with the ./configure options from the Comprehensive Sound Problem Resolution Guide. I also installed the beta version of library and utilities although I don't know if it made a difference.

Finally, I rebooted and voila... the login jingle I've been dying to hear since I got this laptop.

PS My wife says she heard the sound play the other night and I just missed it... I think she was on drugs.

---

### Post by T-Mic on 2007-01-07
I'm having the exact same problem you were, and I was hoping you could clarify a few things.

Those drivers from Realtek, did you get them through the link to the OSS site?
[http://www.opensound.com/oss.html]("http://www.opensound.com/oss.html")

Also, where could I find those alsa drivers?

Thanks for any info you can provide, and congratulations on solving this annoying problem.

---

