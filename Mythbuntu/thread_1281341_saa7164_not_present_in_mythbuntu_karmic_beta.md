---
title: "saa7164 not present in mythbuntu karmic beta"
date: 2009-10-03
forum: Mythbuntu
---

### Post by Caysho on 2009-10-03
Needed for HVR-2200/2250 tuner support.

```

find / -name saa7164*

```
does not find anything.

According to this [PULL request]("http://www.gossamer-threads.com/lists/linux/kernel/1124948"), it and associated drivers are in the kernel tree as of 2.6.31.

I do not know what other drivers are missing.

---

### Post by Caysho on 2009-10-04
Looks like it missed 2.6.31 and made it into 2.6.32, so unless it gets backported, this mythbuntu release will not have support.

---

### Post by Caysho on 2009-10-24
Just trying the mythbuntu Karmic RC and compiling support for this card.
I was getting this type of error when compiling from the linuxtv hg source:
```

 ... error:  implicit declaration of function 'hpsb_unregister_protocol' ...

```

There is an issue with the firedtv source - the compilation stops and most of the modules do not get built.  The fix is to [remove the firedtv module from the selection]("http://www.mail-archive.com/ubuntu-devel-discuss@lists.ubuntu.com/msg09422.html").  Do a 'make menuconfig' and go hunting.

Then the modules compile and can be installed.

---

