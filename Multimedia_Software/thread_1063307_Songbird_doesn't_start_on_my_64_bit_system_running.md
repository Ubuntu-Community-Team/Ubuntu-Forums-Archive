---
title: "Songbird doesn't start on my 64 bit system running a 32 bit Ubuntu distro."
date: 2009-02-07
forum: Multimedia Software
---

### Post by AwesomeTux on 2009-02-07
I believe it has something to do with my system being 64 bit and my Ubuntu distro. running 32 bit. Something about gStreamer, but, I don't know what. Any suggestions?

Here's what I get when running it in a Terminal.

```
*** glibc detected *** ././songbird-bin: double free or corruption (out): 0xb215e2a0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7d4c3f4]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7d4e456]
/usr/lib/libvisual-0.4.so.0(visual_mem_free+0x21)[0xb1c62141]
/usr/lib/libvisual-0.4.so.0[0xb1c59407]
/usr/lib/libvisual-0.4.so.0(visual_plugin_get_list+0x73)[0xb1c595e3]
/usr/lib/libvisual-0.4.so.0(visual_init+0x291)[0xb1c68ec1]
/usr/lib/gstreamer-0.10/libgstlibvisual.so[0xb1cc21f4]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3da52c2]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_plugin_load_file+0x62f)[0xb3da5b79]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3db07ee]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_registry_scan_path+0x135)[0xb3db0993]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3d60a44]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3d60f30]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3d61589]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3d61b44]
/usr/lib/libglib-2.0.so.0(g_option_context_parse+0x5b3)[0xb6b4f7e3]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init_check+0xf1)[0xb3d5fd1b]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init+0x32)[0xb3d5fe25]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN18sbGStreamerService4InitEv+0x9ff)[0xb3cd6cf3]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3cdd8e1]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3ce4252]
/usr/share/Songbird/xulrunner/libxul.so[0xb7610449]
/usr/share/Songbird/xulrunner/libxul.so[0xb760f90b]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3ce12ef]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3ce1319]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3ce0ac5]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3cdc3a5]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN27sbGStreamerMediacoreFactory4InitEv+0x46)[0xb3cdcb5c]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3cdd841]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3ce4252]
/usr/share/Songbird/xulrunner/libxul.so[0xb7610449]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb4eb70f9]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb4eb7126]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb4eb69c1]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN8nsCOMPtrI19sbIMediacoreFactoryEC1ERK15nsCOMPtr_helper+0x2d)[0xb4ea38b5]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN18sbMediacoreManager4InitEv+0x1b7)[0xb4ea11e7]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb4ea1564]
/usr/share/Songbird/xulrunner/libxul.so[0xb75ed21f]
/usr/share/Songbird/xulrunner/libxul.so[0xb75ed7c4]
/usr/share/Songbird/xulrunner/libxul.so[0xb6e82a98]
/usr/share/Songbird/xulrunner/libxul.so(XRE_main+0x1aba)[0xb6e807b2]
././songbird-bin[0x8048f40]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7cf3685]
././songbird-bin[0x8048bb1]
======= Memory map: ========
08048000-0804e000 r-xp 00000000 08:05 465689     /usr/share/Songbird/songbird-bin
0804e000-0804f000 rw-p 00006000 08:05 465689     /usr/share/Songbird/songbird-bin
08e28000-08e49000 rw-p 08e28000 00:00 0          [heap]
b1c48000-b1c84000 r-xp 00000000 08:05 417610     /usr/lib/libvisual-0.4.so.0.0.0
b1c84000-b1c85000 r--p 0003b000 08:05 417610     /usr/lib/libvisual-0.4.so.0.0.0
b1c85000-b1c86000 rw-p 0003c000 08:05 417610     /usr/lib/libvisual-0.4.so.0.0.0
b1c9a000-b1cb0000 r-xp 00000000 08:05 416650     /usr/lib/libmpeg2.so.0.0.0
b1cb0000-b1cb1000 r--p 00015000 08:05 416650     /usr/lib/libmpeg2.so.0.0.0
b1cb1000-b1cb2000 rw-p 00016000 08:05 416650     /usr/lib/libmpeg2.so.0.0.0
b1cb2000-b1cb4000 rw-p b1cb2000 00:00 0 
b1cba000-b1cc0000 rw-p b1cba000 00:00 0 
b1cc0000-b1cc6000 r-xp 00000000 08:05 432809     /usr/lib/gstreamer-0.10/libgstlibvisual.so
b1cc6000-b1cc7000 r--p 00005000 08:05 432809     /usr/lib/gstreamer-0.10/libgstlibvisual.so
b1cc7000-b1cc8000 rw-p 00006000 08:05 432809     /usr/lib/gstreamer-0.10/libgstlibvisual.so
b1cc8000-b1cd4000 r-xp 00000000 08:05 448922     /usr/lib/i686/cmov/libpostproc.so.51.1.0
b1cd4000-b1cd5000 r--p 0000b000 08:05 448922     /usr/lib/i686/cmov/libpostproc.so.51.1.0
b1cd5000-b1cd6000 rw-p 0000c000 08:05 448922     /usr/lib/i686/cmov/libpostproc.so.51.1.0
b1cde000-b1ce8000 r-xp 00000000 08:05 434328     /usr/lib/gstreamer-0.10/libgstmpeg2dec.so
b1ce8000-b1ce9000 r--p 00009000 08:05 434328     /usr/lib/gstreamer-0.10/libgstmpeg2dec.so
b1ce9000-b1cea000 rw-p 0000a000 08:05 434328     /usr/lib/gstreamer-0.10/libgstmpeg2dec.so
b1cea000-b1cee000 r-xp 00000000 08:05 433618     /usr/lib/gstreamer-0.10/libgstpostproc.so
b1cee000-b1cef000 r--p 00003000 08:05 433618     /usr/lib/gstreamer-0.10/libgstpostproc.so
b1cef000-b1cf0000 rw-p 00004000 08:05 433618     /usr/lib/gstreamer-0.10/libgstpostproc.so
b1cf0000-b1cf9000 r-xp 00000000 08:05 212461     /usr/lib/gstreamer-0.10/libgstlame.so
b1cf9000-b1cfa000 r--p 00009000 08:05 212461     /usr/lib/gstreamer-0.10/libgstlame.so
b1cfa000-b1cfb000 rw-p 0000a000 08:05 212461     /usr/lib/gstreamer-0.10/libgstlame.so
b1cfb000-b1d05000 r-xp 00000000 08:05 433524     /usr/lib/gstreamer-0.10/libgstdvdread.so
b1d05000-b1d06000 r--p 00009000 08:05 433524     /usr/lib/gstreamer-0.10/libgstdvdread.so
b1d06000-b1d07000 rw-p 0000a000 08:05 433524     /usr/lib/gstreamer-0.10/libgstdvdread.so
b1d07000-b1d0f000 r-xp 00000000 08:05 434083     /usr/lib/gstreamer-0.10/libgstrfbsrc.so
b1d0f000-b1d10000 r--p 00007000 08:05 434083     /usr/lib/gstreamer-0.10/libgstrfbsrc.so
b1d10000-b1d11000 rw-p 00008000 08:05 434083     /usr/lib/gstreamer-0.10/libgstrfbsrc.so
b1d11000-b1d14000 r-xp 00000000 08:05 433826     /usr/lib/gstreamer-0.10/libgstgsm.so
b1d14000-b1d15000 r--p 00002000 08:05 433826     /usr/lib/gstreamer-0.10/libgstgsm.so
b1d15000-b1d16000 rw-p 00003000 08:05 433826     /usr/lib/gstreamer-0.10/libgstgsm.so
b1d16000-b1d1e000 r-xp 00000000 08:05 433755     /usr/lib/gstreamer-0.10/libgstdeinterlace2.so
b1d1e000-b1d1f000 r--p 00007000 08:05 433755     /usr/lib/gstreamer-0.10/libgstdeinterlace2.so
b1d1f000-b1d20000 rw-p 00008000 08:05 433755     /usr/lib/gstreamer-0.10/libgstdeinterlace2.so
b1d20000-b1d2d000 r-xp 00000000 08:05 434066     /usr/lib/gstreamer-0.10/libgstmpegtsparse.so
b1d2d000-b1d2e000 r--p 0000c000 08:05 434066     /usr/lib/gstreamer-0.10/libgstmpegtsparse.so
b1d2e000-b1d2f000 rw-p 0000d000 08:05 434066     /usr/lib/gstreamer-0.10/libgstmpegtsparse.so
b1d2f000-b1d45000 r-xp 00000000 08:05 416921     /usr/lib/libsasl2.so.2.0.22
b1d45000-b1d46000 r--p 00015000 08:05 416921     /usr/lib/libsasl2.so.2.0.22
b1d46000-b1d47000 rw-p 00016000 08:05 416921     /usr/lib/libsasl2.so.2.0.22
b1d47000-b1d53000 r-xp 00000000 08:05 418784     /usr/lib/liblber-2.4.so.2.1.0
b1d53000-b1d54000 r--p 0000b000 08:05 418784     /usr/lib/liblber-2.4.so.2.1.0
b1d54000-b1d55000 rw-p 0000c000 08:05 418784     /usr/lib/liblber-2.4.so.2.1.0
b1d55000-b1d94000 r-xp 00000000 08:05 418785     /usr/lib/libldap_r-2.4.so.2.1.0
b1d94000-b1d95000 r--p 0003e000 08:05 418785     /usr/lib/libldap_r-2.4.so.2.1.0
b1d95000-b1d96000 rw-p 0003f000 08:05 418785     /usr/lib/libldap_r-2.4.so.2.1.0
b1d96000-b1d97000 rw-p b1d96000 00:00 0 
b1d97000-b1dc7000 r-xp 00000000 08:05 418341     /usr/lib/libidn.so.11.5.37
b1dc7000-b1dc8000 r--p 00030000 08:05 418341     /usr/lib/libidn.so.11.5.37
b1dc8000-b1dc9000 rw-p 00031000 08:05 418341     /usr/lib/libidn.so.11.5.37
b1dc9000-b1dd2000 r-xp 00000000 08:05 156172     /lib/tls/i686/cmov/libcrypt-2.8.90.so
b1dd2000-b1dd3000 r--p 00008000 08:05 156172     /lib/tls/i686/cmov/libcrypt-2.8.90.so
b1dd3000-b1dd4000 rw-p 00009000 08:05 156172     /lib/tls/i686/cmov/libcrypt-2.8.90.so
b1dd4000-b1dfb000 rw-p b1dd4000 00:00 0 
b1dfb000-b1e34000 r-xp 00000000 08:05 416897     /usr/lib/libcurl-gnutls.so.4.1.0
b1e34000-b1e35000 r--p 00038000 08:05 416897     /usr/lib/libcurl-gnutls.so.4.1.0
b1e35000-b1e36000 rw-p 00039000 08:05 416897     /usr/lib/libcurl-gnutls.so.4.1.0
b1e36000-b1fd4000 r-xp 00000000 08:05 418777     /usr/lib/libmysqlclient.so.15.0.0
b1fd4000-b1fd5000 ---p 0019e000 08:05 418777     /usr/lib/libmysqlclient.so.15.0.0
b1fd5000-b1fd8000 r--p 0019e000 08:05 418777     /usr/lib/libmysqlclient.so.15.0.0
b1fd8000-b2018000 rw-p 001a1000 08:05 418777     /usr/lib/libmysqlclient.so.15.0.0
b2018000-b2019000 rw-p b2018000 00:00 0 
b2019000-b2039000 r-xp 00000000 08:05 418808     /usr/lib/libgmyth.so.0.0.0
b2039000-b203b000 rw-p 0001f000 08:05 418808     /usr/lib/libgmyth.so.0.0.0
b203b000-b203d000 r-xp 00000000 08:05 434222     /usr/lib/gstreamer-0.10/libgststereo.so
b203d000-b203e000 r--p 00001000 08:05 434222     /usr/lib/gstreamer-0.10/libgststereo.so
b203e000-b203f000 rw-p 00002000 08:05 434222     /usr/lib/gstreamer-0.10/libgststereo.so
b203f000-b2044000 r-xp 00000000 08:05 434068     /usr/lib/gstreamer-0.10/libgstmpegvideoparse.so
b2044000-b2045000 r--p 00005000 08:05 434068     /usr/lib/gstreamer-0.10/libgstmpegvideoparse.so
b2045000-b2046000 rw-p 00006000 08:05 434068     /usr/lib/gstreamer-0.10/libgstmpegvideoparse
```

