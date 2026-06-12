---
title: "Wifi broke after updates"
date: 2010-11-27
forum: Networking &amp; Wireless
---

### Post by harris.sw on 2010-11-27
In a previous post 

[U][http://ubuntuforums.org/showthread.php?t=1618554](http://ubuntuforums.org/showthread.php?t=1618554) 

[/U]I got help getting wifi working on a Toshiba laptop with 10.10.  After an update came through and I applied it (I believe it was a linux kernel update or generic headers update) wifi stopped working.

I followed the steps in the post to re-create the driver but this time it doesn't work.  So 2 questions:
1. How to re-create the driver after this update?
2. How to prevent this from happening again?  So that another update doesn't make the driver not work?

Thanks for any help!
Steve[U]
[/U]

---

### Post by MooPi on 2010-11-27
The install process will need one extra step.
```
make clean
make
sudo make install
```
Try that and post back if it works.

---

### Post by harris.sw on 2010-11-27
That did it!  Thanks so much!

---

