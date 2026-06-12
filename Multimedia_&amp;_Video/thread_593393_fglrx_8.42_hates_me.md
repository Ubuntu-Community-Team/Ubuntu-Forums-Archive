---
title: "fglrx 8.42 hates me"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by Kazade on 2007-10-27
Hi all,

I've just spent the last 2 hours following every howto I can find on installing the new fglrx driver. No matter what I always end up without DRI and the following messages in the log:

(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(WW) fglrx(0): No DRM connection for driver fglrx.
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *


I've tried everything, I've blacklist fglrx then I even removed the linux-restricted-modules altogether. The above items are the only things in the log that contain warnings or errors.

modprobe fglrx 

doesn't print anything to screen so I assume thats good.

My Xorg.conf is configured using the aticonfig --initial -f command, but I also tried with a working config from the open source drivers just with ati replaced by fglrx.

I've seen loads of posts saying to remove everything to do with fglrx and start again, which I have done about 5 times now.

I've tried this set of commands which I found in a post somewhere:

sudo invoke-rc.d gdm stop
sudo modprobe -r fglrx
sudo rm /lib/modules/`uname -r`/volatile/fglrx.ko
sudo depmod -a
sudo invoke-rc.d gdm start

which didn't work. 

I have a Radeon 9550 and I've never had trouble with any of the previous fglrx drivers. Please can anyone help me?

---

### Post by Kazade on 2007-10-27
I've narrowed the problem down a little. During installation you have to do the following:

sudo depmod -a
sudo ln -s /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko

That symbolic link disappears every time I reboot. I don't know why.

Surely someone must have had the same problem?

---

### Post by wesmo on 2007-10-27
Try re enabling fglrx (after symbolic linking) in restricted driver manager then reboot - I had a similiar prob n it fixed it.

Don't forget to whitelist fglrx if you wan to get compiz working.

---

### Post by Kazade on 2007-10-27
Thanks, you're a lifesaver :)

---

