---
title: "Newbie - MythTV PVR-150 Lirc Can't get remote to work.  HELP"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by Newbentu on 2007-10-27
This is what I get...Please help!

aaron@blackbox:~$ sudo lircd -n
lircd-0.8.2[6306]: lircd(userspace) ready
lircd-0.8.2[6306]: accepted new client on /dev/lircd
lircd-0.8.2[6306]: could not get file information for /dev/lirc
lircd-0.8.2[6306]: default_init(): No such file or directory
lircd-0.8.2[6306]: caught signal
Terminated



aaron@blackbox:~$ depmod -ae
FATAL: Could not open /lib/modules/2.6.22-14-generic/modules.dep.temp for writing: Permission denied
aaron@blackbox:~$ modprobe lirc_i2c
aaron@blackbox:~$ chmod 666 /dev/lircd
chmod: changing permissions of `/dev/lircd': Operation not permitted
aaron@blackbox:~$ lircd
lircd: can't open or create /var/run/lircd.pid
lircd: Permission denied
aaron@blackbox:~$ irw

---

