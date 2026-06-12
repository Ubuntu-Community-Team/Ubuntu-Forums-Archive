---
title: "Ati Mobility Radeon 9000"
date: 2007-02-13
forum: Multimedia &amp; Video
---

### Post by passonno on 2007-02-13
Hello,

I am at my wit's end here in regards to any sort of 3d acceleration.  

My notebook has a Mobility Radeon 9000, and I actually did have it working last year, quite well, until the hard drive died and I went back to XP fulltime.

Now I am all Dapper, so any help would be appreciated.

---

### Post by r4ik on 2007-02-13
Try,

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

or

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck !

---

### Post by passonno on 2007-02-13
thanks for the quick reply, I will try it and report back.

---

### Post by passonno on 2007-02-13
So far nothing.

---

### Post by r4ik on 2007-02-14
Did you try this one ?

[http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html](http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html)

---

### Post by teryan2006 on 2007-02-14
with dapper or edgy, the mobility 9000 should have DRI and 3d accel out of the box with the xorg-video-ati driver. Can you post your xorg.conf?

---

### Post by towsonu2003 on 2007-02-14
ati's proprietary fglrx module doesn't have 3D support for that card afaik... if your xorg.conf has "ati" as the driver, I believe you should have 3D working...

---

