---
title: "No luck with lirc/old Dvico Remote"
date: 2008-07-17
forum: Mythbuntu
---

### Post by bigdawgte on 2008-07-17
Finally got my DVICO FusionHDTV3 Gold Q running under Mythbuntu Hardy.  Can't seem to get the remote working at all - selected and installed DVICO USB Remote in Control Centre.  I seem to have the dreaded "irw kills lircd daemon" problem.  When I "sudo lircd -n," and then "irw" I get:

lircd-0.8.3pre1[8659]: lircd(userspace) ready
lircd-0.8.3pre1[8659]: accepted new client on /dev/lircd
lircd-0.8.3pre1[8659]: could not get file information for /dev/lirc
lircd-0.8.3pre1[8659]: default_init(): No such file or directory
lircd-0.8.3pre1[8659]: caught signal
Terminated

Please help.  I don't have a lircc or lirc0 in /dev/usb, only lircd.  Don't know where else to look if symlink is the answer.  Thanks.

---

### Post by bigdawgte on 2008-07-18
Why do my posts in forums so often draw 0 replies.  I must have the internet equivalent of b.o. or bad breath.  But I digress....:)  A little help, please?

---

### Post by bigdawgte on 2008-07-18
O.K. 

Can someone refer me to an appropriate forum with my issue?

Thanks.

---

### Post by dentaku65 on 2008-07-22
Try this (it works on my kubuntu, I don't know for Myth)

```
sudo killall -9 lircd
sudo killall -9 lircmd
sudo killall -9 irexec
sudo killall -9 kaffeine
sudo killall -9 mythfrontend
sudo /usr/sbin/lircd --device=/dev/lirc/0
sudo /usr/sbin/lircmd
irexec &
exit

```

---

