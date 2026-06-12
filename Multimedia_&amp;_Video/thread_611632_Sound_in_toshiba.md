---
title: "Sound in toshiba"
date: 2007-11-13
forum: Multimedia &amp; Video
---

### Post by lik on 2007-11-13
I´m new to linux, but I really want to learn! 
Just installed ubunto on my laptop whit dual boot option (xp and ubunto), managed to install nvidia drivers (taken some time to figure it out lol) and now i'm having a big problem with installing the sound card. I get bips but thats it. Did everything in the comprehensive sound thingy post of this forum and when I get to step ''sudo modprobe snd-hda-intel'', i get this error message:

FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-14-generic/updates/alsa/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)


I've tried to install alsa drivers in other ways with the help of other posts. The did a cleanup explainde in the comprehensive post, but still didnt work. 

At some point, I tried to delete the files in /usr/src/alsa to begin again with instalation but it says I cant delete because of restricted previleges.

I'm sorry for yet another sound problem post, but I really want to use ubunto, really want to learn! 

Thanks in advance and thanks for this fantastic community for all the help given to guys like me!

P.S. When I try to open the volume control it says no gstreamer plugins or devices found. And the aplay -l says no sound card installed.

---

### Post by lik on 2007-11-13
MAGIC!! Did absolutely nothing and it started working!

---

