---
title: "Audigy problem"
date: 2006-10-13
forum: Multimedia &amp; Video
---

### Post by drakedog on 2006-10-13
My sound don´t work, until i have replaced Audigy 2 with the on board sound. i not eaven have an device. How can a manual install this?


alsamixer: function snd_ctl_open failed for default: No such device
alsamixer

tnks8)


PS: Ubuntu 6.10, but i not even had an device on 6.06

---

### Post by leif3d on 2006-10-13
I have the same problem!:( 
I've followed every step on this guide:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

but nothing helps!:confused: 

What pisses me off the most is that last time I installed Ubuntu on the same machine it recognized my sound card with no problem...the same thing happened in my house...I happen to have the same motherboard on both computers: Tyan K8WE Thunder and Audigy 2 zs...I had to pop the Live CD in multiple times until it recognized my sound card...WTF is that suposed to mean? that Ubuntu randomly likes to configure devices? and if not you're out of luck? this sucks...

the problem is that everything else is so great in Ubuntu that I can't complain too much...but any help would be appreciated.

My /etc/modules reads like this:

  GNU nano 1.3.10             File: /etc/modules

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
rtc
sbp2
sr_mod
snd-emu10k1


I've tried "emu10k1" instead of "snd-emu10k1", but nothing...

I try opening alsamixer:

alsamixer: function snd_ctl_open failed for default: No such device

the fact that I don't have a sound folder under /dev may be part of the problem...

Thanks in advance to anyone that helps out!;)

---

### Post by DoorGunner on 2006-12-22
what was happening to me was Via kept starting up instead of the Audigy. 
If you go to your volume control when Ubuntu starts up you may find that the option for Via or what ever your generic mother board sound device is starts up before and takes over instead of Audigy.

To solve this you will need to go to 
> 
sudo gedit /etc/modprobe.d/alsa-base


in the bottom you may see stuff like this

options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2

Change what ever is there too look like this

> 
options snd-emu10k1 index=0
#options snd-bt87x index=-2
#options snd-atiixp-modem index=-2
#options snd-intel8x0m index=-2
#options snd-via82xx-modem index=-2


As long as emu10k1 is in index=0 it wil always start first. It doesnt matter what is after it. or even if it is hashed out (#). I Hashed mine to ensure it wouldnt start

index=0 starts first
index=1 starts second
etc etc

---

