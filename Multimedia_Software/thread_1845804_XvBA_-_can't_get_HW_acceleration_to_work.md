---
title: "XvBA - can't get HW acceleration to work"
date: 2011-09-17
forum: Multimedia Software
---

### Post by Tarmael on 2011-09-17
Hi all,

I (stupidly) bought [this]("http://www.gigabyte.com/products/product-page.aspx?pid=3681#ov") without knowing that there are issues with AMD and hardware acceleration. In fact, I didn't know anything on the topic until after I set that machine up.

My issue is:
[https://launchpad.net/~dtl131/+archive/catalysthacks](https://launchpad.net/~dtl131/+archive/catalysthacks)
installed
[http://www.splitted-desktop.com/~gbeauchesne/xvba-video/](http://www.splitted-desktop.com/~gbeauchesne/xvba-video/)
installed
ln -s /usr/lib/va/drivers/xvba_drv_video.so /usr/lib/dri/fglrx_drv_video.so
which finally gives vainfo a positive output for once
```
libva: libva version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA API version: 0.32
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.8.0
vainfo: Supported profile and entrypoints
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD

```

Yet when I run vlc (Built from the catalysthacks PPA) it gives me the output of:
```
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
Segmentation fault
```
mplayer gives me ```
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1

```

is there a way to specify which driver it's to use before I start it?
Any help?

---

### Post by Tarmael on 2011-09-19
Got it working.

I ended up building libva from git when I realised I had to still install the libva*.deb to cover the mplayer and vlc dependencies (It was easier this way).
So I installed libva, after building from git then linked /usr/local/lib/libva.so.1 to /usr/lib/
bla bla bla, got that working.
vainfo gave me the correct output again.

Then VLC didn't work (Still)
That's when I found out VLC was using libva from /usr/lib32/.
I linked /usr/local/lib/libva to /usr/lib32
AND IT WORKED!


Not great, but it's gone from 90%~50% CPU usage.

---

### Post by Tarmael on 2011-09-29
Update: I got it working flawlessly a few days after my last post using XBMC built from PPA, Libva built from git and splitted desktops xvba driver.

---

### Post by LLMike on 2012-02-09
Hello Tarmael,
 
I tried to send you a PM but I couldn't.
 
I'm new to Ubuntu and I'm using Ubuntu 10.10.
 
I'm trying to use VLC with my E350, but it's not working.
 
I don't know what symbolic links I should do, or if I'm missing some step.
 
Could you please give me some advices?
 
Thanks in advance.
 
That's what I get in my VLC:
 
libva: libva version 0.31.1-sds1
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_openDriver() returns 0
xvba_video: XVBA_GetSurface(): status 2
[0x99762e4] avcodec decoder: Using VA API version 0.31 for hardware decoding.

---

