---
title: "Adobe-FlashPlugin smoother than FlashPlugin-NonFree in Jaunty?"
date: 2010-01-23
forum: Multimedia Software
---

### Post by Virus666 on 2010-01-23
Hi all,

Yesterday, I was seeking for some Flash Player tweaks for Jaunty. In Adobe's web site I found and installed "**APT for Ubuntu 9.04+**." That move installed **adobe-flashplugin** to the system. After I removed **flashplugin-nonfree** and **flashplugin-installer**, Interestingly flash videos begin to player smoother; especially in [http://www.animefreak.tv/](http://www.animefreak.tv/) . Is it just a coincidence or an advantage of "APT for Ubuntu 9.04+"; because it did not exist in Adobe's website one month ago, just "**.deb for Ubuntu 8.04+**" was available for download.

Internet browser: **Firefox 3.0.17**
adobe-flashplugin version: **10.0.42.34-2jaunty1**
flashplugin-nonfree version: **10.0.42.34ubuntu0.9.04.1** (not installed anymore)

---

### Post by lovinglinux on 2010-01-23
I personally never saw any difference. Some people say the adobe one is better.

---

### Post by Virus666 on 2010-01-31
Thanks for reply. But it seems that in some websites it's beneficial to use Flashblock extension of Firefox. Because, bunch of flash animation in same page just stucks the present video... Thanks again...

---

### Post by efflandt on 2010-02-01
I always thought that flashplugin-nonfree was a transitional version (an older version disguised as a newer version in case you had problems with the newer version), whereas, flashplugin-installer alone (without the nonfree package) was the most recent released Adobe flash version.

If the flashplugin-nonfree package is still using flash 9, that might explain it tripping on sites that require flash 10.  Have you tried flashplugin-installer without installing flashplugin-nonfree?

---

### Post by lovinglinux on 2010-02-01
> **efflandt said:**
> I always thought that flashplugin-nonfree was a transitional version (an older version disguised as a newer version in case you had problems with the newer version), whereas, flashplugin-installer alone (without the nonfree package) was the most recent released Adobe flash version.

If the flashplugin-nonfree package is still using flash 9, that might explain it tripping on sites that require flash 10.  Have you tried flashplugin-installer without installing flashplugin-nonfree?

flashplugin-nonfree is a transitional package that just depends on flashplugin-installer, so it doesn't matter if you install one or the other. When you install flashplugin-nonfree it automatically installs flashplugin-installer, which in fact downloads the most recent version of libflashplayer.so from Adobe. 
BTW, it's not using flash 9. I think the only difference was that the adobe-flashplugin contained the libflashplayer.so file, while the other is a downloader.

---

