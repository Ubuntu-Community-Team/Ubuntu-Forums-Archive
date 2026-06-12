---
title: "DVD doesent run"
date: 2009-06-12
forum: Multimedia Software
---

### Post by Xtreme co on 2009-06-12
Hi im running kubuntu, I have a problem: my machine doesn't want to read a (relatively new) DVD.
It doesn't even find it. The only reason i can think of is that it is copy protected.

thanks

---

### Post by pauna on 2009-06-16
> **Xtreme co said:**
> Hi im running kubuntu, I have a problem: my machine doesn't want to read a (relatively new) DVD.
It doesn't even find it. The only reason i can think of is that it is copy protected.

thanks

If you have never played a commercial DVD on your system you're probably missing the appropriate decoding libraries. See [https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/) for details and instructions.

---

### Post by Mka on 2009-06-16
Install libdvdcss2, libdvdread3 and libdvdnav4 (probably ... and vlc and some w32codecs). You may need medibuntu repositories enabled.

---

