---
title: "VLC crashing on startup"
date: 2008-07-13
forum: Multimedia Software
---

### Post by croese on 2008-07-13
There are a couple of forum categories where this could conceivably go, but this seems the most logical place.

I'm running Hardy 64-bit and whenever I start up VLC (the latest one -- 0.8.6), it crashes and dumps this to the console window:

```
$ vlc %U
VLC media player 0.8.6e Janus
*** glibc detected *** vlc: free(): invalid pointer: 0x00000000009e1770 ***
======= Backtrace: =========
/lib/libc.so.6[0x7feac308e08a]
/lib/libc.so.6(cfree+0x8c)[0x7feac3091c1c]
/usr/lib/libwx_gtk2u_core-2.6.so.0[0x7feabf38ae5e]
/usr/lib/vlc/gui/libwxwidgets_plugin.so(_ZN5wxvlc8MessagesC1EP13intf_thread_tP8wxWindow+0x52a)[0x7feac089c0ba]
/usr/lib/vlc/gui/libwxwidgets_plugin.so(_ZN15DialogsProviderC1EP13intf_thread_tP8wxWindow+0x1ea)[0x7feac085cfba]
/usr/lib/vlc/gui/libwxwidgets_plugin.so(_Z21CreateDialogsProviderP13intf_thread_tP8wxWindow+0x34)[0x7feac085d564]
/usr/lib/vlc/gui/libwxwidgets_plugin.so(_ZN8Instance6OnInitEv+0x7d)[0x7feac08301dd]
/usr/lib/vlc/gui/libwxwidgets_plugin.so(_ZN12wxAppConsole10CallOnInitEv+0xd)[0x7feac0831ecd]
/usr/lib/libwx_baseu-2.6.so.0(_Z7wxEntryRiPPw+0x22)[0x7feabeab3ab2]
/usr/lib/vlc/gui/libwxwidgets_plugin.so[0x7feac08318bc]
/usr/lib/libvlc.so.0[0x7feac409efb8]
/usr/lib/libvlc.so.0(intf_RunThread+0x5a)[0x7feac409f16a]
/usr/lib/libvlc.so.0[0x7feac409c922]
vlc[0x400b90]
/lib/libc.so.6(__libc_start_main+0xf4)[0x7feac30381c4]
vlc[0x400a39]
======= Memory map: ========
00400000-00401000 r-xp 00000000 08:01 11243740                           /usr/bin/vlc
00601000-00602000 rw-p 00001000 08:01 11243740                           /usr/bin/vlc
00602000-00a82000 rw-p 00602000 00:00 0                                  [heap]
41a45000-41a46000 ---p 41a45000 00:00 0 
41a46000-42246000 rw-p 41a46000 00:00 0 
42246000-42247000 ---p 42246000 00:00 0 
42247000-42a47000 rw-p 42247000 00:00 0 
42a47000-42a48000 ---p 42a47000 00:00 0 
42a48000-43248000 rw-p 42a48000 00:00 0 
43248000-43249000 ---p 43248000 00:00 0 
43249000-43a49000 rw-p 43249000 00:00 0 
43a49000-43a4a000 ---p 43a49000 00:00 0 
43a4a000-4424a000 rw-p 43a4a000 00:00 0 
7feab266a000-7feab2679000 r-xp 00000000 08:01 9846860                    /lib/libbz2.so.1.0.4
7feab2679000-7feab2878000 ---p 0000f000 08:01 9846860                    /lib/libbz2.so.1.0.4
7feab2878000-7feab287a000 rw-p 0000e000 08:01 9846860                    /lib/libbz2.so.1.0.4
7feab287a000-7feab28e8000 r-xp 00000000 08:01 11239537                   /usr/lib/libgio-2.0.so.0.0.0
7feab28e8000-7feab2ae8000 ---p 0006e000 08:01 11239537                   /usr/lib/libgio-2.0.so.0.0.0
7feab2ae8000-7feab2aeb000 rw-p 0006e000 08:01 11239537                   /usr/lib/libgio-2.0.so.0.0.0
7feab2aeb000-7feab2b23000 r-xp 00000000 08:01 11248946                   /usr/lib/libcroco-0.6.so.3.0.1
7feab2b23000-7feab2d22000 ---p 00038000 08:01 11248946                   /usr/lib/libcroco-0.6.so.3.0.1
7feab2d22000-7feab2d26000 rw-p 00037000 08:01 11248946                   /usr/lib/libcroco-0.6.so.3.0.1
7feab2d26000-7feab2d5d000 r-xp 00000000 08:01 11244612                   /usr/lib/libgsf-1.so.114.0.7
7feab2d5d000-7feab2f5c000 ---p 00037000 08:01 11244612                   /usr/lib/libgsf-1.so.114.0.7
7feab2f5c000-7feab2f60000 rw-p 00036000 08:01 11244612                   /usr/lib/libgsf-1.so.114.0.7
7feab2f60000-7feab2f61000 rw-p 7feab2f60000 00:00 0 
7feab2f61000-7feab2f95000 r-xp 00000000 08:01 11244614                   /usr/lib/librsvg-2.so.2.22.2
7feab2f95000-7feab3195000 ---p 00034000 08:01 11244614                   /usr/lib/librsvg-2.so.2.22.2
7feab3195000-7feab3197000 rw-p 00034000 08:01 11244614                   /usr/lib/librsvg-2.so.2.22.2
7feab3197000-7feab3199000 r-xp 00000000 08:01 11321716                   /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
7feab3199000-7feab3398000 ---p 00002000 08:01 11321716                   /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
7feab3398000-7feab3399000 rw-p 00001000 08:01 11321716                   /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
7feab3399000-7feab372a000 r--p 00000000 08:01 38289410                   /usr/share/icons/hicolor/icon-theme.cache
7feab372a000-7feab3e9a000 r--p 00000000 08:01 11354696                   /usr/share/icons/gnome/icon-theme.cache
7feab3e9a000-7feab4000000 r--p 00000000 08:01 11601720                   /usr/share/icons/Human/icon-theme.cache
7feab4000000-7feab4021000 rw-p 7feab4000000 00:00 0 
7feab4021000-7feab8000000 ---p 7feab4021000 00:00 0 
7feab802c000-7feab80d7000 r--p 00000000 08:01 11699774                   /usr/share/icons/Tangerine/icon-theme.cache
7feab80d7000-7feab80d9000 r-xp 00000000 08:01 11322538                   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7feab80d9000-7feab82d8000 ---p 00002000 08:01 11322538                   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7feab82d8000-7feab82d9000 rw-p 00001000 08:01 11322538                   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7feab82d9000-7feab8339000 rw-s 00000000 00:09 5832726                    /SYSV00000000 (deleted)
7feab8339000-7feab8399000 rw-s 00000000 00:09 5799957                    /SYSV00000000 (deleted)
7feab8399000-7feab839f000 r-xp 00000000 08:01 11322409                   /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
7feab839f000-7feab859f000 ---p 00006000 08:01 11322409                   /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
7feab859f000-7feab85a0000 rw-p 00006000 08:01 11322409                   /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
7feab85a0000-7feab85b2000 r-xp 00000000 08:01 29982721                   /usr/lib/gtk-2.0/2.10.0/immodules/im-scim-bridge.so
7feab85b2000-7feab87b2000 ---p 00012000 08:01 29982721                   /usr/lib/gtk-2.0/2.10.0/immodules/im-scim-bridge.so
7feab87b2000-7feab87b3000 rw-p 00012000 08:01 29982721                   /usr/lib/gtk-2.0/2.10.0/immodules/im-scim-bridge.so
7feab87b3000-7feab87ba000 r-xp 00000000 08:01 11246454                   /usr/lib/libgailutil.so.18.0.1
7feab87ba000-7feab89ba000 ---p 00007000 08:01 11246454                   /usr/lib/libgailutil.so.18.0.1
7feab89ba000-7feab89bb000 rw-p 00007000 08:01 11246454                   /usr/lib/libgailutil.so.18.0.1
7feab89bb000-7feab89f0000 r-xp 00000000 08:01 11241663                   /usr/lib/libgnomecanvas-2.so.0.2001.0
7feab89f0000-7feab8bef000 ---p 00035000 08:01 11241663                   /usr/lib/libgnomecanvas-2.so.0.2001.0
7feab8bef000-7feab8bf1000 rw-p 00034000 08:01 11241663                   /usr/lib/libgnomecanvas-2.so.0.2001.0
7feab8bf1000-7feab8c35000 r-xp 00000000 08:01 11243807                   /usr/lib/libgnomeprintui-2-2.so.0.1.0
7feab8c35000-7feab8e35000 ---p 00044000 08:01 11243807                   /usr/lib/libgnomeprintui-2-2.so.0.1.0
7feab8e35000-7feab8e38000 rw-p 00044000 08:01 11243807                   /usr/lib/libgnomeprintui-2-2.so.0.1.0
7feab8e38000-7feab8f75000 r-xp 00000000 08:01 11248935                   /usr/lib/libxml2.so.2.6.31
7feab8f75000-7feab9175000 ---p 0013d000 08:01 11248935                   /usr/lib/libxml2.so.2.6.31
7feab9175000-7feab917e000 rw-p 0013d000 08:01 11248935                   /usr/lib/libxml2.so.2.6.31
7feab917e000-7feab917f000 rw-p 7feab917e000 00:00 0 
7feab917f000-7feab9197000 r-xp 00000000 08:01 11244112                   /usr/lib/libart_lgpl_2.so.2.3.20
7feab9197000-7feab9396000 ---p 00018000 08:01 11244112                   /usr/lib/libart_lgpl_2.so.2.3.20
7feab9396000-7feab9397000 rw-p 00017000 08:01 11244112                   /usr/lib/libart_lgpl_2.so.2.3.20
7feab9397000-7feab9406000 r-xp 00000000 08:01 11244308                   /usr/lib/libgnomeprint-2-2.so.0.1.0
7feab9406000-7feab9605000 ---p 0006f000 08:01 11244308                   /usr/lib/libgnomeprint-2-2.so.0.1.0
7feab9605000-7feab9608000 rw-p 0006e000 08:01 11244308                   /usr/lib/libgnomeprint-2-2.so.0.1.0
7feab9610000-7feab9621000 r--p 00000000 08:01 11699799                   /usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf
7feab9621000-7feab9633000 r-xp 00000000 08:01 11355272                   /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
7feab9633000-7feab9833000 ---p 00012000 08:01 11355272                   /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
7feab9833000-7feab9834000 rw-p 00012000 08:01 11355272                   /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
7feab9834000-7feab9839000 r-xp 00000000 08:01 11243351                   /usr/lib/libXdmcp.so.6.0.0
7feab9839000-7feab9a38000 ---p 00005000 08:01 11243351                   /usr/lib/libXdmcp.so.6.0.Aborted

```

Anyone have ideas on this?  I've tried searching around, but haven't found any specific fixes.

Thanks in advance.

---

