---
title: "need assistant with adobe flash playert 7.10  64bi"
date: 2007-12-06
forum: Multimedia &amp; Video
---

### Post by ameba on 2007-12-06
i

---

### Post by wolfen69 on 2007-12-06
in terminal:
```
sudo aptitude install flashplugin-nonfree
```

before that though, try installing nspluginwrapper.

---

### Post by ameba on 2007-12-06
i

---

### Post by samjh on 2007-12-06
I'm getting that message as well.

Previous install of flash worked fine, but I reinstalled Ubuntu today and can't get flash to work.

---

### Post by Dynaflow on 2007-12-07
I'm setting up a newly-Ubuntuized laptop for a friend, and I've been repeatedly frustrated by that same error message.  I get the same thing whether I'm grabbing the file from Adobe through Synaptic or Add/Remove, or  us iing an installer downloaded directly from Adobe.  Are they tossing out corrupted files for us tonight?  I might alien one of the .rpm files and try to get an install out of that, just to see if the problem is only with the file that Ubuntu grabs by default.

---

### Post by Dynaflow on 2007-12-07
Using a .deb made out of the downloadable .rpm didn't work either, for any of my browsers (Firefox, Opera, Iceape).  It looks like Adobe released a broken plugin again.  What a surprise.  

Does anyone have the link for the older versions?

---

### Post by ameba on 2007-12-07
i

---

### Post by daradib on 2007-12-08
This is a very recent bug, caused by Adobe's update of Flash 9.0 update 3 (9.0.115.0) codename "Moviestar" on December 4th.

[http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html](http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html)

This causes Ubuntu to not install the flash plugin, detecting a change in the flash plugin installer file (via MD5 checksums). See [bug 173890]("http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890"). This bug has been fixed in the next release of Ubuntu (Hardy 8.04) and it should soon come as an update to Ubuntu 7.10.

If you want an immediate fix, do the following.

Using Synaptic Package Manager, remove the package flashplugin-nonfree.

Alternatively, you can run this command in the Terminal (Applications -> Accessories -> Terminal): sudo apt-get remove flashplugin-nonfree

Then just download this package (32-bit only) and install it (it is identical to the current package in the next release of Ubuntu, Hardy 8.04): [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

If you have 64-bit Ubuntu, you currently need to build a binary package from this source package: [http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2](http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2)

---

### Post by daradib on 2007-12-10
For more information on this bug, see [http://ubuntuforums.org/showthread.php?p=3929669](http://ubuntuforums.org/showthread.php?p=3929669)

---

