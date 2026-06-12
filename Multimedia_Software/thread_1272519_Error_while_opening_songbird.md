---
title: "Error while opening songbird"
date: 2009-09-22
forum: Multimedia Software
---

### Post by r5r4y on 2009-09-22
Hello,
i've downloaded songbird .deb file grom getdeb, i dobule click the program in the menu but it does not open at all... i've tried runing songbird from the terminal, here is the output:

```

songbird

(songbird-bin:4054): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstdeinterlace.so': /usr/lib/gstreamer-0.10/libgstdeinterlace.so: undefined symbol: gst_video_format_parse_caps_interlaced

(songbird-bin:4054): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgsthdvparse.so': /usr/lib/gstreamer-0.10/libgsthdvparse.so: undefined symbol: _gst_debug_dump_mem
././songbird-bin: symbol lookup error: /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_task_pool_get_type
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal

```

i've also tried to remove the packge libvisual-0.4-plugins from Synpatic but it does not help, i'm still getting this error.

i've tried to download the tar.gz from the songbird site but still i'm getting the same error.

any ideas?

---

### Post by r5r4y on 2009-10-01
Solved...!

```
sudo mv /usr/lib/python2.6/dist-packages/gst-0.10/ /usr/lib/python2.6/dist-packages/gst-0.10_bad
```

:)

---

### Post by SiN_AmoR on 2009-10-28
Thaaaaanks :)

totally worked on Karmic ;)

---

### Post by rockstarmode on 2009-11-03
I had this problem on Fedora 11 as well.  You can also try removing the all of the libgst files that are distributed with Songbird.  Look in Songbird/lib/libgst* and remove them.

Songbird starts up like a charm after this.  Source: [http://changelog.complete.org/archives/1081-songbird-how-to-make-great-software-unpopular](http://changelog.complete.org/archives/1081-songbird-how-to-make-great-software-unpopular)

---

### Post by rob.arntfield on 2009-11-10
I have to confirm this one, after trying everything else it worked out. 

Also note, I had previously removed the libvisual-0.4-plugins.

---

