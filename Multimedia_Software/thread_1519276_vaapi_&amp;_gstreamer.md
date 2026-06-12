---
title: "vaapi &amp; gstreamer"
date: 2010-06-27
forum: Multimedia Software
---

### Post by owenlinx on 2010-06-27
Ok I have it installed and working from the command line :p
[list]
[*]Install latest ffmpeg I used [_this link_]("http://ubuntuforums.org/showpost.php?p=4907079&postcount=1") 
be sure to include --enable-vaapi when compiling ffmpeg
[*]Install [_gstreamer-vaapi_]("http://www.splitted-desktop.com/~gbeauchesne/gstreamer-vaapi/") 
./configure
make
sudo checkinstall --default
[*]sudo ldconfig
[*]delete the file ~/.gstreamer-0.10/registry.i486.bin
[*]run in terminal "gst-inspect-0.10 vaapisink"
[*]play a movie with "gst-launch-0.10 -v filesrc location=/home/justin/Videos/nova.mp4 ! \ qtdemux ! vaapidecode ! vaapisink fullscreen=false" [/list]

It works very well, but **I can't enter vaapisink into gstreamer-properties**. It gives the error can't link ffmpegcsp to vaapisink.

If this can get working will vaapi work with all gstreamer programs? In particular my case, empathy.

---

### Post by Yellow Pasque on 2010-06-28
I have the same issue. :\

---

### Post by Guzpido Krush on 2011-04-22
try this crazy pipeline:

! decodebin  ! x264enc ! vaapidecode ! vaapisink

works for me in the shell as in:

$ gst-launch-0.10 -vv  filesrc location="/home/talon/area/TZone/putz.rmvb"  ! decodebin  ! x264enc ! vaapidecode ! vaapisink

---

### Post by Guzpido Krush on 2011-04-22
ok i put only

 x264enc ! vaapidecode ! vaapisink

on the gstreamer-properties video tab and is seems to work.

---

### Post by HunterAtUbuntu on 2011-11-22
Has anyone gotten this to work with the latest gstreamer-vaapi from git?
I keep getting the following error:
```
/usr/bin/ld: test_decode-test-decode.o: undefined reference to symbol 'gst_mini_object_unref'
/usr/bin/ld: note: 'gst_mini_object_unref' is defined in DSO /usr/lib/libgstreamer-0.10.so.0 so try adding it to the linker command line
/usr/lib/libgstreamer-0.10.so.0: could not read symbols: Invalid operation
collect2: ld returned 1 exit status

```

Edit:
Fixed that and another error by including a couple libraries. But now I'm stuck at
```

../gst-libs/gst/vaapi/.libs/libgstvaapi-x11-0.10.so: undefined reference to `vaPutSurface'
../gst-libs/gst/vaapi/.libs/libgstvaapi-x11-0.10.so: undefined reference to `vaGetDisplay'
collect2: ld returned 1 exit status


```

Both functions are defined in va/va_x11.h which I have included in every file that references them, but I still keep getting that error

Edit:
And now past that. had to do
```
export LIBS="/usr/lib/libgstreamer-0.10.so /usr/lib/libva-x11.so /usr/lib/libva.so"
```
now it compiles and installs successfully, but I still can't play anything. The test in gstreamer-properties works fine, but when trying to play something with totem I get "gstreamer encountered an internal stream error" :(

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

