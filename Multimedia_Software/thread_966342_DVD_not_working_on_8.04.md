---
title: "DVD not working on 8.04"
date: 2008-11-01
forum: Multimedia Software
---

### Post by Lenny212 on 2008-11-01
Hi, I have read all the posts to fix issue whereby DVDs don't play properly. Unfortunately the fixes are all for versions earlier than 8.04.
I cannot download libdvdcss2 or ws32codecs.
How do I get my DVDs to play?
Your help would be greatly appreciated.

I have installed MPlayer, VLC as well as the standard Totem.

---

### Post by xc3RnbFO8P on 2008-11-01
In Terminal:
> sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) --output-document=/etc/apt/sources.list.d/medibuntu.list
> sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
> sudo apt-get install libdvdcss2
> sudo apt-get install w32codecs

---

