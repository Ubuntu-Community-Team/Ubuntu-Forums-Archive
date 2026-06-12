---
title: "MP4Box throws Buffer overflow"
date: 2011-04-26
forum: Multimedia Software
---

### Post by _mystery_ on 2011-04-26
Muxing my a MP4 file with MP4Box throws following error:

Command:
=========================================================
/usr/local/bin/MP4Box -add 18_temp.mp4#audio 18.m4v 2>&1

Output:
*** buffer overflow detected ***: /usr/local/bin/MP4Box terminated
======= Backtrace: =========
/lib/libc.so.6(__fortify_fail+0x37)[0x2b378b8fc217]
/lib/libc.so.6(+0xfe0d0)[0x2b378b8fb0d0]
/usr/lib/libgpac.so(chpl_New+0x39)[0x2b378ad0d189]
/usr/lib/libgpac.so(gf_isom_parse_box_ex+0x10e)[0x2b378ad2306e]
/usr/lib/libgpac.so(udta_Read+0x43)[0x2b378ad0e1f3]
/usr/lib/libgpac.so(gf_isom_parse_box_ex+0x293)[0x2b378ad231f3]
/usr/lib/libgpac.so(gf_isom_read_box_list_ex+0x35)[0x2b378ad23555]
/usr/lib/libgpac.so(gf_isom_parse_box_ex+0x293)[0x2b378ad231f3]
/usr/lib/libgpac.so(gf_isom_parse_root_box+0x4a)[0x2b378ad2364a]
/usr/lib/libgpac.so(gf_isom_parse_movie_boxes+0x6a)[0x2b378ad2947a]
/usr/lib/libgpac.so(gf_isom_open_file+0xcd)[0x2b378ad2982d]
/usr/lib/libgpac.so(gf_media_import+0x9f0)[0x2b378ada65a0]
/usr/local/bin/MP4Box[0x4184b3]
/usr/local/bin/MP4Box[0x408a2d]
/lib/libc.so.6(__libc_start_main+0xfd)[0x2b378b81bc4d]
/usr/local/bin/MP4Box[0x406df9]
======= Memory map: ========
00400000-00429000 r-xp 00000000 09:03 77225985                           /usr/local/bin/MP4Box
00628000-00629000 r--p 00028000 09:03 77225985                           /usr/local/bin/MP4Box
00629000-0062a000 rw-p 00029000 09:03 77225985                           /usr/local/bin/MP4Box
14159000-1417a000 rw-p 14159000 00:00 0                                  [heap]
2b378a9b1000-2b378a9d1000 r-xp 00000000 09:03 25503967                   /lib/ld-2.11.1.so
2b378a9d1000-2b378a9d6000 rw-p 2b378a9d1000 00:00 0
2b378abd0000-2b378abd1000 r--p 0001f000 09:03 25503967                   /lib/ld-2.11.1.so
2b378abd1000-2b378abd2000 rw-p 00020000 09:03 25503967                   /lib/ld-2.11.1.so

Version of my linux:
=================================
root@blue...:~#uname -a 
Linux Ubuntu 10.04 2.6.18-238.5.1.el5.028stab085.3 #1 SMP Mon Mar 21 20:05:12 MSK 2011 x86_64 GNU/Linux

root@blue...:~# MP4Box -version
MP4Box - GPAC version 0.4.5 (build 33)
GPAC Copyright: (c) Jean Le Feuvre 2000-2005
        (c) ENST 2005-200X

---

