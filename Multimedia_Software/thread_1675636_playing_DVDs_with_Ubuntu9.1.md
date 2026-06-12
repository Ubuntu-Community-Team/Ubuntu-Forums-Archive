---
title: "playing DVDs with Ubuntu9.1"
date: 2011-01-25
forum: Multimedia Software
---

### Post by CompuTom on 2011-01-25
How can I play DVD movies with Ubuntu9.1? I had it working at one time and wiped my harddrive reinstalling Ubuntu9.1. Even with VLC I can't watch a movie. Please help!

---

### Post by johntaylor1887 on 2011-01-26
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
then
```
sudo apt-get install libdvdcss2
```

---

### Post by CompuTom on 2011-01-26
Thank you! That worked wonderfully well.:popcorn:

---

