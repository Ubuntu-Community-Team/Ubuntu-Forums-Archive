---
title: "the source cannot be read?"
date: 2008-05-05
forum: Multimedia Software
---

### Post by pwntang on 2008-05-05
[SIZE="1"][FONT="Arial"]i'm becoming really really frustrated with the following error message:

[COLOR="DimGray"]'the source can't be read.

maybe you don't have enough rights for this, or the source doesn't contain data (e.g: no disk in drive). (/dev)(/dvd)'[/COLOR]

at first it thought it was a problem with the disk, so i changed it, but the message was the same. i switched DVD drives, but the error message was still the same. 
i'm a **complete** n00b to ubuntu so i really have no idea what i'm doing, and ANY help would be muchly appreciated.

[/FONT][/SIZE]

---

### Post by ajmorris on 2008-05-06
hey there,
you may not have permission to the cd/dvd drive. You can edit your /etc/fstab file as root, and add to the options line, for your cdrom drive entry, users . this enables normal users to mount the dvd drive, and use the contents.

AJ

---

