---
title: "flashplugin-nonfree vs adobe-flashplugin"
date: 2009-01-01
forum: Multimedia Software
---

### Post by brjoon1021 on 2009-01-01
I was just wondering which works better....   I noticed that one is Flash 9 and the other is Flash 10. I use Firefox

---

### Post by sasha1024 on 2009-03-15
The flashplugin-nonfree package is located in the ubuntu repository (ubuntu.com/multiverse),
while the adobe-flashplugin is located in the external repository (archive.canonical.com/partner).

The flashplugin-nonfree is somewhat "unusual" package: when you start installing it, it initiates a download from [www.adobe.com;](www.adobe.com;) but no files are contained directly inside the package.
On the other hand, the adobe-flashplugin is a "regular" package of size ~3.7 MB, which actually contains the flash plugin inside.

Thus, "unusual|downloader" flashplugin-nonfree is located in the primary repository, and the "regular" adobe-flashplugin is contained in external repository.
I don't know why they did like that. Just some my stupid assumption:
a) Long-ago they were not sure whether adobe license allows to include the plugin directly into package, so they created "unusual" flashplugin-nonfree.
b) Relatively-recently they created the "regular" adobe-flashplugin; but it's yet experimental and without 64bit support, so the older one is still in repository.

Which one to use -- your choice :). See also [http://ubuntulinuxtipstricks.blogspot.com/2008/12/adobe-flash-avoiding-md5-errors.html](http://ubuntulinuxtipstricks.blogspot.com/2008/12/adobe-flash-avoiding-md5-errors.html)

---

### Post by gandaran on 2009-03-15
--------

---

