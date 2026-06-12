---
title: "how to run xawtv on ubuntu 7.10"
date: 2007-11-09
forum: Multimedia &amp; Video
---

### Post by yinglcs2 on 2007-11-09
Hi ,

i am trying run xawtv on ubuntu 7.10. 

But I get the following error:

Can you please tell if I need DGA support for my X-Server?
And if ubuntu works with Hauppauge 950 tv card?



This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.22-14-generic)
WARNING: Your X-Server has no DGA support.
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available

---

### Post by five_13 on 2008-02-08
i get exactly the same output on an amd64 platform with fglrx drivers (ati radeon xpress 1100)

---

### Post by Dandeloreon on 2008-02-08
I think the issue is how the Hauppaunge WinTV HVR 950 is configured, please look over at linuxtv for details [more details on it's linux support..](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950)

---

