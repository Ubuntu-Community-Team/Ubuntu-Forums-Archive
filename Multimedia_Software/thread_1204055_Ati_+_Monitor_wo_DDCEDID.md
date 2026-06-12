---
title: "Ati + Monitor w/o DDC/EDID"
date: 2009-07-04
forum: Multimedia Software
---

### Post by der_hede on 2009-07-04
Hi,

I'm using an uncommon constellation of a newer ATI Card with the proprietary fglrx driver and two old crt monitors. One of them is cabled via bnc and has no DDC/EDID capabilities. Since Ubuntu 9.04 it's no longer possible to get refresh rates above 60Hz. I tried everything including modeline settings in xorg.conf and amdcccle. Nothing worked.

Then I found some little post somewhere in the fedora forums ([http://forums.fedoraforum.org/showthread.php?p=1205586](http://forums.fedoraforum.org/showthread.php?p=1205586)). I had to disable XRandR support. I want to spread it here:

Add either in xorg.conf: 
```

Section "Device"
        Driver      "fglrx"
        option      "EnableRandR12" "false"
        [...]
EndSection

```
or in the file /etc/ati/amdpcsdb in the section
```

 [AMDPCSROOT/SYSTEM/DDX]

```
add
```

 EnableRandR12=Sfalse

```

Now modelines in xorg.conf are recognized, hey, 100Hz is so much better than the flickering 60Hz :-)

Some Ati guy should add this to the Documentation (/usr/share/doc/xorg-driver-fglrx/configure.html)

---

