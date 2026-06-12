---
title: "Burn + Verify multiple DVDs simultaneously"
date: 2011-02-17
forum: Multimedia Software
---

### Post by maxim99 on 2011-02-17
I have two USB DVD rewriters and would like to use them to burn different sets of data simultaneously.

I'm not able to do this with the application I love, K3B. It has everything and works beautifully, however doesn't allow me to run multiple instances of it.
```
k3b --nofork &
[2] 7788
maxim@maxim-lt:~$ <unknown program name>(7788)/: KUniqueApplication: Can't setup D-Bus service. Probably already running.
```

As for brasero which "does verification" it does an MD5 sum of the image of the disc and after the burn, does an md5 sum of the disc it burnt and compares. It doesn't even do this well.

I'm looking for another application which I can use at the same time as K3B and also does verification of the disc by comparison to the data itself instead of by proxy of an MD5 check.

Any ideas? I've tried the following which I found to not have verify after burn as a feature, didn't support dvd as a selectable format, or didn't support data sessions (IE: ISO Burn only):
```
GnomeBaker
CD/DVD Creator
Xfburn
Gnome CD Master
```

---

