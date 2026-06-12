---
title: "handbrake problems"
date: 2012-06-16
forum: Multimedia Software
---

### Post by irishetalon007 on 2012-06-16
I'm having problems with handbrake. any help is greatly appreciated.

I have a fresh install of 12.04, fully up-to-date.

I can start handbrake fine. I click source, click my DVD iso, it starts loading titles, it gets to the last title and then the program just ends.

I've tried both dvdnav and libdvdread. 

I'm trying to rip the dvd collection I have for my HTPC running ubuntu. I ripped the iso's using k9copy.

Here's the output when I open handbrake using a terminal:

```
*** glibc detected *** ghb: free(): invalid pointer: 0x00007f5d6c000078 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x7e626)[0x7f5d98035626]
ghb[0x9ee89e]
ghb[0x4957d2]
ghb[0x4b6bb5]
ghb[0x4b172b]
/lib/x86_64-linux-gnu/libpthread.so.0(+0x7e9a)[0x7f5d9ae73e9a]
/lib/x86_64-linux-gnu/libc.so.6(clone+0x6d)[0x7f5d980a94bd]
======= Memory map: ========
00400000-0161c000 r-xp 00000000 08:07 391727                             /usr/bin/ghb
0181b000-0181c000 r--p 0121b000 08:07 391727                             /usr/bin/ghb
0181c000-01853000 rw-p 0121c000 08:07 391727                             /usr/bin/ghb
01853000-01e5a000 rw-p 00000000 00:00 0 
0312d000-03b3e000 rw-p 00000000 00:00 0                                  [heap]
7f5d5c000000-7f5d5c021000 rw-p 00000000 00:00 0 
7f5d5c021000-7f5d60000000 ---p 00000000 00:00 0 
7f5d60000000-7f5d60022000 rw-p 00000000 00:00 0 
7f5d60022000-7f5d64000000 ---p 00000000 00:00 0 
7f5d6659a000-7f5d665fa000 rw-s 00000000 00:04 4587535                    /SYSV00000000 (deleted)
7f5d665fa000-7f5d665fc000 r-xp 00000000 08:07 784132                     /usr/lib/x86_64-linux-gnu/gconv/ISO8859-1.so
7f5d665fc000-7f5d667fb000 ---p 00002000 08:07 784132                     /usr/lib/x86_64-linux-gnu/gconv/ISO8859-1.so
7f5d667fb000-7f5d667fc000 r--p 00001000 08:07 784132                     /usr/lib/x86_64-linux-gnu/gconv/ISO8859-1.so
7f5d667fc000-7f5d667fd000 rw-p 00002000 08:07 784132                     /usr/lib/x86_64-linux-gnu/gconv/ISO8859-1.so
7f5d667fd000-7f5d667fe000 ---p 00000000 00:00 0 
7f5d667fe000-7f5d66ffe000 rw-p 00000000 00:00 0 
7f5d66ffe000-7f5d66fff000 ---p 00000000 00:00 0 
7f5d66fff000-7f5d677ff000 rw-p 00000000 00:00 0 
7f5d677ff000-7f5d67800000 ---p 00000000 00:00 0 
7f5d67800000-7f5d68000000 rw-p 00000000 00:00 0 
7f5d68000000-7f5d68022000 rw-p 00000000 00:00 0 
7f5d68022000-7f5d6c000000 ---p 00000000 00:00 0 
7f5d6c000000-7f5d6c7aa000 rw-p 00000000 00:00 0 
7f5d6c7aa000-7f5d70000000 ---p 00000000 00:00 0 
7f5d70000000-7f5d70022000 rw-p 00000000 00:00 0 
7f5d70022000-7f5d74000000 ---p 00000000 00:00 0 
7f5d74000000-7f5d74022000 rw-p 00000000 00:00 0 
7f5d74022000-7f5d78000000 ---p 00000000 00:00 0 
7f5d78000000-7f5d78022000 rw-p 00000000 00:00 0 
7f5d78022000-7f5d7c000000 ---p 00000000 00:00 0 
7f5d7c055000-7f5d7c0b5000 rw-s 00000000 00:04 4554766                    /SYSV00000000 (deleted)
7f5d7c0b5000-7f5d7c0bd000 r-xp 00000000 08:07 396540                     /usr/lib/libdvdcss.so.2.1.0
7f5d7c0bd000-7f5d7c2bc000 ---p 00008000 08:07 396540                     /usr/lib/libdvdcss.so.2.1.0
7f5d7c2bc000-7f5d7c2bd000 r--p 00007000 08:07 396540                     /usr/lib/libdvdcss.so.2.1.0
7f5d7c2bd000-7f5d7c2be000 rw-p 00008000 08:07 396540                     /usr/lib/libdvdcss.so.2.1.0
7f5d7c2be000-7f5d7c2fe000 r-xp 00000000 08:07 784261                     /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstcoreelements.so
7f5d7c2fe000-7f5d7c4fe000 ---p 00040000 08:07 784261                     /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstcoreelements.so
7f5d7c4fe000-7f5d7c4ff000 r--p 00040000 08:07 784261                     /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstcoreelements.so
7f5d7c4ff000-7f5d7c501000 rw-p 00041000 08:07 784261                     /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstcoreelements.so
7f5d7c501000-7f5d7c52e000 r-xp 00000000 08:07 400025                     /usr/lib/x86_64-linux-gnu/libgconf-2.so.4.1.5
7f5d7c52e000-7f5d7c72d000 ---p 0002d000 08:07 400025                     /usr/lib/x86_64-linux-gnu/libgconf-2.so.4.1.5
7f5d7c72d000-7f5d7c72e000 r--p 0002c000 08:07 400025                     /usr/lib/x86_64-linux-gnu/libgconf-2.so.4.1.5
7f5d7c72e000-7f5d7c72f000 rw-p 0002d000 08:07 400025                     /usr/lib/x86_64-linux-gnu/libgconf-2.so.4.1.5
7f5d7c72f000-7f5d7c736000 r-xp 00000000 08:07 784278                     /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstgconfelements.so
7f5d7c736000-7f5d7c935000 ---p 00007000 08:07 784278                     /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstgconfelements.so
7f5d7c935000-7f5d7c936000 r--p 00006000 08:07 784278                     /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstgconfelements.so
7f5d7c936000-7f5d7c937000 rw-p 00007000 08:07 784278                     /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstgconfelements.so
7f5d7c937000-7f5d7c976000 r-xp 00000000 08:07 784305                     /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstplaybin.so
7f5d7c976000-7f5d7cb76000 ---p 0003f000 08:07 784305                     /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstplaybin.so
7f5d7cb76000-7f5d7cb77000 r--p 0003f000 08:07 784305                     /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstplaybin.so
7f5d7cb77000-7f5d7cb79000 rw-p 00040000 08:07 784305                     /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstplaybin.so
7f5d7cb79000-7f5d7cbbd000 r-xp 00000000 08:07 400150                     /usr/lib/x86_64-linux-gnu/libibus-1.0.so.0.401.0
7f5d7cbbd000-7f5d7cdbc000 ---p 00044000 08:07 400150                     /usr/lib/x86_64-linux-gnu/libibus-1.0.so.0.401.0
7f5d7cdbc000-7f5d7cdbe000 r--p 00043000 08:07 400150                     /usr/lib/x86_64-linux-gnu/libibus-1.0.so.0.401.0
7f5d7cdbe000-7f5d7cdbf000 rw-p 00045000 08:07 400150                     /usr/lib/x86_64-linux-gnu/libibus-1.0.so.0.401.0
7f5d7cdbf000-7f5d7cdc0000 rw-p 00000000 00:00 0 
7f5d7cdc0000-7f5d7cdc1000 ---p 00000000 00:00 0 
7f5d7cdc1000-7f5d7d5c1000 rw-p 00000000 00:00 0 
7f5d7ddc2000-7f5d7ddc3000 ---p 00000000 00:00 0 
7f5d7ddc3000-7f5d7e5c3000 rw-p 00000000 00:00 0 
7f5d7edc4000-7f5d7edc5000 ---p 00000000 00:00 0 
7f5d7edc5000-7f5d7f5c5000 rw-p 00000000 00:00 0 
7f5d7f5c5000-7f5d7f5c6000 ---p 00000000 00:00 0 
7f5d7f5c6000-7f5d7fdc6000 rw-p 00000000 00:00 0 
7f5d7fdc6000-7f5d7fdfd000 r-xp 00000000 08:07 399939                     /usr/lib/x86_64-linux-gnu/libcroco-0.6.so.3.0.1
7f5d7fdfd000-7f5d7fffc000 ---p 00037000 08:07 399939                     /usr/lib/x86_64-linux-gnu/libcroco-0.6.so.3.0.1
7f5d7fffc000-7f5d7ffff000 r--p 00036000 08:07 399939                     /usr/lib/x86_64-linux-gnu/libcroco-0.6.so.3.0.1
7f5d7ffff000-7f5d80000000 rw-p 00039000 08:07 399939                     /usr/lib/x86_64-linux-gnu/libcroco-0.6.so.3.0.1
7f5d80000000-7f5d80022000 rw-p 00000000 00:00 0 
7f5d80022000-7f5d84000000 ---p 00000000 00:00 0 
7f5d84000000-7f5d84022000 rw-p 00000000 00:00 0 
7f5d84022000-7f5d88000000 ---p 00000000 00:00 0 
7f5d8801b000-7f5d88021000 r-xp 00000000 08:07 784364                     /usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
7f5d88021000-7f5d88220000 ---p 00006000 08:07 784364                     /usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
7f5d88220000-7f5d88221000 r--p 00005000 08:07 784364                     /usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
7f5d88221000-7f5d88222000 rw-p 00006000 08:07 784364                     /usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
7f5d88222000-7f5d88256000 r-xp 00000000 08:07 400309                     /usr/lib/x86_64-linux-gnu/librsvg-2.so.2.36.1
7f5d88256000-7f5d88455000 ---p 00034000 08:07 400309                     /usr/lib/x86_64-linux-gnu/librsvg-2.so.2.36.1
7f5d88455000-7f5d88456000 r--p 00033000 08:07 400309                     /usr/lib/x86_64-linux-gnu/librsvg-2.so.2.36.1
7f5d88456000-7f5d88457000 rw-p 00034000 08:07 400309                     /usr/lib/x86_64-linux-gnu/librsvg-2.so.2.36.1
7f5d88457000-7f5d88459000 r-xp 00000000 08:07 784212                     /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
7f5d88459000-7f5d88658000 ---p 00002000 08:07 784212                     /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
7f5d88658000-7f5d88659000 r--p 00001000 08:07 784212                     /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
7f5d88659000-7f5d8865a000 rw-p 00002000 08:07 784212                     /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
7f5d8865a000-7f5d89d95000 r--p 00000000 08:07 1306694                    /usr/share/icons/hicolor/icon-theme.cache
7f5d89d95000-7f5d8a67f000 r--p 00000000 08:07 1306490                    /usr/share/icons/gnome/icon-theme.cache
7f5d8a67f000-7f5d8a768000 r--p 00000000 08:07 1325761                    /usr/share/icons/Humanity/icon-theme.cache
7f5d8a768000-7f5d8a778000 r-xp 00000000 08:07 784224                     /usr/lib/x86_64-linux-gnu/gio/modules/libgioremote-volume-monitor.so
7f5d8a778000-7f5d8a977000 ---p 00010000 08:07 784224                     /usr/lib/x86_64-linux-gnu/gio/modules/libgioremote-volume-monitor.so
7f5d8a977000-7f5d8a978000 r--p 0000f000 08:07 784224                     /usr/lib/x86_64-linux-gnu/gio/modules/libgioremote-volume-monitor.so
7f5d8a978000-7f5d8a979000 rw-p 00010000 08:07 784224                     /usr/lib/x86_64-linux-gnu/gio/modules/libgioremote-volume-monitor.so
7f5d8a979000-7f5d8a98f000 r-xp 00000000 08:07 784424                     /usr/lib/x86_64-linux-gnu/gvfs/libgvfscommon.so
7f5d8a98f000-7f5d8ab8e000 ---p 00016000 08:07 784424                     /usr/lib/x86_64-linux-gnu/gvfs/libgvfscommon.so
7f5d8ab8e000-7f5d8ab8f000 r--p 00015000 08:07 784424                     /usr/lib/x86_64-linux-gnu/gvfs/libgvfscommon.so
7f5d8ab8f000-7f5d8ab90000 rw-p 00016000 08:07 784424                     /usr/lib/x86_64-linux-gnu/gvfs/libgvfscommon.so
7f5d8ab90000-7f5d8abb8000 r-xp 00000000 08:07 784225                     /usr/lib/x86_64-linux-gnu/gio/modules/libgvfsdbus.so
7f5d8abb8000-7f5d8adb7000 ---p 00028000 08:07 784225                     /usr/lib/x86_64-linux-gnu/gio/modules/libgvfsdbus.so
7f5d8adb7000-7f5d8adb8000 r--p 00027000 08:07 784225                     /usr/lib/x86_64-linux-gnu/gio/modules/libgvfsdbus.so
7f5d8adb8000-7f5d8adb9000 rw-p 00028000 08:07 784225                     /usr/lib/x86_64-linux-gnu/gio/modules/libgvfsdbus.so
7f5d8adb9000-7f5d8adbb000 r-xp 00000000 08:07 790878                     /usr/lib/x86_64-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
7f5d8adbb000-7f5d8afba000 ---p 00002000 08:07 790878                     /usr/lib/x86_64-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
7f5d8afba000-7f5d8afbb000 r--p 00001000 08:07 790878                     /usr/lib/x86_64-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
7f5d8afbb000-7f5d8afbc000 rw-p 00002000 08:07 790878                     /usr/lib/x86_64-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
7f5d8afbc000-7f5d8afbd000 ---p 00000000 00:00 0 
7f5d8afbd000-7f5d8b7bd000 rw-p 00000000 00:00 0 
7f5d8b7bd000-7f5d8b7c2000 r-xp 00000000 08:07 396077                     /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
7f5d8b7c2000-7f5d8b9c1000 ---p 00005000 08:07 396077                     /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
7f5d8b9c1000-7f5d8b9c2000 r--p 00004000 08:07 396077                     /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
7f5d8b9c2000-7f5d8b9c3000 rw-p 00005000 08:07 396077                     /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
7f5d8b9c3000-7f5d8b9c9000 r-xp 00000000 08:07 400235                     /usr/lib/x86_64-linux-gnu/libogg.so.0.7.1
7f5d8b9c9000-7f5d8bbc8000 ---p 00006000 08:07 400235                     /usr/lib/x86_64-linux-gnu/libogg.so.0.7.1
7f5d8bbc8000-7f5d8bbc9000 r--p 00005000 08:07 400235                     /usr/lib/x86_64-linux-gnu/libogg.so.0.7.1
7f5d8bbc9000-7f5d8bbca000 rw-p 00006000 08:07 400235                     /usr/lib/x86_64-linux-gnu/libogg.so.0.7.1
7f5d8bbca000-7f5d8bbf5000 r-xp 00000000 08:07 400393                     /usr/lib/x86_64-linux-gnu/libvorbis.so.0.4.5
7f5d8bbf5000-7f5d8bdf4000 ---p 0002b000 08:07 400393                     /usr/lib/x86_64-linux-gnu/libvorbis.so.0.4.5
7f5d8bdf4000-7f5d8bdf5000 r--p 0002a000 08:07 400393                     /usr/lib/x86_64-linux-gnu/libvorbis.so.0.4.5
7f5d8bdf5000-7f5d8bdf6000 rw-p 0002b000 08:07 400393                     /usr/lib/x86_64-linux-gnu/libvorbis.so.0.4.5
7f5d8bdf6000-7f5d8bdfe000 r-xp 00000000 08:07 400192                     /usr/lib/x86_64-linux-gnu/libltdl.so.7.3.0
7f5d8bdfe000-7f5d8bffe000 ---p 00008000 08:07 400192                     /usr/lib/x86_64-linux-gnu/libltdl.so.7.3.0
7f5d8bffe000-7f5d8bfff000 r--p 00008000 08:07 400192                     /usr/lib/x86_64-linux-gnu/libltdl.so.7.3.0
7f5d8bfff000-7f5d8c000000 rw-p 00009000 08:07 400192                     /usr/lib/x86_64-linux-gnu/libltdl.so.7.3.0
7f5d8c000000-7f5d8c022000 rw-p 00000000 00:00 0 
7f5d8c022000-7f5d90000000 ---p 00000000 00:00 0 
7f5d90000000-7f5d90058000 r--p 00000000 08:07 1176009                    /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-BI.ttf
7f5d90058000-7f5d900aa000 r--p 00000000 08:07 1176008                    /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-B.ttf
7f5d900aa000-7f5d90123000 rw-p 00000000 00:00 0 
7f5d90123000-7f5d90133000 r-xp 00000000 08:07 400360                     /usr/lib/x86_64-linux-gnu/libtdb.so.1.2.9
7f5d90133000-7f5d90332000 ---p 00010000 08:07 400360                     /usr/lib/x86_64-linux-gnu/libtdb.so.1.2.9
7f5d90332000-7f5d90333000 r--p 0000f000 08:07 400360                     /usr/lib/x86_64-linux-gnu/libtdb.so.1.2.9
7f5d90333000-7f5d90334000 rw-p 00010000 08:07 400360                     /usr/lib/x86_64-linux-gnu/libtdb.so.1.2.9
7f5d90334000-7f5d9033b000 r-xp 00000000 08:07 400397                     /usr/lib/x86_64-linux-gnu/libvorbisfile.so.3.3.4
7f5d9033b000-7f5d9053a000 ---p 00007000 08:07 400397                     /usr/lib/x86_64-linux-gnu/libvorbisfile.so.3.3.4
7f5d9053a000-7f5d9053b000 r--p 00006000 08:07 400397                     /usr/lib/x86_64-linux-gnu/libvorbisfile.so.3.3.4
7f5d9053b000-7f5d9053c000 rw-p 00007000 08:07 400397                     /usr/lib/x86_64-linux-gnu/libvorbisfile.so.3.3.4
7f5d9053c000-7f5d9054b000 r-xp 00000000 08:07 399930                     /usr/lib/x86_64-linux-gnu/libcanberra.so.0.2.5
7f5d9054b000-7f5d9074a000 ---p 0000f000 08:07 399930                     /usr/lib/x86_64-linux-gnu/libcanberra.so.0.2.5
7f5d9074a000-7f5d9074b000 r--p 0000e000 08:07 399930                     /usr/lib/x86_64-linux-gnu/libcanberra.so.0.2.5
7f5d9074b000-7f5d9074c000 rw-p 0000f000 08:07 399930                     /usr/lib/x86_64-linux-gnu/libcanberra.so.0.2.5
7f5d9074c000-7f5d90750000 r-xp 00000000 08:07 399926                     /usr/lib/x86_64-linux-gnu/libcanberra-gtk.so.0.1.8
7f5d90750000-7f5d9094f000 ---p 00004000 08:07 399926                     /usr/lib/x86_64-linux-gnu/libcanberra-gtk.so.0.1.8
7f5d9094f000-7f5d90950000 r--p 00003000 08:07 399926                     /usr/lib/x86_64-linux-gnu/libcanberra-gtk.so.0.1.8
7f5d90950000-7f5d90951000 rw-p 00004000 08:07 399926                     /usr/lib/x86_64-linux-gnu/libcanberra-gtk.so.0.1.8
7f5d90951000-7f5d90956000 r-xp 00000000 08:07 784378                     /usr/lib/x86_64-linux-gnu/gtk-2.0/modules/libcanberra-gtk-module.so
7f5d90956000-7f5d90b55000 ---p 00005000 08:07 784378                     /usr/lib/x86_64-linux-gnu/gtk-2.0/modules/libcanberra-gtk-module.soAborted (core dumped)
```

