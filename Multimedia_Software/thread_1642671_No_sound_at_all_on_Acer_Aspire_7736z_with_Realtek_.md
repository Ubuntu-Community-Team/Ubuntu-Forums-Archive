---
title: "No sound at all on Acer Aspire 7736z with Realtek ACL888, Please help!"
date: 2010-12-10
forum: Multimedia Software
---

### Post by edde_e on 2010-12-10
Hi, I am a new ubuntu user and I love it but I have a major problem:
I cant get alsa-drive to install on my system, i have tried everything and i look all over the net and tried every work aound and even the Alsa Upgrade Script and nothing I get the same error:
```

/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/acore/pcm_native.c: In function ‘snd_pcm_hw_params’:
/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/acore/pcm_native.c:489: error: implicit declaration of function ‘pm_qos_remove_requirement’
/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/acore/pcm_native.c:492: error: implicit declaration of function ‘pm_qos_add_requirement’
make[3]: *** [/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/acore/pcm_native.o] Error 1
make[2]: *** [/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/acore] Error 2
make[1]: *** [_module_/usr/src/Alsa-1.0.23/alsa-driver-1.0.23] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-23-generic'
make: *** [compile] Error 2

***************************************************************************
*  alsa-driver-1.0.23 make failed
***************************************************************************
```

It always happens on the make cmd. I have no sound at all. Here my system out put:

```
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Sat Dec 11 00:09:05 UTC 2010

!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"

!!DMI Information
!!---------------

Manufacturer:      Acer           
Product Name:      Aspire 7736                    

!!Kernel Information
!!------------------

Kernel release:    2.6.35-23-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         unknown
SMP Enabled:       Yes

!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.23
Utilities version:  1.0.23

!!Loaded ALSA modules
!!-------------------

!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No

!!Soundcards recognised by ALSA
!!-----------------------------

!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03) Realtek ACL888

!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:293e (rev 03)
    Subsystem: 1025:0296
```

I had used Fedora and Mandriva One before and never had this problem with this laptop.
I like the way Ubuntu is design and is more easy for my kids to use it.

---

