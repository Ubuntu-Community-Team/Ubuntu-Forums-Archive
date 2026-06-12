---
title: "VLC plays .avi but not DVDs"
date: 2010-08-05
forum: Multimedia Software
---

### Post by DavidVS on 2010-08-05
I don't get many new DVDs, but checked out Stardust from the library recently.

VLC won't play it.  I tried a few old DVDs and it won't play them either.  The DVD's name appears on the bottom left corner momentarily, and then the VLC window returns to its small, initial "waiting for instructions" shape and state.

It plays .avi files without problem.  Any idea what might be wrong?

(Searching has not helped.  Please forgive me if this has been answered but I cannot find it.)

---

### Post by lisati on 2010-08-05
Have a look here: [https://help.ubuntu.com/10.04/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/10.04/musicvideophotos/C/video-dvd.html)

---

### Post by deskman on 2010-08-05
Sorry, has been answered before

---

### Post by DavidVS on 2010-08-06
> **lisati said:**
> Have a look here: [https://help.ubuntu.com/10.04/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/10.04/musicvideophotos/C/video-dvd.html)

Thank you very much!

This was the needed part:

> sudo /usr/share/doc/libdvdread4/install-css.sh

Which confuses me, because when I searched in Synaptic Package Manager for "libdvdcss2" there was no package with that name, but it did bring up the package "ubuntu-restricted-extras" which as already installed.  (I remembered to check *that* much.)

Could that package have been installed but broken, and that Terminal command reinstalled it properly?

---