Help would be much appreciated. I don't know much about gStreamer, Songbird, or 64 bit system software :)

---

### Post by jeperezd on 2009-02-19
I have the same issue. I post my output when I launch it on a Terminal. My system is an Intrepid 64 bits. I have been using Songbird before I had to reinstall due to a harddisk failure.

```
in10se@poseidon:~$ songbird 
*** glibc detected *** ././songbird-bin: free(): invalid pointer: 0x00007f74bcd770e0 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f74d8a7ea58]
/lib/libc.so.6(cfree+0x76)[0x7f74d8a810a6]
/usr/lib/libvisual-0.4.so.0(visual_mem_free+0xe)[0x7f74baa5f4ce]
/usr/lib/libvisual-0.4.so.0[0x7f74baa58646]
/usr/lib/libvisual-0.4.so.0(visual_plugin_get_list+0x48)[0x7f74baa587d8]
/usr/lib/libvisual-0.4.so.0(visual_init+0x243)[0x7f74baa65703]
/usr/lib64/gstreamer-0.10/libgstlibvisual.so[0x7f74bac86c24]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7f74c75422f6]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_plugin_load_file+0x64b)[0x7f74c7542baf]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7f74c754cf0d]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_registry_scan_path+0x11f)[0x7f74c754d090]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7f74c74fd7a5]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7f74c74fdc13]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7f74c74fe1cf]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7f74c74fe753]
/usr/lib/libglib-2.0.so.0(g_option_context_parse+0x528)[0x7f74d4e708e8]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init_check+0xd6)[0x7f74c74fcb56]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init+0x29)[0x7f74c74fcc43]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN18sbGStreamerService4InitEv+0xacc)[0x7f74c51a5068]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7f74c51aae79]
/usr/share/Songbird/xulrunner/libxul.so[0x7f74d69a660b]
/usr/share/Songbird/xulrunner/libxul.so[0x7f74d69a6155]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7f74c51ae217]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7f74c51ae244]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7f74c51ada2c]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7f74c51a9bca]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN27sbGStreamerMediacoreFactory4InitEv+0x4b)[0x7f74c51aa159]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7f74c51aade9]
/usr/share/Songbird/xulrunner/libxul.so[0x7f74d69a660b]
/usr/share/Songbird/components/sbMediacoreManager.so[0x7f74c9b7ca7f]
/usr/share/Songbird/components/sbMediacoreManager.so[0x7f74c9b7cabc]
/usr/share/Songbird/components/sbMediacoreManager.so[0x7f74c9b7c39e]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN8nsCOMPtrI19sbIMediacoreFactoryEC1ERK15nsCOMPtr_helper+0x1c)[0x7f74c9b6c364]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN18sbMediacoreManager4InitEv+0x1ff)[0x7f74c9b6a203]
/usr/share/Songbird/components/sbMediacoreManager.so[0x7f74c9b6a5d8]
/usr/share/Songbird/xulrunner/libxul.so[0x7f74d6986fea]
/usr/share/Songbird/xulrunner/libxul.so[0x7f74d69874bc]
/usr/share/Songbird/xulrunner/libxul.so[0x7f74d625d81e]
/usr/share/Songbird/xulrunner/libxul.so(XRE_main+0x184c)[0x7f74d625b500]
././songbird-bin[0x401417]
/lib/libc.so.6(__libc_start_main+0xe6)[0x7f74d8a23466]
././songbird-bin[0x401009]
======= Memory map: ========
00400000-00408000 r-xp 00000000 09:03 680140                             /usr/share/Songbird/songbird-bin
00608000-00609000 rw-p 00008000 09:03 680140                             /usr/share/Songbird/songbird-bin
01128000-01149000 rw-p 01128000 00:00 0                                  [heap]
4013c000-4013d000 ---p 4013c000 00:00 0 
4013d000-4093d000 rwxp 4013d000 00:00 0 
40d70000-40d71000 ---p 40d70000 00:00 0 
40d71000-41571000 rwxp 40d71000 00:00 0 
7f74b8ff3000-7f74b8ff4000 r-xp 00000000 09:03 16363                      /usr/lib/tls/libnvidia-tls.so.180.29
7f74b8ff4000-7f74b90f4000 ---p 00001000 09:03 16363                      /usr/lib/tls/libnvidia-tls.so.180.29
7f74b90f4000-7f74b90f5000 rw-p 00001000 09:03 16363                      /usr/lib/tls/libnvidia-tls.so.180.29
7f74baa46000-7f74baa83000 r-xp 00000000 09:03 728850                     /usr/lib/libvisual-0.4.so.0.0.0
7f74baa83000-7f74bac82000 ---p 0003d000 09:03 728850                     /usr/lib/libvisual-0.4.so.0.0.0
7f74bac82000-7f74bac83000 r--p 0003c000 09:03 728850                     /usr/lib/libvisual-0.4.so.0.0.0
7f74bac83000-7f74bac84000 rw-p 0003d000 09:03 728850                     /usr/lib/libvisual-0.4.so.0.0.0
7f74bac84000-7f74bac8a000 r-xp 00000000 09:03 730131                     /usr/lib/gstreamer-0.10/libgstlibvisual.so
7f74bac8a000-7f74bae89000 ---p 00006000 09:03 730131                     /usr/lib/gstreamer-0.10/libgstlibvisual.so
7f74bae89000-7f74bae8a000 r--p 00005000 09:03 730131                     /usr/lib/gstreamer-0.10/libgstlibvisual.so
7f74bae8a000-7f74bae8b000 rw-p 00006000 09:03 730131                     /usr/lib/gstreamer-0.10/libgstlibvisual.so
7f74bae8b000-7f74bae97000 r-xp 00000000 09:03 728600                     /usr/lib/libpostproc.so.51.2.0
7f74bae97000-7f74bb096000 ---p 0000c000 09:03 728600                     /usr/lib/libpostproc.so.51.2.0
7f74bb096000-7f74bb097000 rw-p 0000b000 09:03 728600                     /usr/lib/libpostproc.so.51.2.0
7f74bb097000-7f74bb0a1000 r-xp 00000000 09:03 728322                     /usr/lib/libavutil.so.49.14.0
7f74bb0a1000-7f74bb2a0000 ---p 0000a000 09:03 728322                     /usr/lib/libavutil.so.49.14.0
7f74bb2a0000-7f74bb2a1000 rw-p 00009000 09:03 728322                     /usr/lib/libavutil.so.49.14.0
7f74bb2a1000-7f74bb2a4000 rw-p 7f74bb2a1000 00:00 0 
7f74bb2a4000-7f74bb2a9000 r-xp 00000000 09:03 731841                     /usr/lib/gstreamer-0.10/libgstpostproc.so
7f74bb2a9000-7f74bb4a8000 ---p 00005000 09:03 731841                     /usr/lib/gstreamer-0.10/libgstpostproc.so
7f74bb4a8000-7f74bb4a9000 r--p 00004000 09:03 731841                     /usr/lib/gstreamer-0.10/libgstpostproc.so
7f74bb4a9000-7f74bb4aa000 rw-p 00005000 09:03 731841                     /usr/lib/gstreamer-0.10/libgstpostproc.so
7f74bb4aa000-7f74bb4b2000 r-xp 00000000 09:03 730142                     /usr/lib/gstreamer-0.10/libgstpng.so
7f74bb4b2000-7f74bb6b1000 ---p 00008000 09:03 730142                     /usr/lib/gstreamer-0.10/libgstpng.so
7f74bb6b1000-7f74bb6b2000 r--p 00007000 09:03 730142                     /usr/lib/gstreamer-0.10/libgstpng.so
7f74bb6b2000-7f74bb6b3000 rw-p 00008000 09:03 730142                     /usr/lib/gstreamer-0.10/libgstpng.so
7f74bb6b3000-7f74bb78f000 r-xp 00000000 09:03 728457                     /usr/lib/libxvidcore.so.4.1
7f74bb78f000-7f74bb98e000 ---p 000dc000 09:03 728457                     /usr/lib/libxvidcore.so.4.1
7f74bb98e000-7f74bb999000 rw-p 000db000 09:03 728457                     /usr/lib/libxvidcore.so.4.1
7f74bb999000-7f74bba03000 rw-p 7f74bb999000 00:00 0 
7f74bba03000-7f74bba0e000 r-xp 00000000 09:03 730281                     /usr/lib/gstreamer-0.10/libgstxvid.so
7f74bba0e000-7f74bbc0e000 ---p 0000b000 09:03 730281                     /usr/lib/gstreamer-0.10/libgstxvid.so
7f74bbc0e000-7f74bbc0f000 r--p 0000b000 09:03 730281                     /usr/lib/gstreamer-0.10/libgstxvid.so
7f74bbc0f000-7f74bbc10000 rw-p 0000c000 09:03 730281                     /usr/lib/gstreamer-0.10/libgstxvid.so
7f74bbc10000-7f74bbc15000 r-xp 00000000 09:03 691181                     /usr/share/Songbird/gst-plugins/libgstspectrum.so
7f74bbc15000-7f74bbe15000 ---p 00005000 09:03 691181                     /usr/share/Songbird/gst-plugins/libgstspectrum.so
7f74bbe15000-7f74bbe16000 rw-p 00005000 09:03 691181                     /usr/share/Songbird/gst-plugins/libgstspectrum.so
7f74bbe16000-7f74bbf7d000 r-xp 00000000 09:03 691224                     /usr/share/Songbird/gst-plugins/libgstflump3dec.so
7f74bbf7d000-7f74bc07c000 ---p 00167000 09:03 691224                     /usr/share/Songbird/gst-plugins/libgstflump3dec.so
7f74bc07c000-7f74bc082000 rw-p 00166000 09:03 691224                     /usr/share/Songbird/gst-plugins/libgstflump3dec.so
7f74bc082000-7f74bc0a5000 r-xp 00000000 09:03 691178                     /usr/share/Songbird/gst-plugins/libgstogg.so
7f74bc0a5000-7f74bc2a5000 ---p 00023000 09:03 691178                     /usr/share/Songbird/gst-plugins/libgstogg.so
7f74bc2a5000-7f74bc2a7000 rw-p 00023000 09:03 691178                     /usr/share/Songbird/gst-plugins/libgstogg.so
7f74bc2a7000-7f74bc2ad000 r-xp 00000000 09:03 691192                     /usr/share/Songbird/gst-plugins/libgstvideobox.so
7f74bc2ad000-7f74bc4ad000 ---p 00006000 09:03 691192                     /usr/share/Songbird/gst-plugins/libgstvideobox.so
7f74bc4ad000-7f74bc4ae000 rw-p 00006000 09:03 691192                     /usr/share/Songbird/gst-plugins/libgstvideobox.so
7f74bc4ae000-7f74bc4c3000 r-xp 00000000 09:03 691232                     /usr/share/Songbird/gst-plugins/libgstmozillasrc.so
7f74bc4c3000-7f74bc6c2000 ---p 00015000 09:03 691232                     /usr/share/Songbird/gst-plugins/libgstmozillasrc.so
7f74bc6c2000-7f74bc6c4000 rw-p 00014000 09:03 691232                     /usr/share/Songbird/gst-plugins/libgstmozillasrc.so
7f74bc6c4000-7f74bc6c9000 r-xp 00000000 09:03 691213                     /usr/share/Songbird/gst-plugins/libgstcutter.so
7f74bc6c9000-7f74bc8c8000 ---p 00005000 09:03 691213                     /usr/share/Songbird/gst-plugins/libgstcutter.so
7f74bc8c8000-7f74bc8c9000 rw-p 00004000 09:03 691213                     /usr/share/Songbird/gst-plugins/libgstcutter.so
7f74bc8c9000-7f74bc8d3000 r-xp 00000000 09:03 691177                     /usr/share/Songbird/gst-plugins/libgstvideotestsrc.so
7f74bc8d3000-7f74bcad2000 ---p 0000a000 09:03 691177                     /usr/share/Songbird/gst-plugins/libgstvideotestsrc.so
7f74bcad2000-7f74bcad4000 rw-p 00009000 09:03 691177                     /usr/share/Songbird/gst-plugins/libgstvideotestsrc.so
7f74bcad4000-7f74bcaff000 r-xp 00000000 09:03 691216                     /usr/share/Songbird/gst-plugins/libgstplaybin.so
7f74bcaff000-7f74bccfe000 ---p 0002b000 09:03 691216                     /usr/share/Songbird/gst-plugins/libgstplaybin.so
7f74bccfe000-7f74bcd00000 rw-p 0002a000 09:03 691216                     /usr/share/Songbird/gst-plugins/libgstplaybin.so
7f74bcd00000-7f74bce00000 rw-p 7f74bcd00000 00:00 0 
7f74bce44000-7f74bce48000 r-xp 00000000 09:03 691230                     /usr/share/Songbird/gst-plugins/libgstapetag.so
7f74bce48000-7f74bd047000 ---p 00004000 09:03 691230                     /usr/share/Songbird/gst-plugins/libgstapetag.so
7f74bd047000-7f74bd048000 rw-p 00003000 09:03 691230                     /usr/share/Songbird/gst-plugins/libgstapetag.so
7f74bd048000-7f74bd056000 r-xp 00000000 09:03 691191                     /usr/share/Songbird/gst-plugins/libgsttypefindfunctions.so
7f74bd056000-7f74bd256000 ---p 0000e000 09:03 691191                     /usr/share/Songbird/gst-plugins/libgsttypefindfunctions.so
7f74bd256000-7f74bd259000 rw-p 0000e000 09:03 691191                     /usr/share/Songbird/gst-plugins/libgsttypefindfunctions.so
7f74bd259000-7f74bd277000 r-xp 00000000 09:03 691208                     /usr/share/Songbird/gst-plugins/libgstasf.so
7f74bd277000-7f74bd476000 ---p 0001e000 09:03 691208                     /usr/share/Songbird/gst-plugins/libgstasf.so
7f74bd476000-7f74bd478000 rw-p 0001d000 09:03 691208                     /usr/share/Songbird/gst-plugins/libgstasf.so
7f74bd478000-7f74bd488000 r-xp 00000000 09:03 691173                     /usr/share/Songbird/gst-plugins/libgstsmpte.so
7f74bd488000-7f74bd687000 ---p 00010000 09:03 691173                     /usr/share/Songbird/gst-plugins/libgstsmpte.so
7f74bd687000-7f74bd689000 rw-p 0000f000 09:03 691173                     /usr/share/Songbird/gst-plugins/libgstsmpte.so
7f74bd689000-7f74bd699000 r-xp 00000000 09:03 691167                     /usr/share/Songbird/gst-plugins/libgstmpegaudioparse.so
7f74bd699000-7f74bd899000 ---p 00010000 09:03 691167                     /usr/share/Songbird/gst-plugins/libgstmpegaudioparse.so
7f74bd899000-7f74bd89a000 rw-p 00010000 09:03 691167                     /usr/share/Songbird/gst-plugins/libgstmpegaudioparse.so
7f74bd89a000-7f74bd8ac000 r-xp 00000000 09:03 691222                     /usr/share/Songbird/gst-plugins/libgstflac.so
7f74bd8ac000-7f74bdaac000 ---p 00012000 09:03 691222                     /usr/share/Songbird/gst-plugins/libgstflac.so
7f74bdaac000-7f74bdaad000 rw-p 00012000 09:03 691222                     /usr/share/Songbird/gst-plugins/libgstflac.so
7f74bdaad000-7f74bdab2000 r-xp 00000000 09:03 691211                     /usr/share/Songbird/gst-plugins/libgstvolume.so
7f74bdab2000-7f74bdcb1000 ---p 00005000 09:03 691211                     /usr/share/Songbird/gst-plugins/libgstvolume.so
7f74bdcb1000-7f74bdcb2000 rw-p 00004000 09:03 691211                     /usr/share/Songbird/gst-plugins/libgstvolume.so
7f74bdcb2000-7f74bdcbf000 r-xp 00000000 09:03 691205                     /usr/share/Songbird/gst-plugins/libgstximagesink.so
7f74bdcbf000-7f74bdebf000 ---p 0000d000 09:03 691205                     /usr/share/Songbird/gst-plugins/libgstximagesink.so
7f74bdebf000-7f74bdec0000 rw-p 0000d000 09:03 691205                     /usr/share/Songbird/gst-plugins/libgstximagesink.so
7f74bdec0000-7f74bdee8000 r-xp 00000000 09:03 691193                     /usr/share/Songbird/gst-plugins/libgstqtdemux.so
7f74bdee8000-7f74be0e8000 ---p 00028000 09:03 691193                     /usr/share/Songbird/gst-plugins/libgstqtdemux.so
7f74be0e8000-7f74be0ea000 rw-p 00028000 09:03 691193                     /usr/share/Songbird/gst-plugins/libgstqtdemux.so
7f74be0ea000-7f74be0ef000 r-xp 00000000 09:03 691182                     /usr/share/Songbird/gst-plugins/libgstflxdec.so
7f74be0ef000-7f74be2ee000 ---p 00005000 09:03 691182                     /usr/share/Songbird/gst-plugins/libgstflxdec.so
7f74be2ee000-7f74be2ef000 rw-p 00004000 09:03 691182                     /usr/share/Songbird/gst-plugins/libgstflxdec.so
7f74be2ef000-7f74be309000 r-xp 00000000 09:03 691185                     /usr/share/Songbird/gst-plugins/libgstalsa.so
7f74be309000-7f74be509000 ---p 0001a000 09:03 691185                     /usr/share/Songbird/gst-plugins/libgstalsa.so
7f74be509000-7f74be50a000 rw-p 0001a000 09:03 691185                     /usr/share/Songbird/gst-plugins/libgstalsa.so
7f74be50a000-7f74be517000 r-xp 00000000 09:03 691176                     /usr/share/Songbird/gst-plugins/libgstudp.so
7f74be517000-7f74be717000 ---p 0000d000 09:03 691176                     /usr/share/Songbird/gst-plugins/libgstudp.so
7f74be717000-7f74be718000 rw-p 0000d000 09:03 691176                     /usr/share/Songbird/gst-plugins/libgstudp.so
7f74be718000-7f74be722000 r-xp 00000000 09:03 691212                     /usr/share/Songbird/gst-plugins/libgsteffectv.so
7f74be722000-7f74be921000 ---p 0000a000 09:03 691212                     /usr/share/Songbird/gst-plugins/libgsteffectv.so
7f74be921000-7f74be923000 rw-p 00009000 09:03 691212                     /usr/share/Songbird/gst-plugins/libgsteffectv.so
7f74be923000-7f74be93f000 r-xp 00000000 09:03 691189                     /usr/share/Songbird/gst-plugins/libgstrtsp.so
7f74be93f000-7f74beb3e000 ---p 0001c000 09:03 691189                     /usr/share/Songbird/gst-plugins/libgstrtsp.so
7f74beb3e000-7f74beb40000 rw-p 0001b000 09:03 691189                     /usr/share/Songbird/gst-plugins/libgstrtsp.so
7f74beb40000-7f74beb43000 r-xp 00000000 09:03 691183                     /usr/share/Songbird/gst-plugins/libgstalphacolor.so
7f74beb43000-7f74bed42000 ---p 00003000 09:03 691183                     /usr/share/Songbird/gst-plugins/libgstalphacolor.so
7f74bed42000-7f74bed43000 rw-p 00002000 09:03 691183                     /usr/share/Songbird/gst-plugins/libgstalphacolor.so
7f74bed43000-7f74bed4d000 r-xp 00000000 09:03 691214                     /usr/share/Songbird/gst-plugins/libgstreplaygain.so
7f74bed4d000-7f74bef4d000 ---p 0000a000 09:03 691214                     /usr/share/Songbird/gst-plugins/libgstreplaygain.so
7f74bef4d000-7f74bef4e000 rw-p 0000a000 09:03 691214                     /usr/share/Songbird/gst-plugins/libgstreplaygain.so
7f74bef4e000-7f74bef52000 r-xp 00000000 09:03 691172                     /usr/share/Songbird/gst-plugins/libgstalaw.so
7f74bef52000-7f74bf152000 ---p 00004000 09:03 691172                     /usr/share/Songbird/gst-plugins/libgstalaw.so
7f74bf152000-7f74bf153000 rw-p 00004000 09:03 691172                     /usr/share/Songbird/gst-plugins/libgstalaw.so
7f74bf153000-7f74bf158000 r-xp 00000000 09:03 691187                     /usr/share/Songbird/gst-plugins/libgstvideoflip.so
7f74bf158000-7f74bf357000 ---p 00005000 09:03 691187                     /usr/share/Songbird/gst-plugins/libgstvideoflip.so
7f74bf357000-7f74bf358000 rw-p 00004000 09:03 691187                     /usr/share/Songbird/gst-plugins/libgstvideoflip.so
7f74bf358000-7f74bf373000 r-xp 00000000 09:03 691174                     /usr/share/Songbird/gst-plugins/libgstaudiofx.so
7f74bf373000-7f74bf573000 ---p 0001b000 09:03 691174                     /usr/share/Songbird/gst-plugins/libgstaudiofx.so
7f74bf573000-7f74bf574000 rw-p 0001b000 09:03 691174                     /usr/share/Songbird/gst-plugins/libgstaudiofx.so
7f74bf574000-7f74bf580000 r-xp 00000000 09:03 691228                     /usr/share/Songbird/gst-plugins/libgstaudioresample.so
7f74bf580000-7f74bf77f000 ---p 0000c000 09:03 691228                     /usr/share/Songbird/gst-plugins/libgstaudioresample.so
7f74bf77f000-7f74bf780000 rw-p 0000b000 09:03 691228                     /usr/share/Songbird/gst-plugins/libgstaudioresample.so
7f74bf780000-7f74bf784000 r-xp 00000000 09:03 728392                     /usr/lib/libXv.so.1.0.0
7f74bf784000-7f74bf984000 ---p 00004000 09:03 728392                     /usr/lib/libXv.so.1.0.0
7f74bf984000-7f74bf985000 r--p 00004000 09:03 728392                     /usr/lib/libXv.so.1.0.0
7f74bf985000-7f74bf986000 rw-p 00005000 09:03 728392                     /usr/lib/libXv.so.1.0.0
7f74bf986000-7f74bf998000 r-xp 00000000 09:03 691171                     /usr/share/Songbird/gst-plugins/libgstxvimagesink.so
7f74bf998000-7f74bfb98000 ---p 00012000 09:03 691171                     /usr/share/Songbird/gst-plugins/libgstxvimagesink.so
7f74bfb98000-7f74bfb99000 rw-p 00012000 09:03 691171                     /usr/share/Songbird/gst-plugins/libgstxvimagesink.so
7f74bfb99000-7f74bfba3000 r-xp 00000000 09:03 691197                     /usr/share/Songbird/gst-plugins/libgstid3demux.so
7f74bfba3000-7f74bfda3000 ---p 0000a000 09:03 691197                     /usr/share/Songbird/gst-plugins/libgstid3demux.so
7f74bfda3000-7f74bfda4000 rw-p 0000a000 09:03 691197                     /usr/share/Songbird/gst-plugins/libgstid3demux.so
7f74bfda4000-7f74bfda9000 r-xp 00000000 09:03 691190                     /usr/share/Songbird/gst-plugins/libgstalpha.so
7f74bfda9000-7f74bffa9000 ---p 00005000 09:03 691190                     /usr/share/Songbird/gst-plugins/libgstalpha.so
7f74bffa9000-7f74bffaa000 rw-p 00005000 09:03 691190                     /usr/share/Songbird/gst-plugins/libgstalpha.so
7f74bffaa000-7f74bffb1000 r-xp 00000000 09:03 691198                     /usr/share/Songbird/gst-plugins/libgstequalizer.so
7f74bffb1000-7f74c01b0000 ---p 00007000 09:03 691198                     /usr/share/Songbird/gst-plugins/libgstequalizer.so
7f74c01b0000-7f74c01b1000 rw-p 00006000 09:03 691198                     /usr/share/Songbird/gst-plugins/libgstequalizer.so
7f74c01b1000-7f74c01e1000 r-xp 00000000 09:03 691225                     /usr/share/Songbird/gst-plugins/libgstcoreelements.so
7f74c01e1000-7f74c03e0000 ---p 00030000 09:03 691225                     /usr/share/Songbird/gst-plugins/libgstcoreelements.so
7f74c03e0000-7f74c03e2000 rw-p 0002f000 09:03 691225                     /usr/share/Songbird/gst-plugins/libgstcoreelements.so
7f74c03e2000-7f74c03e5000 r-xp 00000000 09:02 15979                      /lib/libcap.so.1.10
7f74c03e5000-7f74c05e5000 ---p 00003000 09:02 15979                      /lib/libcap.so.1.10
7f74c05e5000-7f74c05e6000 rw-p 00003000 09:02 15979                      /lib/libcap.so.1.10
7f74c05e6000-7f74c0634000 r-xp 00000000 09:03 729614                     /usr/lib/libpulse.so.0.4.1
7f74c0634000-7f74c0834000 ---p 0004e000 09:03 729614                     /usr/lib/libpulse.so.0.4.1
7f74c0834000-7f74c0835000 r--p 0004e000 09:03 729614                     /usr/lib/libpulse.so.0.4.1
7f74c0835000-7f74c0836000 rw-p 0004f000 09:03 729614                     /usr/lib/libpulse.so.0.4.1
7f74c0836000-7f74c0845000 r-xp 00000000 09:03 691217

```

