---
title: "flash MD5 sum failure"
date: 2008-01-05
forum: Multimedia &amp; Video
---

### Post by jej2003 on 2008-01-05
I am trying to install the non free flash plugin and during install I get the following:

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.


Ubuntu says the package was installed correctly, but it does not work.  Any ideas how to fix this?

---

### Post by John.Michael.Kane on 2008-01-05
> **jej2003 said:**
> I am trying to install the non free flash plugin and during install I get the following:

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.


Ubuntu says the package was installed correctly, but it does not work.  Any ideas how to fix this?

This might be of help.
[Bug #173890 flashplugin-nonfree md5 mispatch support thread]("http://ubuntuforums.org/showthread.php?p=3929669")

---

### Post by dsl79 on 2008-01-18
Try removing the nonfree-flash plugin then turn of the ubufox extension 0.4beta1 in firefox extensions. the go visit a site and let firefox reinstall it.

---

### Post by wolfen69 on 2008-01-18
here's the flash fix for firefox:

if you installed flash-plugin, remove before downloading and installing the following flash file.

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb)  then just click and install.

---

