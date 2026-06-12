---
title: "vaapi hardware acceleration not working for vlc"
date: 2013-06-12
forum: Multimedia Software
---

### Post by JebusWankel on 2013-06-12
I have Radeon HD 6310 with fglrx-updates and xvba-va-driver installed from the standard repos and a slightly newer vlc from a PPA installed.

Here's my output for vainfo:
```
$ vainfo
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD

```

When I try to watch an H.264 / AVC mp4 video with VLC, I get the following output:

```
VLC media player 2.0.7 Twoflower (revision 2.0.6-54-g7dd7e4d)
[0x1c7bb18] [http] lua interface: Lua HTTP interface
[0x1bb0108] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
"sni-qt/21198" WARN  21:38:21.879 void StatusNotifierItemFactory::connectToSnw() Invalid interface to SNW_SERVICE 
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
xvba_video: XVBA_CreateSurface(): status 11
[0x1bf7e68] avcodec decoder error: vlc_va_Setup failed

```

I'm not really sure where the problem is. I had the same errors with the version of vlc that ships with Raring.

What can I do to get this working? My CPU is pretty weak so I really need hardware acceleration.

---

### Post by JebusWankel on 2013-06-12
For no reason I can figure it's working now. The only thing I did was run vlc once with verbose output (-v flag). How about that.

---

