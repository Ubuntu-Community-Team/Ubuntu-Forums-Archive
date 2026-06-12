---
title: "imon trouble"
date: 2012-02-12
forum: Mythbuntu
---

### Post by octessence on 2012-02-12
I have been fighting with mythbuntu (11.10) trying to get my remote control working all day and I still haven''t have any success so I thought it's time to ask for some help.

I have an Antec Micro Fusion 350 case that comes with a Veris RM100 remote. I also have a Logitech Harmony 900 which will be configured as and MCE remote (since this seemed to work better in Windows that trying to configure it as an IMON remote).

I have managed to track down the problem to the loading of the lirc_imon kernel module:

```

~# modprobe -v lirc_imon
insmod /lib/modules/3.0.0-15-generic-pae/kernel/drivers/staging/lirc/lirc_imon.ko ir_protocol=1
FATAL: Error inserting lirc_imon (/lib/modules/3.0.0-15-generic-pae/kernel/drivers/staging/lirc/lirc_imon.ko): Invalid argument

```This also produces the dmesg output:
```

[ 2080.465043] lirc_imon: module is from the staging directory, the quality is unknown, you have been warned.
[ 2080.465151] lirc_imon: disagrees about version of symbol lirc_register_driver
[ 2080.465155] lirc_imon: Unknown symbol lirc_register_driver (err -22)

```

---

### Post by octessence on 2012-02-12
It seems that going back to an ealier kernel solves the problem so this must just be in the 3.0.0-15 build of the kernel.

---

### Post by jwhiteIT on 2012-07-29
Hi, I had simular issues.  Have a look at my post 12 in the following:
[http://ubuntuforums.org/showthread.php?t=2026951&highlight=imon&page=2](http://ubuntuforums.org/showthread.php?t=2026951&highlight=imon&page=2)

This got me sorted.

---

