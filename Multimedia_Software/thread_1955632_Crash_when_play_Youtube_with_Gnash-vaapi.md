---
title: "Crash when play Youtube with Gnash-vaapi"
date: 2012-04-09
forum: Multimedia Software
---

### Post by nam228 on 2012-04-09
Hi all,
I have proplem when i play Youtube with gnash-vaapi from Spilited-desktop
*[http://www.splitted-desktop.com/static/libva/gnash-vaapi/old/](http://www.splitted-desktop.com/static/libva/gnash-vaapi/old/)*
-----
THis is command in terminal

root@localhost:/opt/gnash/vaapi-agg/bin#./gtk-gnash  [http://www.youtube.com/v/Gq8wMRtog1A](http://www.youtube.com/v/Gq8wMRtog1A)

** (gtk-gnash:6834): WARNING **: Couldn't find pixmap file: GnashG.png
libva: libva version 0.31.0-sds4
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers//xvba_drv_video.so
libva: va_openDriver() returns 0
[GnashVaapi] VA API version 0.31

------
then when i click buton to play video,its crash and show error to terminal :

[GnashVaapi] VA API version 0.31
gtk-gnash: ../../backend/Renderer_agg.cpp:521: void gnash::<unnamed>::EmptyVideoRenderer<PixelFormat>::renderScanlines(agg :: path_storage&, agg :: renderer_base<PixelFormat>&, Scanline&) [with Scanline = agg:: scanline_p8, PixelFormat = agg:: pixfmt_alpha_blend_rgba<agg:: blender_rgba_pre<agg::rgba8, agg:: order_bgra>, agg::row_accessor<unsigned char>, unsigned int>]: Assertion `span->len > 0' failed.
Aborted

------
this is my vainfo
#vainfo
libva: libva version 0.31.0-sds4
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers//xvba_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA API version: 0.31
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA API - 0.6.3
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :    VAEntrypointIDCT
      VAProfileMPEG2Main              :    VAEntrypointIDCT
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointVLD
----
how to fix it ,pls help me

---

