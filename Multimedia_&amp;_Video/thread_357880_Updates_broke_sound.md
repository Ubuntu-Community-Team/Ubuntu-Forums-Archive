---
title: "Updates broke sound?"
date: 2007-02-10
forum: Multimedia &amp; Video
---

### Post by eilu on 2007-02-10
I successfull configures sound using instructions I found on [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) (with slight modifications as to version numbers)... today there is no sound again! I know there was sound yesterday, and the changes I made today were:
1. installed conky (aptitiude) then updated it (synapic)
2. installed gdesklets, purged it and installed it again (aptitude; long story)
3. installed updates using synaptic; the updates are:
```
automatix2 (1.1-2.9-6.06dapper_i386) to 1.1-2.10-6.06dapper_i386
bind9-host (1:9.3.2-2ubuntu1.1) to 1:9.3.2-2ubuntu1.2
dnsutils (1:9.3.2-2ubuntu1.1) to 1:9.3.2-2ubuntu1.2
flashplugin-nonfree (9.0.31~ubuntu1~dapper1) to 9.0.31.0.1ubuntu1~dapper1
kdelibs-bin (4:3.5.2-0ubuntu18.1) to 4:3.5.2-0ubuntu18.2
kdelibs-data (4:3.5.2-0ubuntu18.1) to 4:3.5.2-0ubuntu18.2
kdelibs4c2a (4:3.5.2-0ubuntu18.1) to 4:3.5.2-0ubuntu18.2
language-pack-en (1:6.06+20061130) to 1:6.06+20070129
language-pack-en-base (1:6.06+20060725) to 1:6.06+20070129
language-pack-gnome-en (1:6.06+20061205) to 1:6.06+20070129
language-pack-gnome-en-base (1:6.06+20060725) to 1:6.06+20070129
libbind9-0 (1:9.3.2-2ubuntu1.1) to 1:9.3.2-2ubuntu1.2
libdns21 (1:9.3.2-2ubuntu1.1) to 1:9.3.2-2ubuntu1.2
libisc11 (1:9.3.2-2ubuntu1.1) to 1:9.3.2-2ubuntu1.2
libisccc0 (1:9.3.2-2ubuntu1.1) to 1:9.3.2-2ubuntu1.2
libisccfg1 (1:9.3.2-2ubuntu1.1) to 1:9.3.2-2ubuntu1.2
liblwres9 (1:9.3.2-2ubuntu1.1) to 1:9.3.2-2ubuntu1.2
libpq4 (8.1.4-0ubuntu1.1) to 8.1.4-0ubuntu1.3
libsmbclient (3.0.22-1ubuntu3.1) to 3.0.22-1ubuntu3.2
linux-386 (2.6.15.25) to 2.6.15.26
linux-686-smp (2.6.15.25) to 2.6.15.26
linux-image-386 (2.6.15.25) to 2.6.15.26
linux-image-686 (2.6.15.25) to 2.6.15.26
linux-restricted-modules-386 (2.6.15.25) to 2.6.15.26
linux-restricted-modules-686 (2.6.15.25) to 2.6.15.26
linux-restricted-modules-common (2.6.15.12-1) to 2.6.15.12-28.1
samba-common (3.0.22-1ubuntu3.1) to 3.0.22-1ubuntu3.2
smbclient (3.0.22-1ubuntu3.1) to 3.0.22-1ubuntu3.2

Installed the following packages:
linux-image-2.6.15-28-386 (2.6.15-28.51)
linux-image-2.6.15-28-686 (2.6.15-28.51)
linux-restricted-modules-2.6.15-28-386 (2.6.15.12-28.1)
linux-restricted-modules-2.6.15-28-686 (2.6.15.12-28.1)

```
system is a notebook. additional information:
```
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
~$ modinfo soundcore
filename:       /lib/modules/2.6.15-28-686/kernel/sound/soundcore.ko
description:    Core sound module
author:         Alan Cox
license:        GPL
alias:          char-major-14-*
vermagic:       2.6.15-28-686 SMP preempt 686 gcc-4.0
depends:
srcversion:     DD426F1CCA2CC5F060F6F92
```

please help! this is driving me crazy!

---

### Post by eilu on 2007-02-11
solved. I opted to do a clean reinstall of the latest drivers. This thread can be closed and/or deleted.

---

