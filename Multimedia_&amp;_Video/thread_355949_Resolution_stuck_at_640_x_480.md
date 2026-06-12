---
title: "Resolution stuck at 640 x 480"
date: 2007-02-07
forum: Multimedia &amp; Video
---

### Post by Ryan8720 on 2007-02-07
Hi everyone,

I'm a first time Linux user.  I just installed Ubuntu today.  I have a 19" widescreen LCD, but the resolution cannot be changed.  The only option is 640 x 480.

The max resolution is 1440 x 900.  I have integrated graphics.  I believe it uses Intel 845GV Graphics.  I have been searching the web for Linux drivers for that chipset, but i can't find anything. Any ideas?

Thanks,
Ryan

---

### Post by pay on 2007-02-07
What version of Ubuntu are you using? In edgy i think the drivers are built in for that chipset but for dapper you might need to install them manually. ```
wget -c http://downloadmirror.intel.com/df-support/8211/eng/dri-I915-v1.1-20041217.i386.rpm
sudo alien dri-I915-v1.1-20041217.i386.rpm
sudo dpkg -i dri-i915_v1.1-20041218_i386.deb
```

---

### Post by Ryan8720 on 2007-02-07
Version 5.04.  It was a CD I got at college.

---

### Post by pay on 2007-02-07
The above steps should be the same for 5.04. Also if you wanted, you could order 6.06LTS for free.

---

### Post by Ryan8720 on 2007-02-08
I typed all the stuff in the terminal, but it didn't seem to do anything. There is still only the 640  400 option for screen resolution.

---

