---
title: "Freeze for videos"
date: 2007-03-26
forum: Multimedia &amp; Video
---

### Post by jose99m on 2007-03-26
Hi,
This is a very strange problem. 
I first tried Ubuntu 6.06. Video was working still i tried a wmv. Since this moment, the system is blocking for every video format, needing a Alt-Sys-K, whatever the player used.
I installed a 6.10 completely (except for the /home partition, whitch is the same since the begining).

Video still refuse to work, forcing me to reboot Windows :(
I tried many things (gstreamer, xine,....), many forums, and have no idea. This forum is my last chance (maybe the Ubuntu 7.04 will save me ?).

DFI lanparty ultra D, Nforce4 (Realtek ACL850 AC"97)
GeForce 6200 TC with proprietary driver nvidia-glx

---

### Post by jose99m on 2007-03-26
up

---

### Post by jose99m on 2007-03-29
kern log :
Mar 29 21:04:49 desktop kernel: [17191055.716000] NVRM: Xid (0005:00): 8, Channel 00000000
Mar 29 21:04:51 desktop kernel: [17191057.908000] SysRq : SAK

---

### Post by jose99m on 2007-03-31
I tried the Live CD with VLC and it's working... 
So it's definitively a config file, created when the wmv was readed, whitch is freezing the system.
Where could it be ?

---

### Post by zeemon on 2007-05-12
I am new to Ubuntu although I tried several Linuxes over the last 8 years. I've never been satisfied with theses OSses before until now. Ubuntu really kicks *** and I am using my XP only 30% of the time now. But back to the problem:

I searched several forums and eventually found someone with the same problem I have. My system totally crashes (except the mouse) when I open any video file. Sometimes I hear the audio but the video remains blue. The funny thing is that in my folder preview I see the video content in the icon so my system must be able to read the video content I guess.
There is the issue of random freezes going around in the forum but I figured out that my problem is different as it only happens with videos (not with the youtube flash thingies, though)

Anyway, it is a real pain in the *** that I cannot watch videos on my new favourite os without freezing it.  My system specs:

Intel Pentium M 740
Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller
1GB Ram
Ubuntu 7.04 Feisty Fawn
Media Players: VLC, Totem, MPlayer

Can anybody help? Please? Is it maybe a config problem or a driver issue?

---

### Post by zeemon on 2007-05-12
As soon as I thought I could not solve my problem myself and started posting here I finally found a solution. 2 Things:

1. switch to the intel driver (found the instructions in some thread around here)
--> the whole system doesn't crash anymore but videos may still not work
2. Disable Desktop effects
--> enjoy!

Thanks :)

---

### Post by jose99m on 2007-05-13
Hi, thx for your answer.
I first tried Linux in 2000, and Ubuntu 6.xx is the first one usable for me. I'm glad to use Windows only 10% of the time.

I have solved the problem with the 6.10 by using the free nvidia driver, in place of the proprietary nvidia-glx package.
The Fawn 7.04 solved the whole problem : maybe the nvidia package is more recent.

Your bug seems different. Did you try with the live CD ? Or another distro (it's easy with GeeXBox : [http://geexbox.org/fr/index.html](http://geexbox.org/fr/index.html)  ) ?

---

