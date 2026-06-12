---
title: "Feisty: No sound, alsa compile fails."
date: 2007-08-26
forum: Multimedia &amp; Video
---

### Post by manicmonk on 2007-08-26
I have a dual-boot Feisty/WinXP system (a Shuttle, small format PC). This has an onboard VIA 82xx chip for AC97 sound. Everything has been working perfectly for many months. (I'm new to Linux, but techy and I can follow instructions.)

A week ago, the sound on Feisty suddenly went very low (Windows still fine).

To try to fix this I downloaded and compiled the latest alsa drivers as described in this tutorial:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

The process appeared to complete successfully, but resulted in NO sound at all in Feisty.

I then found and closely followed this tutorial:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

This indicated that Linux could "see" my soundcard, but there was no driver.

So I tried  "Getting the ALSA drivers from a *fresh* kernel" (still no sound) and then I tried " ALSA driver Compilation" both the latest rev, and the "stable" 1.0.12 version.

Unfortunately all attempts to compile the alsa drivers fail in a similar way:

Most of the error log is uneventful, but the end always looks something like this:

----

checking for which soundcards to compile driver for... via82xx
configure: creating ./config.status
[....snip...]
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
make -C /usr/src/linux-headers-2.6.20-16-generic SUBDIRS=/usr/src/modules/alsa-driver  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /usr/src/modules/alsa-driver/acore/memalloc.o
In file included from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/acore/memalloc.inc:1:26: error: linux/config.h: No such file or directory
In file included from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/include/adriver.h:742: error: redefinition of €˜jiffies_to_msecs€™
include/linux/jiffies.h:268: error: previous definition of €˜jiffies_to_msecs€™ was here
/usr/src/modules/alsa-driver/include/adriver.h:761: error: redefinition of €˜msecs_to_jiffies€™
include/linux/jiffies.h:290: error: previous definition of €˜msecs_to_jiffies€™ was here
In file included from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/include/adriver.h: In function €˜snd_pci_orig_save_state€™:
/usr/src/modules/alsa-driver/include/adriver.h:1099: error: too many arguments to function €˜pci_save_state€™
/usr/src/modules/alsa-driver/include/adriver.h: In function €˜snd_pci_orig_restore_state€™:
/usr/src/modules/alsa-driver/include/adriver.h:1103: error: too many arguments to function €˜pci_restore_state€™
make[3]: *** [/usr/src/modules/alsa-driver/acore/memalloc.o] Error 1
make[2]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[1]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [compile] Error 2

---

The first error seems to be when it cannot find linux/config.h

Any suggestions how I can get my sound back?

If worst-comes-to-worst, is is possible to re-install Ubuntu and retain all the applications I have installed and set up?

Thanks in advance

---

### Post by justinlindh on 2007-08-27
I'm having problems with ALSA, too. Hopefully you don't mind if I piggyback on this thread for a little help.

I just need to tell ALSA which audio device to use, and can't figure it out.

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK8S [NVidia CK8S], device 0: Intel ICH [NVidia CK8S]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK8S [NVidia CK8S], device 2: Intel ICH - IEC958 [NVidia CK8S - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I need to use card0, device 2. I've googled for hours now and still have no idea how to do that. Can anybody help?

---

