---
title: "LinuxTV compiles but nothing runs."
date: 2011-07-06
forum: Multimedia Software
---

### Post by kilowhisky on 2011-07-06
I don't know why i did it but i decided to updated my linuxTV build using the instructions here:

[http://linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers](http://linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers)

It all builds and installs correctly but i can not load any drivers for my hauppage 2250, pvr-150, or pvr-500. 

When i try to modprobe saa7164 i get this. 

```


WARNING: Error inserting media (/lib/modules/2.6.38-8-generic/kernel/drivers/linux/drivers/media/media.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting videodev (/lib/modules/2.6.38-8-generic/kernel/drivers/media/video/videodev.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting v4l2_common (/lib/modules/2.6.38-8-generic/kernel/drivers/media/video/v4l2-common.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting dvb_core (/lib/modules/2.6.38-8-generic/kernel/drivers/media/dvb/dvb-core/dvb-core.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting saa7164 (/lib/modules/2.6.38-8-generic/kernel/drivers/media/video/saa7164/saa7164.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

Dmesg Gives

```

[69036.614770] v4l2_compat_ioctl32: Unknown symbol put_compat_timespec (err 0)

```


Google brings up nothing. Can anyone help?

---

