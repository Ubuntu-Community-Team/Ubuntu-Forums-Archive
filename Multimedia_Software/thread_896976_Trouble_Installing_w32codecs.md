---
title: "Trouble Installing w32codecs"
date: 2008-08-21
forum: Multimedia Software
---

### Post by PlankEyeWilly on 2008-08-21
I wanted to post this, because I searched for a while and couldnt find any answers.  Once i stumbled upon it i wanted to share my findings.

I am running Hardy Heron and was having trouble getting MP3 and DVD Playback.  I went through serveral HowTo's and kept crashing at the same point.  When I would attempt to install the w32codec, it needed libstdc++5 but couldn't find it.  I tried several different ways of adding the Medibuntu repositories with no luck.  I eventually found the package on a Debian site and installed it, and its dependencies from there. 

[libstdc++5]("http://debian.oregonstate.edu/debian/pool/main/g/gcc-3.3/libstdc++5_3.3.6-15_i386.deb")
[gcc-3.3]("http://debian.oregonstate.edu/debian/pool/main/g/gcc-3.3/gcc-3.3-base_3.3.6-15_i386.deb")

Once those were installed, I just added w32codec from a terminal prompt and was done!

```
sudo apt-get install w32codecs
```

---

### Post by Stemp on 2008-08-21
Both libstdc++5 & gcc-3.3 are in the Universe repository.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

