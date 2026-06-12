---
title: "Handbrake"
date: 2014-07-22
forum: Multimedia Software
---

### Post by UncleMonty on 2014-07-22
Handbrake, appears to only offer mkv as format for videos and dvd rips. I am using ubuntu 14.04. Is there anything I can do change the output to another format?

---

### Post by zteam2 on 2014-07-22
The handbrake version offered from the official repositories is restricted in what formats it can convert to because it uses a modified version of a library other than what is available in Ubuntu / Debian repo.

This can be seen if one reading the package description:


> This version of handbrake has been modified for inclusion in Debian.
 It does neither support audio encoding to AAC via faac nor MP4 format
 muxing via libmp4v2, it falls back to the MKV format instead.


You can get the unrestricted version right here:

[http://handbrake.fr/](http://handbrake.fr/)

---

### Post by SeijiSensei on 2014-07-22
Or you can use [John Stebbins PPA]("https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-snapshots"):
```

sudo apt-get remove --purge handbrake handbrake*
sudo add-apt-repository ppa:stebbins/handbrake-snapshots
sudo apt-get update
sudo apt-get install handbrake-gtk

```
Stebbins maintains a more stable repository, [handbrake-releases]("https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-releases"), but there is no version there for Trusty.  You can use the version for Raring, but you need to [futz]("http://ubuntuforums.org/showthread.php?t=2233332&p=13068142&viewfull=1#post13068142") with the entry in /etc/apt/sources.list.d/.  I'm using the "snapshots" version for Trusty, and so far it's worked fine.

---

### Post by sp40140 on 2014-07-23
+1 for Stebbins' snapshots ppa for daily builds. Been using it for couple years without any issues.

---

