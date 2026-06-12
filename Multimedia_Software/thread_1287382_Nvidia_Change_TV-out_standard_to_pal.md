---
title: "Nvidia: Change TV-out standard to pal"
date: 2009-10-10
forum: Multimedia Software
---

### Post by cyrus_the_virus on 2009-10-10
Hi,

I'm using the nvidia settings program to setup my tv-out in ubuntu 9.04. This usually works great. However, yesterday I connected my laptop to an old tv (which doesn't support NTSC) and the picture was black and white. In windows there is an option to set the tv standard to pal and that solved the problem. But in ubuntu I can't find such an option.

I tried to add this to my /etc/X11/xorg.conf
```
 Option         "TVStandard" "PAL-B" 
```
But after doing that my tv wasn't even recognized anymore by the nvidia-settings tool. I also followed [this]("https://help.ubuntu.com/community/NvidiaTVOut") tutorial (the twinview part) but that didn't work either. I actually used this before on older versions of ubuntu before nvidia setting program was available.

So how can I change the tv-out standard to pal?

---

