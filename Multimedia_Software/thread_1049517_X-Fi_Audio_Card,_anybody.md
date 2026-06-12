---
title: "X-Fi Audio Card, anybody?"
date: 2009-01-24
forum: Multimedia Software
---

### Post by George_S on 2009-01-24
I just installed Ubuntu 8.10 and have an [X-Fi]("http://us.creative.com/products/feature.asp?category=1") Creative audio card. However, there is absolutely no sound coming out of my speakers.

The Creative.com web site does have a [Linux driver]("http://support.creative.com/Products/ProductDetails.aspx?catID=1&CatName=Sound+Blaster&subCatID=208&subCatName=X-Fi&prodID=17791&prodName=PCI+Express+X-Fi+Titanium+Fatal1ty+Pro+Series") (XFiDrv_Linux_Public_US_1.00) which was installed successfully. See attached PNG.

Also, whenever I run audio tests in Sound Preferences, the system crashes and restart is needed (attached PNG).

However, still no sound. Then I went through the steps listed in one of the [stickies]("http://ubuntuforums.org/showthread.php?t=205449") and it turned out that ALSA [doesn't support X-Fi]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs") card.

In other words, this code yields nothing:
```
sudo modprobe snd-emu20k1
```

Since emu20k1 is still not officially supported, is there any workaround rot this problem?

Thanks,
George



I went through the steps listed in one of the stickies and discovered

---

### Post by markbuntu on 2009-01-26
If you are having problems getting your Creative X-FI card to work you can try the newest driver from creative, it seems to actually work for some people:

[http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)

Or you can switch to OSS4:

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

[http://ubuntuforums.org/showthread.php?t=780961](http://ubuntuforums.org/showthread.php?t=780961)

Or you can recompile your kernel and apply a patch (take extreme care doing this, recompiling a kernel is serious business and can seriously break your system, do not do this unless you are absolutely sure you know what you are doing):

[http://ubuntuforums.org/showpost.php...&postcount=675](http://ubuntuforums.org/showpost.php...&postcount=675)

---

