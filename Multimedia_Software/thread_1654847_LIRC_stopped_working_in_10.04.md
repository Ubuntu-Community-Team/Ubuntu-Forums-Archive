---
title: "LIRC stopped working in 10.04"
date: 2010-12-28
forum: Multimedia Software
---

### Post by StanleyBE on 2010-12-28
The past year i have used a Philips MCE remote in combination with a first gen Asrock ION system on my Ubuntu install, mainly for XBMC.

I recently upgraded to the latest Ubuntu (10.10). Suddenly the remote stopped working -not immediately after the upgrade, but without an evident cause.
Having read about inclusion of lirc in the kernel of 10.10 and some problems being caused by that, after some hours of trying to get it fixed, I decided to make a clean 10.04 install, since I never had problems on that version. (For the record, I kept my home partition.)

At first, everything was smooth again. But now the remote doesn't work in 10.04 either. I'm pretty sure I have the right config files, since they worked for me earlier.

```
mode2 -d /dev/lirc0
```
could not open /dev/lirc0
default_init(): Permission denied

```
mode2 -d /dev/lircd
```
no error, but remote input does not show

```
sudo mode2 -d /dev/lirc0 
```
This works!

```
irw /dev/lirc0
```
connect: Permission denied

```
irw /dev/lircd
```
no error, but remote input does not show

```
sudo irw /dev/lirc0
```
connect: Connection refused


Any ideas?

---

