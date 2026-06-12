---
title: "modprobe erm"
date: 2006-08-10
forum: Multimedia &amp; Video
---

### Post by lhds on 2006-08-10
hello .... i am probing a tv card ...

i get in return:
insmod /lib/modules/2.6.17.7/kernel/drivers/media/video/saa7134/saa7134.ko sox -c 2 -s -w -r 32000 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp tuner=54 card=65 i2c_scan=1 oss=1 video_nr=0 dsp_nr=1 mixer_nr=3
FATAL: Error inserting saa7134 (/lib/modules/2.6.17.7/kernel/drivers/media/video/saa7134/saa7134.ko): Unknown symbol in module, or unknown parameter (see dmesg)

this line: sox -c 2 -s -w -r 32000 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp
i typed it with the hope that enabeling dsp_nr=1 and mixer_nr=3
i get sound off the card. 
but anyway those 2 params could not load into options of modbrpbe.d folder in /etc.
now that i want to remove them, i did i removed the line 
options saa7134 tuner=54 card=65 i2c_scan=1 oss=1 video_nr=0 dsp_nr=1 mixer_nr=3 in etc/modprobe.d/options 
but i still get that /lib/modules/2.6.17.7/kernel/drivers/media/video/saa7134/saa7134.ko sox -c 2 -s -w -r 32000 -t ossdsp /dev/dsp1
can i just know where this line was inserted to ? any suggestions so i can remove it ?
wasnt in /etc/modules nor etc/modprobe.d/options
:o :confused:

---

### Post by mlind on 2006-08-10
If you used insmod, you should be able to remove the module using **rmmod**. You should be probing modules using **modprobe** (insert) and **modprobe -r** (remove) instead.


After you've removed module from kernel using rmmod, does this procude the same error
```

sudo modprobe saa7134

```

---

### Post by lhds on 2006-08-11
```
lhds@lhds-desktop:~$ sudo modprobe -r -v saa7134
rmmod /lib/modules/2.6.17.7/kernel/drivers/media/video/video-buf.ko
rmmod /lib/modules/2.6.17.7/kernel/drivers/media/video/compat_ioctl32.ko
rmmod /lib/modules/2.6.17.7/kernel/drivers/media/video/v4l2-common.ko
rmmod /lib/modules/2.6.17.7/kernel/drivers/media/video/v4l1-compat.ko
rmmod /lib/modules/2.6.17.7/kernel/drivers/media/video/ir-kbd-i2c.ko
rmmod /lib/modules/2.6.17.7/kernel/drivers/media/common/ir-common.ko
rmmod /lib/modules/2.6.17.7/kernel/drivers/media/video/videodev.ko
lhds@lhds-desktop:~$ sudo modprobe -v saa7134
insmod /lib/modules/2.6.17.7/kernel/drivers/media/video/videodev.ko
insmod /lib/modules/2.6.17.7/kernel/drivers/media/common/ir-common.ko
insmod /lib/modules/2.6.17.7/kernel/drivers/media/video/ir-kbd-i2c.ko
insmod /lib/modules/2.6.17.7/kernel/drivers/media/video/v4l1-compat.ko
insmod /lib/modules/2.6.17.7/kernel/drivers/media/video/v4l2-common.ko
insmod /lib/modules/2.6.17.7/kernel/drivers/media/video/compat_ioctl32.ko
insmod /lib/modules/2.6.17.7/kernel/drivers/media/video/video-buf.ko
insmod /lib/modules/2.6.17.7/kernel/drivers/media/video/saa7134/saa7134.ko sox -c 2 -s -w -r 32000 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp tuner=54 card=65 i2c_scan=1 oss=1 video_nr=0 dsp_nr=1 mixer_nr=3
FATAL: Error inserting saa7134 (/lib/modules/2.6.17.7/kernel/drivers/media/video/saa7134/saa7134.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

i am efraid yes .

how to remove those comands?
i did a sudo modprobe -r saa7134 sox or "sox" for example
it throws back there is no module called sox.

---

### Post by lhds on 2006-08-11
its ok got it working
how? not hard infact i did a normal modprobe saa7134 and realised that 
it was reading from options.save in the modprobe.conf folder. 
well well ....

---

