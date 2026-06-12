---
title: "Intel hda Sound not working completely"
date: 2008-12-12
forum: Multimedia Software
---

### Post by toasty_ghosty on 2008-12-12
Hello

I have an Hda Nvidia sound card. I believe it is an Intel hda equivalent. The sound on my system is very quite, the mic does not work and I believe this is the issue. I am trying to fix it via this link:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

However it fails at this step while I make the kernel patch:

> make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.12/pcmcia/vx'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.12/pcmcia'
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.12'
make -C /usr/src/linux-headers-2.6.27-9-generic SUBDIRS=/usr/src/alsa/alsa-driver-1.0.12  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/usr/src/alsa/alsa-driver-1.0.12/acore/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[2]: *** [/usr/src/alsa/alsa-driver-1.0.12/acore] Error 2
make[1]: *** [_module_/usr/src/alsa/alsa-driver-1.0.12] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [compile] Error 2


What would be the cause of this?

---

### Post by markbuntu on 2008-12-12
You need at least alsa 1.0.17 for that nvidia hda to work properly. If you are using Hardy 8.04 or Intrepid 8.10 this guide will help

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by toasty_ghosty on 2008-12-12
Thanks. I beefed while installing some drivers, killed my sound, and reinstalled the linux-generic package as a means to start over and now my sound works and is quite louder (I believe it must have upgraded me to a newer version in the software channels). Also, before reinstalling the package, when doing alsamixer it only had one option. Now I have all the options and ALSA seems to work under the sound settings. Thanks.

---

