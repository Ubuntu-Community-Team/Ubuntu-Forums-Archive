---
title: "music stutters when doing screen things"
date: 2008-04-18
forum: Multimedia &amp; Video
---

### Post by Titi on 2008-04-18
Hi all,
i have recently upgraded from Gutsy to Hardy. 
Now my music is stuttering every time i do screen things. with screen things i mean things like minimizing or maximizing windows, opening different tabs, etc...
this is really annoying. i'm pretty sure it happened after the upgrade. i have not enabled beryl or compiz or anything like that. 
any suggestions on how to solve this? or should i just wait for the official release of Hardy? 
thanks!

Maarten

---

### Post by ** Andy ** on 2008-04-18
This also happens to me with Hardy. I don't have Compiz enabled, either. I use an Nvidia 6200 graphics card with the latest official Nvidia driver. I've just installed the release candidate and updated most of the packages, so I presume this problem is either unknown or unfixed. It happens whenever minimising or maximising a window and whenever I switch between them. It's not confined to one application, either; it occurs when using Rhythmbox and VLC player. It seems as though some process or other interrupts the playback temporarily.

Just found what I think is the problem:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/190754](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/190754)

---

