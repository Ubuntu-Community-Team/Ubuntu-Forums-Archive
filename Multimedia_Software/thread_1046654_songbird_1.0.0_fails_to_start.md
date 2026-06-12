---
title: "songbird 1.0.0 fails to start"
date: 2009-01-21
forum: Multimedia Software
---

### Post by bobdobbs on 2009-01-21
Hi all.

I downloaded songbird_1.0.0_i686_unter-hund-blog.deb and proceeded to install songbird on my 32-bit ubuntustudio system.

Songbird installed, but when I launch if from the menu, nothing happens.
ps | grep songbird shows that songbird is indeed running.

When I launch it from the terminal, I see this:
```

*** glibc detected *** ././songbird-bin: munmap_chunk(): invalid pointer: 0xb1c304e0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7cab3f4]
/usr/lib/libvisual-0.4.so.0(visual_mem_free+0x21)[0xb1a85141]
/usr/lib/libvisual-0.4.so.0[0xb1a7c407]
/usr/lib/libvisual-0.4.so.0(visual_plugin_get_list+0x73)[0xb1a7c5e3]
/usr/lib/libvisual-0.4.so.0(visual_init+0x291)[0xb1a8bec1]
/usr/lib/gstreamer-0.10/libgstlibvisual.so[0xb1aee1f4]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3fc82c2]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_plugin_load_file+0x62f)[0xb3fc8b79]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3fd37ee]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_registry_scan_path+0x135)[0xb3fd3993]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3f83a44]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3f83f30]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3f84589]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3f84b44]
/usr/lib/libglib-2.0.so.0(g_option_context_parse+0x5b3)[0xb6ab57e3]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init_check+0xf1)[0xb3f82d1b]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init+0x32)[0xb3f82e25]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN18sbGStreamerService4InitEv+0x9ff)[0xb3e74cf3]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3e7b8e1]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3e82252]
/usr/share/Songbird/xulrunner/libxul.so[0xb7581449]
/usr/share/Songbird/xulrunner/libxul.so[0xb758090b]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3e7f2ef]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3e7f319]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3e7eac5]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3e7a3a5]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN27sbGStreamerMediacoreFactory4InitEv+0x46)[0xb3e7ab5c]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3e7b841]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3e82252]
/usr/share/Songbird/xulrunner/libxul.so[0xb7581449]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb4f470f9]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb4f47126]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb4f469c1]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN8nsCOMPtrI19sbIMediacoreFactoryEC1ERK15nsCOMPtr_helper+0x2d)[0xb4f338b5]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN18sbMediacoreManager4InitEv+0x1b7)[0xb4f311e7]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb4f31564]
/usr/share/Songbird/xulrunner/libxul.so[0xb755e21f]
/usr/share/Songbird/xulrunner/libxul.so[0xb755e7c4]
/usr/share/Songbird/xulrunner/libxul.so[0xb6df3a98]
/usr/share/Songbird/xulrunner/libxul.so(XRE_main+0x1aba)[0xb6df17b2]
././songbird-bin[0x8048f40]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7c52685]
././songbird-bin[0x8048bb1]
======= Memory map: ========
08048000-0804e000 r-xp 00000000 08:01 5973114    /usr/share/Songbird/songbird-bin
0804e000-0804f000 rw-p 00006000 08:01 5973114    /usr/share/Songbird/songbird-bin
087c5000-087e6000 rw-p 087c5000 00:00 0          [heap]
b1a6b000-b1aa7000 r-xp 00000000 08:01 5228989    /usr/lib/libvisual-0.4.so.0.0.0
b1aa7000-b1aa8000 r--p 0003b000 08:01 5228989    /usr/lib/libvisual-0.4.so.0.0.0
b1aa8000-b1aa9000 rw-p 0003c000 08:01 5228989    /usr/lib/libvisual-0.4.so.0.0.0
b1ac8000-b1ad4000 r-xp 00000000 08:01 5228651    /usr/lib/libiec61883.so.0.1.0
b1ad4000-b1ad5000 rw-p 0000b000 08:01 5228651    /usr/lib/libiec61883.so.0.1.0
b1ae6000-b1aec000 rw-p b1ae6000 00:00 0 
b1aec000-b1af2000 r-xp 00000000 08:01 5095473    /usr/lib/gstreamer-0.10/libgstlibvisual.so
b1af2000-b1af3000 r--p 00005000 08:01 5095473    /usr/lib/gstreamer-0.10/libgstlibvisual.so
b1af3000-b1af4000 rw-p 00006000 08:01 5095473    /usr/lib/gstreamer-0.10/libgstlibvisual.so
b1af4000-b1b05000 r-xp 00000000 08:01 5229643    /usr/lib/libcdaudio.so.1.0.0
b1b05000-b1b06000 r--p 00010000 08:01 5229643    /usr/lib/libcdaudio.so.1.0.0
b1b06000-b1b07000 rw-p 00011000 08:01 5229643    /usr/lib/libcdaudio.so.1.0.0
b1b09000-b1b13000 r-xp 00000000 08:01 5095425    /usr/lib/gstreamer-0.10/libgst1394.so
b1b13000-b1b14000 r--p 00009000 08:01 5095425    /usr/lib/gstreamer-0.10/libgst1394.so
b1b14000-b1b15000 rw-p 0000a000 08:01 5095425    /usr/lib/gstreamer-0.10/libgst1394.so
b1b15000-b1b24000 r-xp 00000000 08:01 5095500    /usr/lib/gstreamer-0.10/libgsttheora.so
b1b24000-b1b25000 r--p 0000e000 08:01 5095500    /usr/lib/gstreamer-0.10/libgsttheora.so
b1b25000-b1b26000 rw-p 0000f000 08:01 5095500    /usr/lib/gstreamer-0.10/libgsttheora.so
b1b26000-b1b4d000 r-xp 00000000 08:01 5095579    /usr/lib/gstreamer-0.10/libresindvd.so
b1b4d000-b1b4e000 r--p 00027000 08:01 5095579    /usr/lib/gstreamer-0.10/libresindvd.so
b1b4e000-b1b4f000 rw-p 00028000 08:01 5095579    /usr/lib/gstreamer-0.10/libresindvd.so
b1b4f000-b1b6e000 r-xp 00000000 08:01 5228665    /usr/lib/libjpeg.so.62.0.0
b1b6e000-b1b6f000 rw-p 0001e000 08:01 5228665    /usr/lib/libjpeg.so.62.0.0
b1b6f000-b1b84000 r-xp 00000000 08:01 5229649    /usr/lib/libdvdnav.so.4.1.2
b1b84000-b1b85000 r--p 00014000 08:01 5229649    /usr/lib/libdvdnav.so.4.1.2
b1b85000-b1b86000 rw-p 00015000 08:01 5229649    /usr/lib/libdvdnav.so.4.1.2
b1b86000-b1b8c000 r-xp 00000000 08:01 5095584    /usr/lib/gstreamer-0.10/libgsta52dec.so
b1b8c000-b1b8d000 r--p 00005000 08:01 5095584    /usr/lib/gstreamer-0.10/libgsta52dec.so
b1b8d000-b1b8e000 rw-p 00006000 08:01 5095584    /usr/lib/gstreamer-0.10/libgsta52dec.so
b1b8e000-b1b9b000 r-xp 00000000 08:01 5095471    /usr/lib/gstreamer-0.10/libgstjpeg.so
b1b9b000-b1b9c000 r--p 0000c000 08:01 5095471    /usr/lib/gstreamer-0.10/libgstjpeg.so
b1b9c000-b1b9d000 rw-p 0000d000 08:01 5095471    /usr/lib/gstreamer-0.10/libgstjpeg.so
b1b9d000-b1bae000 r-xp 00000000 08:01 5226788    /usr/lib/libv4lconvert.so.0
b1bae000-b1baf000 r--p 00010000 08:01 5226788    /usr/lib/libv4lconvert.so.0
b1baf000-b1bb0000 rw-p 00011000 08:01 5226788    /usr/lib/libv4lconvert.so.0
b1bb0000-b1d00000 rw-p b1bb0000 00:00 0 
b1d09000-b1d12000 r-xp 00000000 08:01 5095597    /usr/lib/gstreamer-0.10/libgstlame.so
b1d12000-b1d13000 r--p 00009000 08:01 5095597    /usr/lib/gstreamer-0.10/libgstlame.so
b1d13000-b1d14000 rw-p 0000a000 08:01 5095597    /usr/lib/gstreamer-0.10/libgstlame.so
b1d14000-b1d19000 r-xp 00000000 08:01 5226742    /usr/lib/libv4l2.so.0
b1d19000-b1d1a000 r--p 00005000 08:01 5226742    /usr/lib/libv4l2.so.0
b1d1a000-b1d1d000 rw-p 00006000 08:01 5226742    /usr/lib/libv4l2.so.0
b1d1d000-b1d3b000 r-xp 00000000 08:01 5243045    /usr/lib/gstreamer-0.10/libgnl.so
b1d3b000-b1d3c000 rw-p 0001d000 08:01 5243045    /usr/lib/gstreamer-0.10/libgnl.so
b1d3c000-b1d63000 r-xp 00000000 08:01 5229701    /usr/lib/libsidplay.so.1.0.3
b1d63000-b1d73000 rw-p 00026000 08:01 5229701    /usr/lib/libsidplay.so.1.0.3
b1d73000-b1d7f000 rw-p b1d73000 00:00 0 
b1d80000-b1d84000 r-xp 00000000 08:01 5095526    /usr/lib/gstreamer-0.10/libgstcdaudio.so
b1d84000-b1d85000 r--p 00003000 08:01 5095526    /usr/lib/gstreamer-0.10/libgstcdaudio.so
b1d85000-b1d86000 rw-p 00004000 08:01 5095526    /usr/lib/gstreamer-0.10/libgstcdaudio.so
b1d86000-b1d9c000 r-xp 00000000 08:01 5095504    /usr/lib/gstreamer-0.10/libgstvideo4linux2.so
b1d9c000-b1d9d000 r--p 00015000 08:01 5095504    /usr/lib/gstreamer-0.10/libgstvideo4linux2.so
b1d9d000-b1d9e000 rw-p 00016000 08:01 5095504    /usr/lib/gstreamer-0.10/libgstvideo4linux2.so
b1d9e000-b1da6000 r-xp 00000000 08:01 5095530    /usr/lib/gstreamer-0.10/libgstdeinterlace2.so
b1da6000-b1da7000 r--p 00007000 08:01 5095530    /usr/lib/gstreamer-0.10/libgstdeinterlace2.so
b1da7000-b1da8000 rw-p 00008000 08:01 5095530    /usr/lib/gstreamer-0.10/libgstdeinterlace2.so
b1da8000-b1db4000 r-xp 00000000 08:01 5095539    /usr/lib/gstreamer-0.10/libgstflvdemux.so
b1db4000-b1db5000 r--p 0000b000 08:01 5095539    /usr/lib/gstreamer-0.10/libgstflvdemux.so
b1db5000-b1db6000 rw-p 0000c000 08:01 5095539    /usr/lib/gstreamer-0.10/libgstflvdemux.so
b1db6000-b1dbe000 r-xp 00000000 08:01 5095535    /usr/lib/gstreamer-0.10/libgstfaad.so
b1dbe000-b1dbf000 r--p 00007000 08:01 5095535    /usr/lib/gstreamer-0.10/libgstfaad.so
b1dbf000-b1dc0000 rw-p 00008000 08:01 5095535    /usr/lib/gstreamer-0.10/libgstfaad.so
b1dc0000-b1dce000 r-xp 00000000 08:01 5229659    /usr/lib/libjack.so.0.0.28
b1dce000-b1dcf000 r--p 0000e000 08:01 5229659    /usr/lib/libjack.so.0.0.28
b1dcf000-b1dd1000 rw-p 0000f000 08:01 5229659    /usr/lib/libjack.so.0.0.28
b1dd1000-b1dd9000 rw-p b1dd1000 00:00 0 
b1dda000-b1ddd000 r-xp 00000000 08:01 5228881    /usr/lib/librom1394.so.0.3.0
b1ddd000-b1dde000 rw-p 00002000 08:01 5228881    /usr/lib/librom1394.so.0.3.0
b1dde000-b1df6000 r-xp 00000000 08:01 5095553    /usr/lib/gstreamer-0.10/libgstmve.so
b1df6000-b1df7000 r--p 00017000 08:01 5095553    /usr/lib/gstreamer-0.10/libgstmve.so
b1df7000-b1df8000 rw-p 00018000 08:01 5095553    /usr/lib/gstreamer-0.10/libgstmve.so
b1df8000-b1e30000 r-xp 00000000 08:01 2760783    /lib

```

