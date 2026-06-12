---
title: "Sound problem 10.04"
date: 2010-05-19
forum: Multimedia Software
---

### Post by sjweinberg on 2010-05-19
Hello.

I recently upgraded to 10.04 and everything has been fine for a while, but just a few days ago I started having sound issues.

Basically, I hear the usual drum beats when the login screen comes up, but once I log in, there is no sound anymore.

I've tried playing around with alsamixer with no luck...

Any ideas?

Thanks.

---

### Post by lidex on 2010-05-20
Need some info to proceed. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Also helpful is the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by DanCar on 2010-05-20
Try the procedures in this post:
[http://ubuntuforums.org/showthread.php?t=1488403](http://ubuntuforums.org/showthread.php?t=1488403)

---

