---
title: "Some ATI advice before I attempt to get dual displays working"
date: 2006-07-15
forum: Multimedia &amp; Video
---

### Post by terryc on 2006-07-15
Hi All, 
I have a clean install of dapper and I have updated it.
I have an ATI 8500 Radeon and 2 19" BenQ FP991 lcd displays.
Each time I have attempted to setup ubuntu in the past I have ended up having to go back to windows because I screw up ubuntu.

So, what is the general path to take to get dual displays going?

Thanks for any insight.
Terry

---

### Post by terryc on 2006-07-15
I used the fglrx method documented here;
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
and installed fglrx-control alwell.
After I installed that I went looking for the program and couldn't find it some I ran fireglcontrol instead and it gave me an option to setup the monitors as I want them which went well.  My only problem now is a small ammount of tearing on one of the panels.
HTH
Terry

---

### Post by ltmon on 2006-07-15
I can't get this working properly myself, although it might be because I have a Radeon Mobility X1600 which is only very recently supported by ATI.

Have a quick read of [http://www.phoronix.com/scan.php?page=article&item=480&num=1](http://www.phoronix.com/scan.php?page=article&item=480&num=1) and [http://www.phoronix.com/scan.php?page=article&item=501&num=1](http://www.phoronix.com/scan.php?page=article&item=501&num=1).  They talk about the hidden feature in the new drivers that allow you to dynamically enable and disable a second monitor.

For example I can:
```

aticonfig --enable-monitor lvds,crt1

```
To get an external monitor working (in clone mode only so far, big-desktop causes both monitors to go crazy and I have to do a hard reboot).

To go back to laptop only mode:
```

aticonfig --enable-monitor lvds

```

Cheers,

L.

---

