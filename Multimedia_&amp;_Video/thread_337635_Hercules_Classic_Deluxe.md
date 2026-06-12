---
title: "Hercules Classic Deluxe"
date: 2007-01-13
forum: Multimedia &amp; Video
---

### Post by zehntagebart on 2007-01-13
Hi all,
i followed installation guide on [http://ubuntuforums.org/showthread.php?p=1705574](http://ubuntuforums.org/showthread.php?p=1705574)
the cam works after all. but after a reboot i have to do the following again that the cam works:

sudo modprobe videodev
sudo modprobe i2c_core
sudo insmod /lib/modules/`uname -r`/extra/ov51x.ko
sudo insmod /lib/modules/`uname -r`/extra/ov519_decomp.ko

what do i have to do that the cam works automatic after a reboot?

many thanks

carsten

---

### Post by gentle_turtle on 2007-01-31
Hi there,

I have posted already a howto to this in the following thread:
[http://www.ubuntuforums.org/showthread.php?t=338338&highlight=hercules](http://www.ubuntuforums.org/showthread.php?t=338338&highlight=hercules)

Works well for me. Have fun

---

