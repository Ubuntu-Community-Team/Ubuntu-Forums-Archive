---
title: "songbird stopped working after gstreamer update"
date: 2009-03-17
forum: Multimedia Software
---

### Post by brunods on 2009-03-17
So, quite nice. I upgraded songbird to 1.1.1, it works perfectly. BUT yesterday I updated the system and there was a gstreamer update. I restarted the computer and now songbird won't start! The weirdest thing is that it just stops, it doesn't even give me a segmentation fault. I'll paste what I get in the terminal:

```
$ songbird --debug
*** glibc detected *** ././songbird-bin: free(): invalid pointer: 0xb3677e60 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7e11454]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7e134b6]
/usr/lib/libvisual-0.4.so.0(visual_mem_free+0x21)[0xb2eeb141]
/usr/lib/libvisual-0.4.so.0[0xb2ee2407]
/usr/lib/libvisual-0.4.so.0(visual_plugin_get_list+0x73)[0xb2ee25e3]
/usr/lib/libvisual-0.4.so.0(visual_init+0x291)[0xb2ef1ec1]
/usr/lib/gstreamer-0.10/libgstlibvisual.so[0xb2f9f1f4]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3da52f6]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_plugin_load_file+0x62f)[0xb3da5bad]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3db0725]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_registry_scan_path+0x135)[0xb3db09c7]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3d60a44]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3d60f30]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3d61589]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3d61b44]
/usr/lib/libglib-2.0.so.0(g_option_context_parse+0x5b3)[0xb6c05803]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init_check+0xf1)[0xb3d5fd1b]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init+0x32)[0xb3d5fe25]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN18sbGStreamerService4InitEv+0x9ff)[0xb3ccf6a3]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3cd7a05]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3ce0db6]
/usr/share/Songbird/xulrunner/libxul.so[0xb76c6a85]
/usr/share/Songbird/xulrunner/libxul.so[0xb76c5f47]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3cdde83]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3cddead]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3cdd659]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3cd6413]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN27sbGStreamerMediacoreFactory4InitEv+0x46)[0xb3cd6be0]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3cd7965]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3ce0db6]
/usr/share/Songbird/xulrunner/libxul.so[0xb76c6a85]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb4edfe29]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb4edfe56]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb4edf6f1]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN8nsCOMPtrI19sbIMediacoreFactoryEC1ERK15nsCOMPtr_helper+0x2d)[0xb4ec8705]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN18sbMediacoreManager4InitEv+0x1b7)[0xb4ec62d7]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb4ec6654]
/usr/share/Songbird/xulrunner/libxul.so[0xb76a3773]
/usr/share/Songbird/xulrunner/libxul.so[0xb76a3d18]
/usr/share/Songbird/xulrunner/libxul.so[0xb6f37be0]
/usr/share/Songbird/xulrunner/libxul.so(XRE_main+0x19af)[0xb6f358c1]
././songbird-bin[0x8048f40]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7db8685]
././songbird-bin[0x8048bb1]
======= Memory map: ========
08048000-0804e000 r-xp 00000000 08:03 3769806    /usr/share/Songbird/songbird-bin
0804e000-0804f000 rw-p 00006000 08:03 3769806    /usr/share/Songbird/songbird-bin
082a0000-082c1000 rw-p 082a0000 00:00 0          [heap]
b2ec1000-b2ed1000 rw-p b2ec1000 00:00 0 
b2ed1000-b2f0d000 r-xp 00000000 08:03 3580010    /usr/lib/libvisual-0.4.so.0.0.0
b2f0d000-b2f0e000 r--p 0003b000 08:03 3580010    /usr/lib/libvisual-0.4.so.0.0.0
b2f0e000-b2f0f000 rw-p 0003c000 08:03 3580010    /usr/lib/libvisual-0.4.so.0.0.0
b2f0f000-b2f15000 r-xp 00000000 08:03 3585205    /usr/lib/gstreamer-0.10/libgstgoom2k1.so
b2f15000-b2f16000 r--p 00005000 08:03 3585205    /usr/lib/gstreamer-0.10/libgstgoom2k1.so
b2f16000-b2f17000 rw-p 00006000 08:03 3585205    /usr/lib/gstreamer-0.10/libgstgoom2k1.so
b2f17000-b2f57000 rw-p b2f17000 00:00 0 
b2f57000-b2f67000 r-xp 00000000 08:03 3580235    /usr/lib/libhal.so.1.0.0
b2f67000-b2f68000 r--p 0000f000 08:03 3580235    /usr/lib/libhal.so.1.0.0
b2f68000-b2f69000 rw-p 00010000 08:03 3580235    /usr/lib/libhal.so.1.0.0
b2f69000-b2f77000 rw-p b2f69000 00:00 0 
b2f7c000-b2f97000 r-xp 00000000 08:03 3596325    /usr/lib/sse2/libspeex.so.1.4.0
b2f97000-b2f98000 r--p 0001a000 08:03 3596325    /usr/lib/sse2/libspeex.so.1.4.0
b2f98000-b2f99000 rw-p 0001b000 08:03 3596325    /usr/lib/sse2/libspeex.so.1.4.0
b2f9d000-b2fa3000 r-xp 00000000 08:03 3584267    /usr/lib/gstreamer-0.10/libgstlibvisual.so
b2fa3000-b2fa4000 r--p 00005000 08:03 3584267    /usr/lib/gstreamer-0.10/libgstlibvisual.so
b2fa4000-b2fa5000 rw-p 00006000 08:03 3584267    /usr/lib/gstreamer-0.10/libgstlibvisual.so
b2fa5000-b2faa000 r-xp 00000000 08:03 3585206    /usr/lib/gstreamer-0.10/libgsthalelements.so
b2faa000-b2fab000 r--p 00004000 08:03 3585206    /usr/lib/gstreamer-0.10/libgsthalelements.so
b2fab000-b2fac000 rw-p 00005000 08:03 3585206    /usr/lib/gstreamer-0.10/libgsthalelements.so
b2fac000-b2fe4000 r-xp 00000000 08:03 1671250    /lib/libncursesw.so.5.6
b2fe4000-b2fe7000 rw-p 00037000 08:03 1671250    /lib/libncursesw.so.5.6
b2fe7000-b2ff8000 r-xp 00000000 08:03 1851591    /usr/lib/libcucul.so.0.99.13
b2ff8000-b2ff9000 r--p 00010000 08:03 1851591    /usr/lib/libcucul.so.0.99.13
b2ff9000-b3080000 rw-p 00011000 08:03 1851591    /usr/lib/libcucul.so.0.99.13
b3080000-b3084000 rw-p b3080000 00:00 0 
b3085000-b3087000 r-xp 00000000 08:03 3585223    /usr/lib/gstreamer-0.10/libgstnavigationtest.so
b3087000-b3088000 ---p 00002000 08:03 3585223    /usr/lib/gstreamer-0.10/libgstnavigationtest.so
b3088000-b3089000 r--p 00002000 08:03 3585223    /usr/lib/gstreamer-0.10/libgstnavigationtest.so
b3089000-b308a000 rw-p 00003000 08:03 3585223    /usr/lib/gstreamer-0.10/libgstnavigationtest.so
b308a000-b3095000 r-xp 00000000 08:03 3585234    /usr/lib/gstreamer-0.10/libgstspeex.so
b3095000-b3096000 r--p 0000a000 08:03 3585234    /usr/lib/gstreamer-0.10/libgstspeex.so
b3096000-b3097000 rw-p 0000b000 08:03 3585234    /usr/lib/gstreamer-0.10/libgstspeex.so
b3097000-b3132000 r-xp 00000000 08:03 1673424    /lib/libslang.so.2.1.3
b3132000-b3135000 r--p 0009a000 08:03 1673424    /lib/libslang.so.2.1.3
b3135000-b3142000 rw-p 0009d000 08:03 1673424    /lib/libslang.so.2.1.3
b3142000-b3178000 rw-p b3142000 00:00 0 
b3178000-b31a5000 r-xp 00000000 08:03 1671248    /lib/libncurses.so.5.6
b31a5000-b31a8000 rw-p 0002c000 08:03 1671248    /lib/libncurses.so.5.6
b31a8000-b31c0000 r-xp 00000000 08:03 1851585    /usr/lib/libaa.so.1.0.4
b31c0000-b31c1000 r--p 00018000 08:03 1851585    /usr/lib/libaa.so.1.0.4
b31c1000-b31c2000 rw-p 00019000 08:03 1851585    /usr/lib/libaa.so.1.0.4
b31c2000-b31c4000 rw-p b31c2000 00:00 0 
b31c4000-b322b000 r-xp 00000000 08:03 1851575    /usr/lib/libtag.so.1.5.0
b322b000-b322c000 r--p 00067000 08:03 1851575    /usr/lib/libtag.so.1.5.0
b322c000-b322d000 rw-p 00068000 08:03 1851575    /usr/lib/libtag.so.1.5.0
b322f000-b3231000 rw-p b322f000 00:00 0 
b3231000-b3239000 r-xp 00000000 08:03 1851595    /usr/lib/libcaca.so.0.99.13
b3239000-b323a000 r--p 00007000 08:03 1851595    /usr/lib/libcaca.so.0.99.13
b323a000-b323b000 rw-p 00008000 08:03 1851595    /usr/lib/libcaca.so.0.99.13
b323b000-b323e000 r-xp 00000000 08:03 3581656    /usr/lib/gstreamer-0.10/libgstcacasink.so
b323e000-b323f000 r--p 00002000 08:03 3581656    /usr/lib/gstreamer-0.10/libgstcacasink.so
b323f000-b3240000 rw-p 00003000 08:03 3581656    /usr/lib/gstreamer-0.10/libgstcacasink.so
b3240000-b3251000 r-xp 00000000 08:03 3582710    /usr/lib/libv4lconvert.so.0
b3251000-b3252000 r--p 00010000 08:03 3582710    /usr/lib/libv4lconvert.so.0
b3252000-b3253000 rw-p 00011000 08:03 3582710    /usr/lib/libv4lconvert.so.0
b3253000-b32a3000 rw-p b3253000 00:00 0 
b32a3000-b32a8000 r-xp 00000000 08:03 3582209    /usr/lib/libv4l2.so.0
b32a8000-b32a9000 r--p 00005000 08:03 3582209    /usr/lib/libv4l2.so.0
b32a9000-b32ac000 rw-p 00006000 08:03 3582209    /usr/lib/libv4l2.so.0
b32ac000-b32b1000 r-xp 00000000 08:03 1851581    /usr/lib/libgpm.so.2.0.0
b32b1000-b32b2000 r--p 00004000 08:03 1851581    /usr/lib/libgpm.so.2.0.0
b32b2000-b32b3000 rw-p 00005000 08:03 1851581    /usr/lib/libgpm.so.2.0.0
b32b3000-b32bd000 r-xp 00000000 08:03 3585235    /usr/lib/gstreamer-0.10/libgsttaglib.so
b32bd000-b32be000 r--p 00009000 08:03 3585235    /usr/lib/gstreamer-0.10/libgsttaglib.so
b32be000-b32bf000 rw-p 0000a000 08:03 3585235    /usr/lib/gstreamer-0.10/libgsttaglib.so
b32bf000-b32d5000 r-xp 00000000 08:03 3585237    /usr/lib/gstreamer-0.10/libgstvideo4linux2.so
b32d5000-b32d6000 r--p 00015000 08:03 3585237    /usr/lib/gstreamer-0.10/libgstvideo4linux2.so
b32d6000-b32d7000 rw-p 00016000 08:03 3585237    /usr/lib/gstreamer-0.10/libgstvideo4linux2.so
b32d7000-b32de000 r-xp 00000000 08:03 3581705    /usr/lib/gstreamer-0.10/libgstgconfelements.so
b32de000-b32df000 r--p 00006000 08:03 3581705    /usr/lib/gstreamer-0.10/libgstgconfelements.so
b32df000-b32e0000 rw-p 00007000 08:03 3581705    /usr/lib/gstreamer-0.10/libgstgconfelements.so
b32e0000-b32f7000 r-xp 00000000 08:03 3581290    /usr/lib/gstreamer-0.10/libgsttcp.so
b32f7000-b32f8000 r--p 00016000 08:03 3581290    /usr/lib/gstreamer-0.10/libgst

```


