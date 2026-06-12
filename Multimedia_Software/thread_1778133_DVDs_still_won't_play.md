---
title: "DVDs still won't play"
date: 2011-06-08
forum: Multimedia Software
---

### Post by tcamdg on 2011-06-08
I've installed libdvdcss2 ([using these instructions]("http://www.dreamingisdigital.com/2011/05/13/how-to-play-dvds-in-ubuntu-11-04/")), but still can't play encrypted DVDs. It appears to be an encryption thing, because I can play backed-up/decrypted DVDs.

I'm using Ubuntu 11.04, 64 bit.

Another user here got it working by installing Ubuntu from scratch, then going straight to install medibuntu and libdvdcss, but that's not a realistic option for me at this point.

Thanks!

---

### Post by wolfen69 on 2011-06-08
Give the medibuntu way a shot.
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
then
```
sudo apt-get install libdvdcss2
```
can't hurt.

---

