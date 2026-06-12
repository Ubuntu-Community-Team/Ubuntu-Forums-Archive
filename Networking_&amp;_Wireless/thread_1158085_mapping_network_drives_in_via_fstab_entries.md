---
title: "mapping network drives in via fstab entries?"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by tonyps on 2009-05-13
Morning,

I am using the latest ubuntu, which by the way is really good!!
I recently added the required entries to map three of the network drives that I frequently use. I logged in this morning, waited a few and none of them mapped.
Checked the fstab file and all entries are the same, no change
When I attempt to manually mount them, via:
sudo mount /media/volumename, I get:
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs

One of the entries in fstab is as follows:
//volume/path  /media/name cifs  username=username,password=password  0  0

Any assistance is greatly appreciated!

Tony ...

---

### Post by Iowan on 2009-05-13
A couple of links:
[How to fstab]("http://ubuntuforums.org/showthread.php?t=283131")
[ Mount Samba shares]("http://ubuntuforums.org/showthread.php?t=288534")

---

