---
title: "vainfo fails on brand-new install"
date: 2010-11-05
forum: Multimedia Software
---

### Post by bsmith1051 on 2010-11-05
Fresh Ubuntu 10.10 (AMD64) install on AMD system with ATI 4200 IGP.  No problem with install and then used 'Additional Drivers' to install the proprietary ATI 10.10 driver.  But now 'vainfo' reports an error:
```
libva: libva version 0.31.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit
```
After a little research I found about the need for the 3rd-party xvba and installed 'xvba-video_0.7.6-1_amd64.deb'.  But it's the exact same error.

So, is there something wrong with the included version of 'libva1' from Ubuntu?  Or, with the way the 'Additional Drivers' utility installs the ATI driver?

---

### Post by bsmith1051 on 2010-11-05
Aha!  I finally made *some* progress, thanks to KleeWho and ridewithstyle over in this thread, [http://ubuntuforums.org/showthread.php?p=10077666](http://ubuntuforums.org/showthread.php?p=10077666)
___________

I had tried/failed to 'update' the included libva1 with the ones provided by splitted-desktop but Synaptic complained that the current file was newer.  Then, from that other thread, I learned I could do the following:

1. uninstall 'vainfo' (since the alternate 'libva1' included it's own copy)
2. force install the alternate 'libva1' using this command-line,
 > sudo dpkg -i libva1_0.31.1-1+sds4_amd64.deb

Note: this alternate appears to be a newer version (0.31.1 vs 0.31.0) but is dated 7/13/10.

Now my vainfo reports;
```
libva: libva version 0.31.1-sds1
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA API version: 0.31
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.6
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :	VAEntrypointIDCT
      VAProfileMPEG2Main              :	VAEntrypointIDCT
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD
```
VLC still reports "unable to open va-api" and is not using hw-accel, but at least I'm making progress?

---