---

### Post by SeijiSensei on 2012-06-16
Do you have libdvdcss installed?  Can you play commercial DVDs on this machine?

What version of Handbrake are you using?  If you're using John Stebbins's PPAs, choose either the stable 11.10 build from [handbrake-releases]("https://launchpad.net/~stebbins/+archive/handbrake-releases") or the 12.04 developmental version from [handbrake-snapshots]("https://launchpad.net/~stebbins/+archive/handbrake-snapshots").

---

### Post by irishetalon007 on 2012-06-16
I'm using the "Snapshots" ppa.

Also, it seems that when I try to encode from the DVD directly, handbrake works fine. I also tried ripping with k3b, and the iso made from k3b works fine. 

soooo,

my problem seems to be with the way k9copy makes images! These images burn and play in dvd players just fine, but somehow they crash handbrake.....

Anyways, I guess I'll mark this as solved. 

Thanks for your input!

---

### Post by SeijiSensei on 2012-06-16
You might want to raise this issue with the [Handbrake developers]("https://forum.handbrake.fr/viewforum.php?f=12").

---

### Post by VMC on 2012-06-16
I only use handbrake on gnome. I noticed your core dump file on libcanberra. You have libcanberra.so.0.2.5, I have libcanberra.so.0.2.8. Which is an indication of the os. I use ubuntu precise.

Then again I use the current [snapshot]("https://launchpad.net/~stebbins/+archive/handbrake-snapshots/+packages"), which is 4739.

I never use handbrake on an iso before. I just did and it worked fine. Have you tried another iso?

---

### Post by irishetalon007 on 2012-06-24
I found that the problem has something to do with the way that k9copy generates ISO's or rips DVD folders to the computer.

Using k3b solved all my problems somehow.

Thanks for all the responses!

---

