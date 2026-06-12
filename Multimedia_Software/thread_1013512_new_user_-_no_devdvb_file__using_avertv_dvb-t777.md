---
title: "new user - no /dev/dvb file? _using avertv dvb-t777"
date: 2008-12-16
forum: Multimedia Software
---

### Post by tinytim174 on 2008-12-16
I'd really appreciate some help here.. I'm trying to get my DVB card recognised.

First, what I've done so far:

Installed 8.1 ibex this morn.
I've updated sources, installed various programs as per [http://ubuntuforums.org/showthread.php?t=781352](http://ubuntuforums.org/showthread.php?t=781352)

Also, followed this threads (MM&V) 'getting started' step 1/5.

**I'm really stuck at stage 1**, after several hours :confused:
I apparently need this directory as per step 1 at [COLOR="Navy"][linuxtvs DVB install guide]("http://linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers")[/COLOR]
but I get this error when I run the command
```
$ ls -l /dev/dvb/
ls: cannot access /dev/dvb/: No such file or directory
```


Two other things that may help those who know
When I tried to identify my tuner card, I ran this including the -vnn variant, and got an error
```
$ /sbin/lspci -v
bash: /sbin/lspci: No such file or directory
```

Also "proprietry drivers" are being used to make the 'ATI/ATA proprietry FGLRX graphics driver' work. i.e. their activated.

I have gone to [linux tv's avertv 777 page]("http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTV_DVB-T_777_(A16AR)#Notes") but I dont know how to modify the kernel config (where are the fields on my machine to add/remove the [*] fields - its a mystery) , assuming I need to, given the kernel for ibex is probably newer than the one listed on that page.

I'v searched and cannot resolve this issue.

Appreciate any assistance****

---

### Post by wolfen69 on 2008-12-17
see post #4 [here]("http://ubuntuforums.org/showthread.php?p=6380942#post6380942").

---

### Post by tinytim174 on 2008-12-17
> **wolfen69 said:**
> see post #4 [here]("http://ubuntuforums.org/showthread.php?p=6380942#post6380942").

thanks wolfen69

I firstly followed your vlc advice, nothing (except using the video 4 linux 2 setting didn't cause an error)

I followed post four, and went to the link, but again i got stumped at the first hurdle:
```
$ cd /usr/src/linux 
bash: cd: /usr/src/linux: No such file or directory
```

I can see my card is supported - so technically its possible.  Also, the link in post #4 shows the number of my card is the same as another post where the suggestion was a modprobe for the same card No., but using that suggested modprobe just caused an error:
```
 modprobe saa7134 card=85,85 tuner=67,67
WARNING: Error inserting tveeprom (/lib/modules/2.6.27-9-generic/kernel/drivers/media/video/tveeprom.ko): Operation not permitted
WARNING: Error inserting videobuf_core (/lib/modules/2.6.27-9-generic/kernel/drivers/media/video/videobuf-core.ko): Operation not permitted
WARNING: Error inserting videobuf_dma_sg (/lib/modules/2.6.27-9-generic/kernel/drivers/media/video/videobuf-dma-sg.ko): Operation not permitted
WARNING: Error inserting v4l1_compat (/lib/modules/2.6.27-9-generic/kernel/drivers/media/video/v4l1-compat.ko): Operation not permitted
WARNING: Error inserting videodev (/lib/modules/2.6.27-9-generic/kernel/drivers/media/video/videodev.ko): Operation not permitted
WARNING: Error inserting v4l2_common (/lib/modules/2.6.27-9-generic/kernel/drivers/media/video/v4l2-common.ko): Operation not permitted
WARNING: Error inserting compat_ioctl32 (/lib/modules/2.6.27-9-generic/kernel/drivers/media/video/compat_ioctl32.ko): Operation not permitted
WARNING: Error inserting ir_common (/lib/modules/2.6.27-9-generic/kernel/drivers/media/common/ir-common.ko): Operation not permitted
WARNING: Error inserting tveeprom (/lib/modules/2.6.27-9-generic/kernel/drivers/media/video/tveeprom.ko): Operation not permitted
WARNING: Error inserting videobuf_core (/lib/modules/2.6.27-9-generic/kernel/drivers/media/video/videobuf-core.ko): Operation not permitted
WARNING: Error inserting videobuf_dma_sg (/lib/modules/2.6.27-9-generic/kernel/drivers/media/video/videobuf-dma-sg.ko): Operation not permitted
WARNING: Error inserting v4l1_compat (/lib/modules/2.6.27-9-generic/kernel/drivers/media/video/v4l1-compat.ko): Operation not permitted
WARNING: Error inserting videodev (/lib/modules/2.6.27-9-generic/kernel/drivers/media/video/videodev.ko): Operation not permitted
WARNING: Error inserting v4l2_common (/lib/modules/2.6.27-9-generic/kernel/drivers/media/video/v4l2-common.ko): Operation not permitted
WARNING: Error inserting compat_ioctl32 (/lib/modules/2.6.27-9-generic/kernel/drivers/media/video/compat_ioctl32.ko): Operation not permitted
WARNING: Error inserting ir_common (/lib/modules/2.6.27-9-generic/kernel/drivers/media/common/ir-common.ko): Operation not permitted
FATAL: Error inserting saa7134 (/lib/modules/2.6.27-9-generic/kernel/drivers/media/video/saa7134/saa7134.ko): Operation not permitted
FATAL: Error running install command for saa7134
```

appreciate if you've got a pointer for me :)

---

### Post by tinytim174 on 2008-12-18
Resolved.

Did a fresh install, /dev/dvb was there straight away.

---

