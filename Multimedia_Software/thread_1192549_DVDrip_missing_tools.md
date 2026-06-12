---
title: "DVDrip missing tools"
date: 2009-06-20
forum: Multimedia Software
---

### Post by Herstjori on 2009-06-20
Hi guys I just installed dvdrip from the sudo apt-get dvdrip it seemed to intall fine but when I go to use it it says I am missing the following mandatory tools

ImageMagick    not installed
xvid4conf      not installed
rar            not installed

A) how do I get these tools?
B) why were they not included?

---

### Post by starcraft.man on 2009-06-20
Hmmmmmmmmmmmmm, never really had trouble installing dvdrip. Good program btw, just wish it did x264. 

I'm not sure why imagemagick didn't install, that I know is a dependancy in the regular repos. xvid4conf, I think that's in the multiverse, check that you have that enabled on the software sources page (System > Admin > Software sources), it's on the first page and check all boxes except source code. After that you can simply install those two packages separately by opening a terminal in the accessories section of applications and putting in the following code then enter :

```
sudo aptitude install imagemagick xvid4conf rar unrar
```

There shouldn't be any problems then. I thought the multi repos were on by default, maybe I'm wrong. Oh and the rar thing isn't a big deal I don't think, just for subs.

---

### Post by Herstjori on 2009-06-21
Thanks Starcraft.man that worked

---

