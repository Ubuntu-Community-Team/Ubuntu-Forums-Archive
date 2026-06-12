---
title: "on dapper, installing IVTV causes major crash"
date: 2007-04-10
forum: Multimedia &amp; Video
---

### Post by wildbillnj1975 on 2007-04-10
I am installing the IVTV drivers on a *very clean* dapper system, for use with a Hauppauge PVR-150.  I am following the "official" howto at [https://help.ubuntu.com/community/Install_IVTV_Dapper](https://help.ubuntu.com/community/Install_IVTV_Dapper)

When I reach the step which says:

sudo modprobe ivtv

modprobe crashes, the system is completely frozen.  This is the second attempt - the first resulted in the kernel being so completely hosed that I resorted to a reinstall of ubuntu.  I won't be able to boot into this kernel again.

Anybody know what might be going wrong?  I followed the howto exactly!

After recoving the system (by dumping and re-installing the kernel) I tried it again, this time with :

modprobe -v ivtv

The first two lines are ok.
the third:

insmod /.../modules/2.6.15-28-386/ivtv/ivtv.ko

(I forget the part of the path in the ...)

It spits that out, and completely freezes - no error messages or anything.

Now the system will only boot to an older kernel (same as the first two failed attempts).

---

