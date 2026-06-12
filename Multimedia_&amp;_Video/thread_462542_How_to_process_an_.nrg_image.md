---
title: "How to process an .nrg image"
date: 2007-06-02
forum: Multimedia &amp; Video
---

### Post by Pumalite on 2007-06-02
I have an .nrg image that weights 4.3GB and I don't know how to record it. Any software? Any ideas? I know it's a Nero image but I packed my Windblows XP in an external drive. Any help will be appreciated. I looked at k3b and Acidrip, but, no go.

---

### Post by taurus on 2007-06-02
K3b should be able to burn it.  In the Tools menu, go down to Burn DVD Image and tell it to display all files (from drop out menu at the bottom).  Then, click on .nrg and burn it.

---

### Post by yabbadabbadont on 2007-06-02
Does k3b know how to handle a Nero image file?  It isn't a standard ISO file.

Edit: There is a nerolinux package available from Nero.  I think the demo version will let you burn images.

---

### Post by yabbadabbadont on 2007-06-02
If you have enough disk space, you might try using nrg2iso to convert the image.

```
/home/daffy $ aptitude show nrg2iso
Package: nrg2iso
State: not installed
Version: 0.4-1.1
Priority: optional
Section: universe/otherosfs
Maintainer: Misha Nasledov <misha@debian.org>
Uncompressed Size: 65.5k
Depends: libc6 (>= 2.3.4-1)
Description: Extracts ISO9660 data from Nero ".nrg" files
 This extracts the ISO9660 CD image data from Nero  ".nrg" files.

```
I don't know if it will work on a DVD image though.

---

