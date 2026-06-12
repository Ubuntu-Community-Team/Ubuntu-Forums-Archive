---
title: "Demod -a and now no SPDIF"
date: 2008-02-12
forum: Multimedia &amp; Video
---

### Post by addisor on 2008-02-12
Would "demod -a" whilst trying to get a UDF patch to work stop SPDIF sound? as it's now broke! 

this is etc/modules

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
rtc
sbp2

Any help out there?

---

### Post by mrsteveman1 on 2008-02-12
What happens when you restart?

---

### Post by addisor on 2008-02-12
Yea still No SPDIF sound, normal speaker sound ok, and SPDIF works with 6.10.

Find this strange

rob@rob-desktop:~$ sudo modprobe snd-
FATAL: Module snd_ not found.

---

### Post by mrsteveman1 on 2008-02-12
Whats the chipset in the box?

You might also check in alsamixer, since you said the normal outputs work, perhaps SPDIF is just disabled or muted. In the mixer it will be referred to as IEC 958

---

### Post by addisor on 2008-02-12
alsamixer shows ie958 at full botton, not muted but wont move either.

---

### Post by mrsteveman1 on 2008-02-12
Yea its either on or off in that case, i don't think theres any real volume control for spdif itself (sort of like a line-out).

Since your analog outputs work there shouldn't be anything wrong with the modules or the driver, it just sounds like the mixer isnt directing the output correctly.

Might be worth checking lsmod for any of the loaded sound modules, and perhaps also dmesg to see what the kernel is saying about the device.

---

