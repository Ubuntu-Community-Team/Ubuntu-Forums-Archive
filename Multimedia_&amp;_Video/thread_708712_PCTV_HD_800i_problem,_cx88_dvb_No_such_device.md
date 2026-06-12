---
title: "PCTV HD 800i problem, cx88_dvb: No such device"
date: 2008-02-26
forum: Multimedia &amp; Video
---

### Post by brandon_r87 on 2008-02-26
Hello,

I bought the PCTV HD 800i tuner from woot.com, and waited until drivers had been developed for it.  I followed the guide from [LinuxTV]("http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_%28800i%29").

I attached my dmesg and lspci outputs below.  The dmesg output has some errors in it, and the lspci looks like it is an entry short compared to some of the other lspci outputs I've seen for this card.  When I try to modprobe cx88_dvb:

```
$ sudo modprobe cx88_dvb
FATAL: Error inserting cx88_dvb (/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko): No such device

```

Thanks
Brandon

Edit: Running Kubuntu Gutsy, with Nvidia drivers (have seen that they can cause issues with this card if setup incorrectly)

---

