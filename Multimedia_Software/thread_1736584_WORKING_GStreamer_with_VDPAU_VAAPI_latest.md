---
title: "WORKING GStreamer with VDPAU VAAPI latest"
date: 2011-04-22
forum: Multimedia Software
---

### Post by Guzpido Krush on 2011-04-22
Choppy RMVB etc. video on totem made me go _insane_
So i realized mplayer with VDPAU output was rocking and rolling! !!
But Ubuntu uses TOTEM. So I tried to figure out why TOTEM and VLC couldn't do VDPAU.

Lots of users tried with no success, months ago, as I was looking at some threads.

Just passing by to inform that I was able to make NVidia's VDPAU technology work with GStreamer by compiling the latest gst-VAAPI lib (~gbeauchesne), like that:

Example RMVB file output

$ gst-launch-0.10 -vv  filesrc location="~/putz.rmvb"  ! ffdemux_rm ! ffdec_rv40  ! x264enc ! vaapidecode ! vaapisink

and no more freezes or choppy video! 

Graphics card is NVidia 8500 GT, NVIDIA Driver Version: 260.19.06 with Intel Core i7 + 4GB RAM

now I'm getting the 0.11 gst GIT and will see if it makes any difference.

Got the latest gst plugin here: (THANK YOU!)
[http://www.splitted-desktop.com/~gbeauchesne/gstreamer-vaapi/]("http://www.splitted-desktop.com/%7Egbeauchesne/gstreamer-vaapi/")


Anyone willing to help me test? Was this useful?

---

### Post by Guzpido Krush on 2011-04-22
ooops sorry i forgot to mention:

To make the **gstreamer-vaapi-0.2.5** compile good I had to insert a new include line:

#include  <va/va_x11.h>

in the
./gst/vaapiconvert/gstvaapiconvert.c 

file.

:D

You will need to install some extra stuff, like gst-plugins-good, bad and ugly, some libraries like: 
libva-dev, libavcodec-dev, gstvaapi-x11-0.10

ask me if there is any problem, don't think this need a tutorial anyway

---

### Post by lord_phantom on 2011-05-15
Thanks, I was looking around the net for recent information about GStreamer and VDPAU. I'll try this tomorrow.

---

### Post by quequotion on 2011-07-11
I installed gstreamer0.10-vaapi, nvidia-va-vdpau, etc. from a ppa.

Trying the above suggestion gives me this output:

```

libva: libva version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/nvidia_drv_video.so
libva: va_openDriver() returns 0
Setting pipeline to PAUSED ...
libva: libva version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/nvidia_drv_video.so
libva: va_openDriver() returns 0
/GstPipeline:pipeline0/GstVaapiSink:vaapisink0: synchronous = FALSE
Pipeline is PREROLLING ...
ERROR: from element /GstPipeline:pipeline0/ffdemux_rm:ffdemux_rm0: GStreamer encountered a general supporting library error.
Additional debug info:
gstffmpegdemux.c(1255): gst_ffmpegdemux_open (): /GstPipeline:pipeline0/ffdemux_rm:ffdemux_rm0:
Input/output error
ERROR: pipeline doesn't want to preroll.
Setting pipeline to NULL ...
Freeing pipeline ...

```

Also, no gstreamer applications are working and most freeze the desktop.

Any ideas?

---

### Post by HunterAtUbuntu on 2011-11-23
I get a similar error to the one above.

When running
```
gst-launch-0.10 -v filesrc location=path/to/file x264enc ! vaapidecode ! vaapisink fullscreen=false

```
I get
```
libva: libva version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/nvidia_drv_video.so
libva: va_openDriver() returns 0
Setting pipeline to PAUSED ...
libva: libva version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/nvidia_drv_video.so
libva: va_openDriver() returns 0
/GstPipeline:pipeline0/GstVaapiSink:vaapisink0: synchronous = FALSE
Pipeline is PREROLLING ...
ERROR: from element /GstPipeline:pipeline0/GstFileSrc:filesrc0: Internal data flow error.
Additional debug info:
gstbasesrc.c(2582): gst_base_src_loop (): /GstPipeline:pipeline0/GstFileSrc:filesrc0:
streaming task paused, reason not-linked (-1)
ERROR: pipeline doesn't want to preroll.
Setting pipeline to NULL ...
Freeing pipeline ...

```

---

