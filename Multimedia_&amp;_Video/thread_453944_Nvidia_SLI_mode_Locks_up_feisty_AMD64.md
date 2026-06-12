---
title: "Nvidia SLI mode Locks up feisty AMD64"
date: 2007-05-24
forum: Multimedia &amp; Video
---

### Post by fain on 2007-05-24
I have two evga 7600 gt's that when not in SLI mode my system works great. never crashes, rock solid. but as soon as i enable SLI the system boots and works for awhile. it randomly locks up while doing several different things. most of the time it seems to lock up under some sort of 3d app. but it locked up on me while installing ie4linux package :confused: i though it might've been totem visualization that was playing that did it. so i hard rebooted and restarted the installation....same thing in the same part of the installation. (i believe it was processing some ini) so i went in init 3 and it installed fine ???? it has something to do with X cause ive tried both the nvidia-glx and the nvidia-glx-new as well as the .run installer from nvidia driver site. i have searched the system log when these crashes happen but they just seem to omit the time that it happened.
i haven't had the problem in vista64 yet but i rarely use that piece o poo.

---

### Post by skshandilya on 2007-06-02
I have the same problems you have mentioned.

Here are some tips to prevent the crashing with SLI enabled.

Disable GL screensavers :(
No overclocking.
no beryl and compiz :(
Use "Option "SLI" "AFR" in /etc/X11/xorg.conf in the Screen section. This seems to be the most stable SLI option.

You could also try to disable powersaved, but I dont want to, electricty bills!!

I am able to play ut2k4 x86_64 with no problems at all.

My config
A8N-SLI
2 x 6600GT
Athlon64  4800+
bt787 TV tuner
Audigy ZS

---

