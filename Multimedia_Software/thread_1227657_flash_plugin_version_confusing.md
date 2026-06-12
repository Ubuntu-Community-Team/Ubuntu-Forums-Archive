---
title: "flash plugin version confusing"
date: 2009-07-30
forum: Multimedia Software
---

### Post by d4v1dv00 on 2009-07-30
hi there,

this morning got an update of adobe-flashplugin package version 10.0.32.18-1jaunty but under my Firefox the version still 10.0.22.87 and when i check using synaptic package manager, the flashplugin-nonfree still the lower version.

What should i do?

---

### Post by Intrepid Ibex on 2009-07-31
flashplugin-nonfree and adobe-flashplugin are different: [http://ubuntulinuxtipstricks.blogspot.com/2008/12/adobe-flash-avoiding-md5-errors.html](http://ubuntulinuxtipstricks.blogspot.com/2008/12/adobe-flash-avoiding-md5-errors.html).

you should just have the other one. if you have only adobe-flashplugin, did you reboot ff?

---

### Post by jetpeach on 2009-08-01
i have this issue as well, i'm guessing it's going to be common for many people. here's what i'm trying:
remove flashplugin-installer and flashplugin-nonfree
make sure the third party repo is enabled
install adobe-flashplugin if it's not already installed
delete all occurances of libflashplugin.so except that within the /usr/lib/adobe-flashplugin/ directory
gonna restart firefox and see if it fixes it.

ok, after restarted firefox it at first complained that there was no flash installed. then i closed firefox, re-installed the adobe-flashplugin and this time flash works and is the newest version. problem fixed for me...

---

