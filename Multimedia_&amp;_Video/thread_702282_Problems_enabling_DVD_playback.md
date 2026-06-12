---
title: "Problems enabling DVD playback"
date: 2008-02-20
forum: Multimedia &amp; Video
---

### Post by jacktar on 2008-02-20
I have been trying to enable DVD playback by following the guides on the forum but I can't get past this problem -


The following packages have unmet dependencies.
  libdvdcss2: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is to be installed
  w32codecs: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is to be installed
E: Broken packages

I re-installed libc6 but the same version was installed. How do I get the right version of libc6 and install libdvdcss2 ?

---

### Post by erginemr on 2008-02-20
Are you sure you are using the correct repository for Feisty, not for Gutsy:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by jacktar on 2008-02-20
Yes, I selected the 7.04 source.

---

### Post by jacktar on 2008-02-20
You may have been right. I re-installed medibuntu an I now have both libc6 and libdvdcss2 installed.
However, Totem still says I don't have the appropriate plug-ins and VLC shows nothing at all.

Correction - VLC now working

---

### Post by erginemr on 2008-02-20
For totem, you may also need to download and install gstreamer-plugins-ugly and -bad from Synaptic.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

