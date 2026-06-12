---
title: "Parole problem in Xubuntu"
date: 2011-12-01
forum: Multimedia Software
---

### Post by M_Mynaardt on 2011-12-01
Hi all!

I tried to test Parole with an old WMV file that's safe and harmless.  But I got an error message to the effect
> Advanced Streaming format demuxer plugin needed for Parole Media Player

Anyone know how to fix that?

Thanks in advance!
8)

---

### Post by MoreOrLess on 2011-12-01
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

That should install gstreamer-ugly package, which has the asfdemuxer (Parole uses gstreamer).

---

### Post by M_Mynaardt on 2011-12-01
> **MoreOrLess said:**
> [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

That should install gstreamer-ugly package, which has the asfdemuxer (Parole uses gstreamer).

That did the trick!  The links to install that package did _not_ work.  However, the instructions to do so manually worked just fine.  If anyone else needs this; do the following:

```
~$ sudo apt-get install ubuntu-restricted-extras
```

Thanks for that, *MoreOrLess*!
:)

---

