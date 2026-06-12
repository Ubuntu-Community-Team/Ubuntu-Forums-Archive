---
title: "[SOLVED] stuck at 100% volume: intel 82801"
date: 2008-07-22
forum: Multimedia Software
---

### Post by maestrobwh1 on 2008-07-22
EDIT: This is a bug in Hardy.
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/192382](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/192382)


"fixed it by"
add "options snd-hda-intel model=3stack-dig" to /etc/modprobe.d/alsa-base 
After that do a "sudo alsa force-unload; sudo modprobe snd-hda-intel" and you should have sound and kmix. Only the "master" channel will be useless.


I am stuck at full volume.  It happened after a recent update/upgrade.  The slider just won't move from 100%

Use of aumix from command line does nothing. 
code.:

user:~$ aumix -v 50
user:~$ (nothing displays so it looks like it worked)

I also used -w and -l in place of -v.  Same lack of result.

user:~$ aumix -q
igain 1, 1
phout 100, 100

I am at a loss on how to change this:confused:

aplay for my device:
card 0: Intel [HDA Intel], device 0: ALC662 Analog [ALC662 Analog]

lspci for my device:
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

---

