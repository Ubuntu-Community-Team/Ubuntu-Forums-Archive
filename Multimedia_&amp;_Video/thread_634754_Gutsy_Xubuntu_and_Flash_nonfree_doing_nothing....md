---
title: "Gutsy Xubuntu and Flash nonfree doing nothing..."
date: 2007-12-08
forum: Multimedia &amp; Video
---

### Post by D351 on 2007-12-08
So, I installed Flash-nonfree... but when I go to flash sites, firefox just asks me to install a plugin again. And if I choose flash-nonfree as my option again, it tells me that it's already installed. The plugin appears to be doing nothing at all. Is there something important I'm missing here?

---

### Post by Yellow Pasque on 2007-12-08
Probably the md5sum issue if you downloaded recently.
[http://ubuntuforums.org/showthread.php?t=634404](http://ubuntuforums.org/showthread.php?t=634404)

---

### Post by D351 on 2007-12-08
Thanks. I only wish I'd found that before making this thread...

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

### Post by Yellow Pasque on 2007-12-08
> **daradib said:**
> If you have 64-bit Ubuntu, you currently need to build a binary package from this source package: 

Not quite. Adobe doesn't offer source to build or native 64-bit, so you have to use nspluginwrapper to make the 32-bit library compatible (see the Flash threads in the 64-bit forum).

---

### Post by daradib on 2007-12-08
> **Temüjin said:**
> Not quite. Adobe doesn't offer source to build or native 64-bit, so you have to use nspluginwrapper to make the 32-bit library compatible (see the Flash threads in the 64-bit forum).

The Ubuntu package (which is what is being built- not an Adobe package, sorry if I was misunderstood) automagically takes care of the nspluginwrapper stuff. The Ubuntu package contains nothing other than instructions to download the installer from Adobe's site. When compiled for 64-bit, it also takes care of nspluginwrapper.

---

### Post by daradib on 2007-12-08
This is the built package. I recommend that you build the packages yourself, however, because you should exercise caution when downloading a random package (the source package is trusted as it is from an included Hardy source package) since that lets anything be executed that the creator of the package made (and possibly malicious).

---

### Post by daradib on 2007-12-10
For more information on this bug, see [http://ubuntuforums.org/showthread.php?p=3929669](http://ubuntuforums.org/showthread.php?p=3929669)

---

### Post by JoePits on 2007-12-15
> **daradib said:**
> This is the built package. I recommend that you build the packages yourself, however, because you should exercise caution when downloading a random package (the source package is trusted as it is from an included Hardy source package) since that lets anything be executed that the creator of the package made (and possibly malicious).

thanks mate, used your build. was gonna do it myself with that 64 bit source thing that was posted but i trust you even though you told me not to.

---