As you can see, the launch process seems to freeze in the middle of an interaction with a library.

Any idea what could be happening here?
Is this a problem with songbird, or with a library?

Thanks

---

### Post by aeacides on 2009-01-21
Hey there,

I can't give you an answer based on your backtrace, but I got a question / suggestion:

Have you try downloading from Songbird website? 
[http://www.getsongbird.com/]("http://www.getsongbird.com/")

Maybe it will solve your problem ... :)

---

### Post by bobdobbs on 2009-01-21
> **aeacides said:**
> Hey there,

I can't give you an answer based on your backtrace, but I got a question / suggestion:

Have you try downloading from Songbird website? 
[http://www.getsongbird.com/]("http://www.getsongbird.com/")

Maybe it will solve your problem ... :)

Hi.

The binary in the tarball does pretty much the same thing.
It freezes at a different point. But the output is very similair:
```

...(some code omitted)...
b164d000-b164e000 rw-p 00016000 08:01 5095504    /usr/lib/gstreamer-0.10/libgstvideo4linux2.so
b164e000-b1653000 r-xp 00000000 08:01 5095596    /usr/lib/gstreamer-0.10/libgstsid.so
b1653000-b1654000 r--p 00004000 08:01 5095596    /usr/lib/gstreamer-0.10/libgstsid.so
b1654000-b1655000 rw-p 00005000 08:01

```

---

### Post by aeacides on 2009-01-21
it seems that you have the same kind of problem... 

[http://ubuntuforums.org/showthread.php?t=1005356](http://ubuntuforums.org/showthread.php?t=1005356)

---

### Post by escentrix on 2009-01-23
I was having this problem and after some digging I started trying some things.
Removing **libvisual-0.4-plugins** package seems to have made it work. Might want to try it yourself and see.

---

### Post by Stealth on 2009-01-25
Thanks for that escentrix, odd that fixed it o_o

---

### Post by pbrito81 on 2009-03-16
That worked for me too! Thanks, escentrix!

---

