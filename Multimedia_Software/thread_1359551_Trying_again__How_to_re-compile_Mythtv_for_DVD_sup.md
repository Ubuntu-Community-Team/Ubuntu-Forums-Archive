---
title: "Trying again:  How to re-compile Mythtv for DVD support"
date: 2009-12-19
forum: Multimedia Software
---

### Post by ronklob on 2009-12-19
Hi all, 

I still need [_this problem_]("http://ubuntuforums.org/showthread.php?t=1346894") fixed.  Is there a way to recompile Mythtv to just add DVD support, and install without fouling up the already installed parts that work fine?  Or will I need to completely start from scratch?

If this is possible, please put in as much detail as possible, I'm still learning.  

Thanks!

---

### Post by HappyFeet on 2009-12-19
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
then
```
sudo apt-get install libdvdcss2
```

---

### Post by ronklob on 2009-12-20
Thanks, but the problem isn't with DVD access in Ubuntu, but DVD support in Mythtv.  I can watch, rip, transcode, etc. any DVD just fine in Ubuntu, but can't do any of it in Myth.

I have all of the 'unsupported' DVD libraries installed.

---

