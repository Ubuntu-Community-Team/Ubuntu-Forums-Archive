---
title: "Trying to build alsa-drivers"
date: 2008-05-28
forum: Multimedia Software
---

### Post by Cosmopolitan on 2008-05-28
Hi,
  I'm trying to install alsa on my Acer Aspire 4315. I use Ubuntu 7.10
  Initially, there was sound in the speakers, but when I plugged earphones in the jack, the sound was still in the speakers, and there was no sound in the earphones.
  I the tried to build alsa, and now there's no sound at all, neither  in the speakers nor in the  earphones.
  When clicking on the sound control, I get the message that "no devices are found".

  I followed the instructions on [http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html](http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html)    I can install the alsa_1.sh and reboot, but when I type 'sudo sh alsa_2.sh.txt' I get the following:

troels@Stru:~$ cd Alsa-musikdriver

troels@Stru:~/Alsa-musikdriver$ sudo sh alsa_2.sh.txt

[sudo] password for troels:

alsa_2.sh.txt: 1: &#65279;#!/bin/sh: not found

`/lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko' -> `/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko'

`/usr/src/alsa/alsa-driver-1.0.15/modules/snd-hda-intel.ko' -> `/lib/modules/2.6.22-14-generic/kernel/sound/snd-hda-intel.ko'

`/usr/src/alsa/alsa-driver-1.0.15/modules/snd-hwdep.ko' -> `/lib/modules/2.6.22-14-generic/kernel/sound/snd-hwdep.ko'

`/usr/src/alsa/alsa-driver-1.0.15/modules/snd-mixer-oss.ko' -> `/lib/modules/2.6.22-14-generic/kernel/sound/snd-mixer-oss.ko'

`/usr/src/alsa/alsa-driver-1.0.15/modules/snd-page-alloc.ko' -> `/lib/modules/2.6.22-14-generic/kernel/sound/snd-page-alloc.ko'

`/usr/src/alsa/alsa-driver-1.0.15/modules/snd-pcm-oss.ko' -> `/lib/modules/2.6.22-14-generic/kernel/sound/snd-pcm-oss.ko'

`/usr/src/alsa/alsa-driver-1.0.15/modules/snd-pcm.ko' -> `/lib/modules/2.6.22-14-generic/kernel/sound/snd-pcm.ko'

`/usr/src/alsa/alsa-driver-1.0.15/modules/snd-rtctimer.ko' -> `/lib/modules/2.6.22-14-generic/kernel/sound/snd-rtctimer.ko'

`/usr/src/alsa/alsa-driver-1.0.15/modules/snd-seq-device.ko' -> `/lib/modules/2.6.22-14-generic/kernel/sound/snd-seq-device.ko'

`/usr/src/alsa/alsa-driver-1.0.15/modules/snd-seq-midi-event.ko' -> `/lib/modules/2.6.22-14-generic/kernel/sound/snd-seq-midi-event.ko'

`/usr/src/alsa/alsa-driver-1.0.15/modules/snd-seq-oss.ko' -> `/lib/modules/2.6.22-14-generic/kernel/sound/snd-seq-oss.ko'

`/usr/src/alsa/alsa-driver-1.0.15/modules/snd-seq.ko' -> `/lib/modules/2.6.22-14-generic/kernel/sound/snd-seq.ko'

`/usr/src/alsa/alsa-driver-1.0.15/modules/snd-timer.ko' -> `/lib/modules/2.6.22-14-generic/kernel/sound/snd-timer.ko'

`/usr/src/alsa/alsa-driver-1.0.15/modules/snd.ko' -> `/lib/modules/2.6.22-14-generic/kernel/sound/snd.ko'

cp: cannot stat `/usr/src/alsa/alsa-driver-1.0.16/modules/snd-hda-intel.ko': No such file or directory

cp: cannot stat `/usr/src/alsa/alsa-driver-1.0.16/modules/snd-hwdep.ko': No such file or directory

cp: cannot stat `/usr/src/alsa/alsa-driver-1.0.16/modules/snd-mixer-oss.ko': No such file or directory

cp: cannot stat `/usr/src/alsa/alsa-driver-1.0.16/modules/snd-page-alloc.ko': No such file or directory

cp: cannot stat `/usr/src/alsa/alsa-driver-1.0.16/modules/snd-pcm-oss.ko': No such file or directory

cp: cannot stat `/usr/src/alsa/alsa-driver-1.0.16/modules/snd-pcm.ko': No such file or directory

cp: cannot stat `/usr/src/alsa/alsa-driver-1.0.16/modules/snd-rtctimer.ko': No such file or directory

cp: cannot stat `/usr/src/alsa/alsa-driver-1.0.16/modules/snd-seq-device.ko': No such file or directory

cp: cannot stat `/usr/src/alsa/alsa-driver-1.0.16/modules/snd-seq-midi-event.ko': No such file or directory

cp: cannot stat `/usr/src/alsa/alsa-driver-1.0.16/modules/snd-seq-oss.ko': No such file or directory

cp: cannot stat `/usr/src/alsa/alsa-driver-1.0.16/modules/snd-seq.ko': No such file or directory

cp: cannot stat `/usr/src/alsa/alsa-driver-1.0.16/modules/snd-timer.ko': No such file or directory

cp: cannot stat `/usr/src/alsa/alsa-driver-1.0.16/modules/snd.ko': No such file or directory

troels@Stru:~/Alsa-musikdriver$ 



  Please help an absolute beginner!
  Thanks a lot!

---

### Post by zenwalker on 2008-05-28
Well theres a lesser ver of Alsa driver but not 1.0.16 in u r system. Not sure why u r building it. Plz get it off the official repos.

---

### Post by Cosmopolitan on 2008-05-28
Hi zenwalker

  Thanks very much for your reply. Being a complete beginner and not understanding slang, I'm afraid I don't understand what "Plz get it off the official repos" means. Can you explain it to me? Thanks a lot - I appreciate your help!

---

