---
title: "Music player help"
date: 2011-07-11
forum: Multimedia Software
---

### Post by l07 on 2011-07-11
VLC does what I want, however, it often freezes up my system so that it's difficult to even kill itself. I have to do a hard reset because while playing something it gets stuck. If there's something I can do to stop that, what is it?

If not, is there a more stable alternative? I don't want to hunt for codecs.

---

### Post by wolfen69 on 2011-07-11
> **l07 said:**
> I don't want to hunt for codecs.

Just do:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
then
```
sudo apt-get install non-free-codecs
```
then any media player will play anything.

---

### Post by l07 on 2011-07-13
Thanks.

---