---

### Post by Yellow Pasque on 2009-02-19
Songbird isn't a part of the Ubuntu repositories, so you should probably let us know where you got songbird from (compiled from source, downloaded a .deb, etc.)

> I believe it has something to do with my system being 64 bit and my Ubuntu distro. running 32 bit.
Very unlikely. 64-bit processors have the exact same x86 architecture at their core and only use 64-bit register/instruction extensions when running a 64-bit OS/software.

---

### Post by jeperezd on 2009-02-19
Hello,

I used the Getdeb  package. Sorry if this is not the correct place to report the problem, but as I say before the same package version (64bit) worked with no issues in my previous installation of Intrepid 64 (same computer only changing to new harddisk)

Thanks in advance

---

### Post by Yellow Pasque on 2009-02-19
Just to clarify: My 64-bit comment was directed to AwesomeTux.
There are other people reporting similar problems with the package: [http://www.getdeb.net/comment/1635](http://www.getdeb.net/comment/1635)
My advice would be to make sure you're using the latest stable version of songbird (1.0.0), and if you're still having issues, report them on songbird's bug tracker: [http://bugzilla.songbirdnest.com/](http://bugzilla.songbirdnest.com/)

---

### Post by AwesomeTux on 2009-02-24
Hello,

Sorry for delay. Temüjin, I downloaded the .deb file from getdeb.net, it didn't work, I also downloaded the tarball from getsongbird.com, it also didn't work. Like it shows in the code, it is primarily complaining about the gStreamer, I'm not saying that's the problem, but, it normally fixes these kinds of problems if I fix what it's complaining about.

---

### Post by AwesomeTux on 2009-03-23
Really? no more help :( I want Songbird.

---

### Post by mpurses on 2009-03-23
try:

sudo apt-get remove libvisual-0.4-plugins

---

### Post by AwesomeTux on 2009-03-24
> **mpurses said:**
> try:

sudo apt-get remove libvisual-0.4-plugins

Thank you so much. That did it! But, would I be able to re-install libvisual-0.4-plugins and have Songbird work some how?

---

### Post by mpurses on 2009-03-24
yes you can reinstall it...

head over here for more info:
[http://getsatisfaction.com/songbird/topics/glibc_2_8_detects_invalid_free_pointer](http://getsatisfaction.com/songbird/topics/glibc_2_8_detects_invalid_free_pointer)

---