and then it'll just hang there!

can anyone help me??

---

### Post by BatPenguin on 2009-03-18
Same, or similar, thing happens to me as well:

```
*** glibc detected *** ././songbird-bin: free(): invalid pointer: 0xb2ce6c40 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7d80454]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7d824b6]
/usr/lib/tls/libnvidia-tls.so.1[0xb4f00aa0]
/usr/lib/libgmodule-2.0.so.0(g_module_open+0x1cc)[0xb7d0a73c]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_plugin_load_file+0x348)[0xb3ea58c6]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3eb0822]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_registry_scan_path+0x135)[0xb3eb09c7]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3e60a44]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3e60f30]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3e61589]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3e61b44]
/usr/lib/libglib-2.0.so.0(g_option_context_parse+0x5b3)[0xb6b79803]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init_check+0xf1)[0xb3e5fd1b]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init+0x32)[0xb3e5fe25]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN18sbGStreamerService4InitEv+0x9ff)[0xb3dfa6a3]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3e02a05]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3e0bdb6]
/usr/share/Songbird/xulrunner/libxul.so[0xb7644a85]
/usr/share/Songbird/xulrunner/libxul.so[0xb7643f47]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3e08e83]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3e08ead]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3e08659]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3e01413]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN27sbGStreamerMediacoreFactory4InitEv+0x46)[0xb3e01be0]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3e02965]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3e0bdb6]
/usr/share/Songbird/xulrunner/libxul.so[0xb7644a85]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb593be29]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb593be56]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb593b6f1]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN8nsCOMPtrI19sbIMediacoreFactoryEC1ERK15nsCOMPtr_helper+0x2d)[0xb5924705]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN18sbMediacoreManager4InitEv+0x1b7)[0xb59222d7]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb5922654]
/usr/share/Songbird/xulrunner/libxul.so[0xb7621773]
/usr/share/Songbird/xulrunner/libxul.so[0xb7621d18]
/usr/share/Songbird/xulrunner/libxul.so[0xb6eb5be0]
/usr/share/Songbird/xulrunner/libxul.so(XRE_main+0x19af)[0xb6eb38c1]
././songbird-bin[0x8048f40]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7d27685]
././songbird-bin[0x8048bb1]
======= Memory map: ========
08048000-0804e000 r-xp 00000000 08:02 7456219    /usr/share/Songbird/songbird-bin
0804e000-0804f000 rw-p 00006000 08:02 7456219    /usr/share/Songbird/songbird-bin
b1100000-b1200000 rw-p b1100000 00:00 0 
b126c000-b1f85000 r-xp 00000000 08:02 6179267    /usr/lib/libGLcore.so.180.37
b1f85000-b2176000 rwxp 00d19000 08:02 6179267    /usr/lib/libGLcore.so.180.37
b2176000-b2183000 rwxp b2176000 00:00 0 
b2183000-b2210000 r-xp 00000000 08:02 6179265    /usr/lib/libGL.so.180.37
b2210000-b222e000 rwxp 0008d000 08:02 6179265    /usr/lib/libGL.so.180.37
b222e000-b223d000 rwxp b222e000 00:00 0 
b223d000-b225e000 r-xp 00000000 08:02 6176942    /usr/lib/libexif.so.12.2.0
b225e000-b2266000 r--p 00020000 08:02 6176942    /usr/lib/libexif.so.12.2.0
b2266000-b2267000 rw-p 00028000 08:02 6176942    /usr/lib/libexif.so.12.2.0
b2267000-b230e000 r-xp 00000000 08:02 6179542    /usr/lib/libexempi.so.3.1.3
b230e000-b230f000 r--p 000a7000 08:02 6179542    /usr/lib/libexempi.so.3.1.3
b230f000-b2312000 rw-p 000a8000 08:02 6179542    /usr/lib/libexempi.so.3.1.3
b232f000-b2349000 r-xp 00000000 08:02 6182963    /usr/lib/libcdio.so.7.1.0
b2349000-b234a000 r--p 00019000 08:02 6182963    /usr/lib/libcdio.so.7.1.0
b234a000-b234b000 rw-p 0001a000 08:02 6182963    /usr/lib/libcdio.so.7.1.0
b234b000-b234f000 rw-p b234b000 00:00 0 
b2350000-b2358000 r-xp 00000000 08:02 6178033    /usr/lib/libiptcdata.so.0.3.2
b2358000-b235a000 rw-p 00007000 08:02 6178033    /usr/lib/libiptcdata.so.0.3.2
b235a000-b236a000 r-xp 00000000 08:02 6177030    /usr/lib/gstreamer-0.10/libgstmetadata.so
b236a000-b236b000 r--p 0000f000 08:02 6177030    /usr/lib/gstreamer-0.10/libgstmetadata.so
b236b000-b236c000 rw-p 00010000 08:02 6177030    /usr/lib/gstreamer-0.10/libgstmetadata.so
b236c000-b237f000 r-xp 00000000 08:02 6182967    /usr/lib/libdirect-1.0.so.0.1.0
b237f000-b2380000 r--p 00012000 08:02 6182967    /usr/lib/libdirect-1.0.so.0.1.0
b2380000-b2381000 rw-p 00013000 08:02 6182967    /usr/lib/libdirect-1.0.so.0.1.0
b2381000-b23e5000 r-xp 00000000 08:02 6182969    /usr/lib/libdirectfb-1.0.so.0.1.0
b23e5000-b23e6000 r--p 00063000 08:02 6182969    /usr/lib/libdirectfb-1.0.so.0.1.0
b23e6000-b23e7000 rw-p 00064000 08:02 6182969    /usr/lib/libdirectfb-1.0.so.0.1.0
b23e9000-b23ee000 r-xp 00000000 08:02 4046849    /usr/lib/gstreamer-0.10/libgstglimagesink.so
b23ee000-b23ef000 rw-p 00004000 08:02 4046849    /usr/lib/gstreamer-0.10/libgstglimagesink.so
b23ef000-b23f7000 r-xp 00000000 08:02 4047633    /usr/lib/gstreamer-0.10/libgstrtpjitterbuffer.so
b23f7000-b23f8000 r--p 00007000 08:02 4047633    /usr/lib/gstreamer-0.10/libgstrtpjitterbuffer.so
b23f8000-b23f9000 rw-p 00008000 08:02 4047633    /usr/lib/gstreamer-0.10/libgstrtpjitterbuffer.so
b23f9000-b2402000 r-xp 00000000 08:02 6176901    /usr/lib/gstreamer-0.10/libgstdvdspu.so
b2402000-b2403000 r--p 00008000 08:02 6176901    /usr/lib/gstreamer-0.10/libgstdvdspu.so
b2403000-b2404000 rw-p 00009000 08:02 6176901    /usr/lib/gstreamer-0.10/libgstdvdspu.so
b2404000-b245a000 r-xp 00000000 08:02 6179067    /usr/lib/libsndfile.so.1.0.17
b245a000-b245b000 rw-p 00056000 08:02 6179067    /usr/lib/libsndfile.so.1.0.17
b245b000-b2460000 rw-p b245b000 00:00 0 
b2462000-b2465000 r-xp 00000000 08:02 6177326    /usr/lib/gstreamer-0.10/libgstcdio.so
b2465000-b2466000 r--p 00002000 08:02 6177326    /usr/lib/gstreamer-0.10/libgstcdio.so
b2466000-b2467000 rw-p 00003000 08:02 6177326    /usr/lib/gstreamer-0.10/libgstcdio.so
b2467000-b246e000 r-xp 00000000 08:02 6183181    /usr/lib/libfusion-1.0.so.0.1.0
b246e000-b246f000 r--p 00006000 08:02 6183181    /usr/lib/libfusion-1.0.so.0.1.0
b246f000-b2470000 rw-p 00007000 08:02 6183181    /usr/lib/libfusion-1.0.so.0.1.0
b2470000-b247b000 r-xp 00000000 08:02 6176866    /usr/lib/gstreamer-0.10/libgstdfbvideosink.so
b247b000-b247c000 r--p 0000a000 08:02 6176866    /usr/lib/gstreamer-0.10/libgstdfbvideosink.so
b247c000-b247d000 rw-p 0000b000 08:02 6176866    /usr/lib/gstreamer-0.10/libgstdfbvideosink.so
b247d000-b248b000 r-xp 00000000 08:02 6182869    /usr/lib/libopenspc.so.0.0.3
b248b000-b248d000 rw-p 0000d000 08:02 6182869    /usr/lib/libopenspc.so.0.0.3
b248d000-b249d000 rw-p b248d000 00:00 0 
b249f000-b24aa000 r-xp 00000000 08:02 4047569    /usr/lib/gstreamer-0.10/libgstossaudio.so
b24aa000-b24ab000 r--p 0000a000 08:02 4047569    /usr/lib/gstreamer-0.10/libgstossaudio.so
b24ab000-b24ac000 rw-p 0000b000 08:02 4047569    /usr/lib/gstreamer-0.10/libgstossaudio.so
b24ac000-b24b2000 r-xp 00000000 08:02 6177177    /usr/lib/gstreamer-0.10/libgstsndfile.so
b24b2000-b24b3000 r--p 00006000 08:02 6177177    /usr/lib/gstreamer-0.10/libgstsndfile.so
b24b3000-b24b4000 rw-p 00007000 08:02 6177177    /usr/lib/gstreamer-0.10/libgstsndfile.so
b24b4000-b24b8000 r-xp 00000000 08:02 6177216    /usr/lib/gstreamer-0.10/libgstspeed.so
b24b8000-b24b9000 r--p 00003000 08:02 6177216    /usr/lib/gstreamer-0.10/libgstspeed.so
b24b9000-b24ba000 rw-p 00004000 08:02 6177216    /usr/lib/gstreamer-0.10/libgstspeed.so
b24ba000-b24c3000 r-xp 00000000 08:02 6178035    /usr/lib/libmms.so.0.0.2
b24c3000-b24c5000 rw-p 00009000 08:02 6178035    /usr/lib/libmms.so.0.0.2
b24c8000-b24d4000 r-xp 00000000 08:02 6176946    /usr/lib/gstreamer-0.10/libgstflvdemux.so
b24d4000-b24d5000 r--p 0000b000 08:02 6176946    /usr/lib/gstreamer-0.10/libgstflvdemux.so
b24d5000-b24d6000 rw-p 0000c000 08:02 6176946    /usr/lib/gstreamer-0.10/libgstflvdemux.so
b24d6000-b24d9000 r-xp 00000000 08:02 6177260    /usr/lib/gstreamer-0.10/libgstvcdsrc.so
b24d9000-b24da000 r--p 00002000 08:02 6177260    /usr/lib/gstreamer-0.10/libgstvcdsrc.so
b24da000-b24db000 rw-p 00003000 08:02 6177260    /usr/lib/gstreamer-0.10/libgstvcdsrc.so
b24db000-b24e0000 r-xp 00000000 08:02 6177195    /usr/lib/gstreamer-0.10/libgstspc.so
b24e0000-b24e1000 r--p 00004000 08:02 6177195    /usr/lib/gstreamer-0.10/libgstspc.so
b24e1000-b24e2000 rw-p 00005000 08:02 6177195    /usr/lib/gstreamer-0.10/libgstspc.so
b24e2000-b24e5000 r-xp 00000000 08:02 6177034    /usr/lib/gstreamer-0.10/libgstmms.so
b24e5000-b24e6000 r--p 00002000 08:02 6177034    /usr/lib/gstreamer-0.10/libgstmms.s

```

This thread: 

[http://ubuntuforums.org/showthread.php?t=1086378&highlight=songbird](http://ubuntuforums.org/showthread.php?t=1086378&highlight=songbird)

suggested removing the libvisual-0.4-plugins package, but this didn't work for me.

Anybody have any ideas?

---

### Post by oooh on 2010-01-20
Similar problem here :

(songbird-bin:2421): GLib-WARNING **: g_set_prgname() called multiple times
Bus error

I have no libvisual plugins by the way, so I can not uninstall them 

Ideas welcome !

---

