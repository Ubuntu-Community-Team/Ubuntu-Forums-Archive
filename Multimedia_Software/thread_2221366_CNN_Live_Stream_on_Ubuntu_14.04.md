---
title: "CNN Live Stream on Ubuntu 14.04"
date: 2014-05-01
forum: Multimedia Software
---

### Post by gstanden on 2014-05-01
In case anybody on 14.04 wants to use the CNN live streaming news feed at cnn.com, here is what you need to do.  

First, read this post:  [http://ubuntuforums.org/showthread.php?t=1817571](http://ubuntuforums.org/showthread.php?t=1817571)

That worked for me when I was on earlier version of Ubuntu.  When I upgraded to Ubuntu 14.04, it broke my CNN access again.  It turns out the package HAL is not available in the standard repos for 14.04 and is needed for the CNN and similar type feeds that require this DRM authentication, and moreover the replacement package "hal-info" will NOT work for this purpose.

You'll need to do the following to get HAL from a repo that is maintained solely for getting HAL in later versions of Ubuntu.

sudo add-apt-repository ppa:mjblenner/ppa-hal
sudo apt-get update && sudo apt-get install hal

Close all Firefox browser windows.  Then run (as before from above post 1817571) same steps:

cd ~/.adobe/Flash_Player
rm -rf NativeCache AssetCache APSPrivateData2

Restart Firefox and login to CNN live stream successfully.

BIG UPS and thanks to Michael Blennerhassett for his work maintaining HAL here:  ( [https://launchpad.net/~mjblenner/+archive/ppa-hal](https://launchpad.net/~mjblenner/+archive/ppa-hal) )

More information here about multimedia sites proteced by DRM to which the above steps enable access:  [http://linuxg.net/how-to-enable-the-playback-of-flash-content-protected-by-drm/](http://linuxg.net/how-to-enable-the-playback-of-flash-content-protected-by-drm/)

Hope this Helps!  We do need our so-called news...

---

### Post by ron998 on 2014-05-01
> **gstanden said:**
> ...Hope this Helps!  We do need our so-called news...

Hi
Thanks.
This is needed for channel4.com in UK.
Or else error message is...
**A Digital Rights error (3322) has occurred**

(I remember now, I had to install hal from the repo with Ubuntu-12.04)

:cool:

---

