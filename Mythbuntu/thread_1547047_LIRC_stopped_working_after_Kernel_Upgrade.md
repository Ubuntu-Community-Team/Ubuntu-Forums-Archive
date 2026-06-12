---
title: "LIRC stopped working after Kernel Upgrade"
date: 2010-08-06
forum: Mythbuntu
---

### Post by RowanC on 2010-08-06
My remote has stopped working with the last kernel upgrade (2.6.32-24) - I can choose the previous kernel (2.6.32-23) and the remote (and my LCD display) start working again. Any ideas? anything I can do to help?

Thanks.

output of dmesg | grep lirc:
```
[    6.970411] lirc_dev: IR Remote Control driver registered, major 61
[    7.222910] lirc_imon: disagrees about version of symbol lirc_register_driver
[    7.222913] lirc_imon: Unknown symbol lirc_register_driver
[    7.236648] lirc_imon: disagrees about version of symbol lirc_register_driver
[    7.236653] lirc_imon: Unknown symbol lirc_register_driver
[   14.769351] lirc_imon: disagrees about version of symbol lirc_register_driver
[   14.769356] lirc_imon: Unknown symbol lirc_register_driver
```

PC Details:
Mythbuntu 10.04
Kernel:2.6.32-24-generic
Motherboard: Gigabyte GA-M51GM-S2G
RAM: 1Gb
CPU: Athlon 64x2 3800+
HD:500Gb WD
Video: Nvidia Geforce 8400GS 512Mb
Case: Antec Fusion / RM200 remote / IMON LCD

P.S. Mythbuntu is awesome! I have 100% Wife (and daughter) acceptance factor - it tapes playschool everyday :-)

---

### Post by ian dobson on 2010-08-06
Hi,

Did you manually install an updated version of lirc? The errors your seeing come from a version conflict from the kernel/lirc.

If the worst comes to the worst boot the old kernel and wait for an update for lirc.

Maybe have a look here:- [http://ubuntuforums.org/showthread.php?t=1460064](http://ubuntuforums.org/showthread.php?t=1460064)
Regards
Ian Dobson

---

### Post by RowanC on 2010-08-09
Thanks Ian,

The advice on that link worked perfectly. To summarise in case anyone else is having the issue the code below worked for me (change the kernel num to your kernel num):
```
sudo mv /lib/modules/2.6.32-24-generic/kernel/ubuntu/lirc/lirc_imon/lirc_imon.ko ~/.
sudo dpkg-reconfigure lirc-modules-source
```

Cheers,
Rowan.

---

