---
title: "I am having trouble getting Ubuntu 11.10 to play DVDs"
date: 2011-11-14
forum: Multimedia Software
---

### Post by Mick8882003 on 2011-11-14
I am trying to install the codecs, but the URL times out, Help please!

Mick

---

### Post by lukeiamyourfather on 2011-11-14
Are you using this guide?

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

What do you mean the URL times out? The guide, the repositories, something else?

---

### Post by Mick8882003 on 2011-11-14
The second terminal command stalls on:

> Connecting to packages.medibuntu.org|42.1.14.11|:80...

---

### Post by MoreOrLess on 2011-11-14
Do it the old-fashioned way: [http://packages.medibuntu.org/oneiric/libdvdcss2.html](http://packages.medibuntu.org/oneiric/libdvdcss2.html)
Download the appropriate file, cd to the place you downloaded it, and:
```
sudo dpkg -i *filename*
```

---

### Post by Mick8882003 on 2011-11-14
That got it, thanks heaps.

---

