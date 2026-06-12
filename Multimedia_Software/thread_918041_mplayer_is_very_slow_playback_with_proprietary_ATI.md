---
title: "mplayer is very slow playback with proprietary ATI driver ?"
date: 2008-09-12
forum: Multimedia Software
---

### Post by Yumyai on 2008-09-12
Hi.

I don't know why but after install proprietary driver  (via system -> administration -> hardware driver), the video playback of mplayer got alot slower ( I didn't test on every video, most of my video is divx, xvid file if that help) .  Everthing fine again after I uninstall driver.

This kinda bother me for awhile, can't use the driver if I want video to play perfectly fine. Any solution would be really appreciated.  Thanks

---

### Post by markbuntu on 2008-09-12
The ati driver in the repository is not the latest driver from ati and neither is the one from envy. They both lack support for the newer ati cards and are missing a number of fixes and enhancements. It is also probable that the driver has been misinstalled and so has reverted to mesa and indirect rendering. This will cause a vast slowdown in performance.

If you want to try the latest ati driver you can follow the directions here, Method 2. This is especially critical if you are using 64bit hardy:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

The release notes for the driver are here:

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_88_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_88_linux.html)

Make sure your card is listed.

---

### Post by Yumyai on 2008-09-13
> **markbuntu said:**
> The ati driver in the repository is not the latest driver from ati and neither is the one from envy. They both lack support for the newer ati cards and are missing a number of fixes and enhancements. It is also probable that the driver has been misinstalled and so has reverted to mesa and indirect rendering. This will cause a vast slowdown in performance.

If you want to try the latest ati driver you can follow the directions here, Method 2. This is especially critical if you are using 64bit hardy:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

The release notes for the driver are here:

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_88_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_88_linux.html)

Make sure your card is listed.

ah thanks, problem solved now.

:)

---

