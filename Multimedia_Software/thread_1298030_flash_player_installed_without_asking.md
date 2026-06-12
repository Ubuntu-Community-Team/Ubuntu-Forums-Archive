---
title: "flash player installed without asking?"
date: 2009-10-22
forum: Multimedia Software
---

### Post by michael.conner on 2009-10-22
How would I find out what package installed npwrapper.libflashplayer.so without me asking for it specifically? I did not install flashplugin-nonfree.

Using Kubuntu Karmic Beta (AMD64). Have only Firefox 3.5.3 installed.

---

### Post by kbielefe on 2009-10-22
The command to tell what package installed a file is:
```
$ dpkg-query -S npwrapper.libflashplayer.so
```That only works if you installed via a package manager.  Flash can sometimes be installed manually (it is on my system).

---

### Post by michael.conner on 2009-10-22
Thanks. Somehow "flashplugin-installer" got run -- must have been when I enabled codecs in Amarok.

---

