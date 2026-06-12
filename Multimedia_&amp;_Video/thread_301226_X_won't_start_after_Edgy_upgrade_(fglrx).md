---
title: "X won't start after Edgy upgrade (fglrx)"
date: 2006-11-16
forum: Multimedia &amp; Video
---

### Post by dgm on 2006-11-16
Hello. I've been using Ubuntu Dapper for awhile now. I had 3d acceleration working perfectly well with the ATI drivers until I decided to upgrade to Edgy. Now, when I try to start X, it complains that it can't load the "fglrx" module, because "module abi major version (0) doesn't match the server's version (1)". My xorg.conf has remained untouched, so that's not the issue. I've been trying to get this so work for awhile now, with no luck. ](*,) Any help would be greatly appreciated.

Regards,
dgm

---

### Post by Joe_CoT on 2006-11-16
Make sure you have the ubuntu-desktop package installed. the video driver packages all changed, and they aren't reflected if you don't have the metapackage.

fyi, just gave the same response in [this post](http://ubuntuforums.org/showthread.php?t=301238). In other words, the upgrade broke lots of people who didn't have their metapackage.

---

### Post by dgm on 2006-11-16
I HAVE ubuntu-desktop installed. So the lack of ubuntu-desktop is not the issue. By the way I installed my ATI drivers from download, not from a script.

---

### Post by Joe_CoT on 2006-11-16
> By the way I installed my ATI drivers from download, not from a script.

Well there ya go.

```
sudo nano -w /etc/default/linux-restricted-modules-common
```

add fglrx to DISABLED_MODULES, restart. you may need to reinstall your downloaded driver.

---

### Post by dgm on 2006-11-16
fglrx was already in there. I had already tried reinstalling. This is incredibly exasperating.

---

### Post by Joe_CoT on 2006-11-16
Well, then you're running the wrong version of the driver.  Are you sure you're running an xorg 7.1 compatible version of fglrx? Have you tried just using the [ATI package](http://ubuntuforums.org/showthread.php?t=255929) that tseliot maintains?

---

### Post by dgm on 2006-11-17
I followed a method just like this one for installing my drivers:

[http://ubuntuforums.org/showthread.php?t=204910](http://ubuntuforums.org/showthread.php?t=204910)

I'm just worried that this method is confusing something when I'm trying to install from .deb... Is there anything I need to do other than using dpkg to remove the xorg-driver-fglrx package?

---

### Post by Joe_CoT on 2006-11-17
Yes, but notice the date on those :-| Those are probably for Dapper, which is xorg 7.0; Edgy is 7.1, hence the error. Try tseliot's.

---

### Post by dgm on 2006-11-18
Tseliot's don't work either... ](*,)

---

### Post by GeBo on 2006-11-18
I have an GeForce, but had the same problem! Maybe my solution is yours. As root type:
**dpkg-reconfigure xserver-xorg**
and make the appropriate selections. After that enable the graphics driver (if not already done) and start gdm (or kdm or xdm). Worked for me.

---

