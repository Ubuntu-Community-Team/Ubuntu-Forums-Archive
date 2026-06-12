---
title: "Grip crashing during encoding"
date: 2009-08-15
forum: Multimedia Software
---

### Post by human39 on 2009-08-15
Hello!

grip crashes on me while I'm encoding files.  

Below is the error that I get.  If you need more information, please let me know.

Thanks!

```
*** buffer overflow detected ***: grip terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb6dd9da8]
/lib/tls/i686/cmov/libc.so.6[0xb6dd7eb0]
/lib/tls/i686/cmov/libc.so.6[0xb6dd75a8]
/lib/tls/i686/cmov/libc.so.6(_IO_default_xsputn+0xc8)[0xb6d49bb8]
/lib/tls/i686/cmov/libc.so.6(_IO_vfprintf+0x6f3)[0xb6d1bf23]
/lib/tls/i686/cmov/libc.so.6(__vsprintf_chk+0xa4)[0xb6dd7654]
/lib/tls/i686/cmov/libc.so.6(__sprintf_chk+0x2d)[0xb6dd759d]
grip[0x8063afd]
grip[0x80605bb]
grip[0x80507a8]
grip[0x804ecc3]
/usr/lib/libglib-2.0.so.0[0xb71522b6]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e8)[0xb7151b88]
/usr/lib/libglib-2.0.so.0[0xb71550eb]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1ca)[0xb71555ba]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9)[0xb77a17d9]
grip[0x804ec98]
grip[0x804ea42]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb6cf2775]
grip[0x804e981]
======= Memory map: ========
08048000-08076000 r-xp 00000000 08:01 12632087   /usr/bin/grip
08076000-08077000 r--p 0002e000 08:01 12632087   /usr/bin/grip
08077000-0807b000 rw-p 0002f000 08:01 12632087   /usr/bin/grip
0807b000-080a8000 rw-p 0807b000 00:00 0 
09c60000-0a0ed000 rw-p 09c60000 00:00 0          [heap]
b622d000-b623c000 r-xp 00000000 08:01 8003626    /lib/libbz2.so.1.0.4
b623c000-b623d000 r--p 0000f000 08:01 8003626    /lib/libbz2.so.1.0.4
b623d000-b623e000 rw-p 00010000 08:01 8003626    /lib/libbz2.so.1.0.4
b623e000-b626f000 r-xp 00000000 08:01 3754748    /usr/lib/libcroco-0.6.so.3.0.1
b626f000-b6272000 rw-p 00030000 08:01 3754748    /usr/lib/libcroco-0.6.so.3.0.1
b6272000-b62a5000 r-xp 00000000 08:01 3755025    /usr/lib/libgsf-1.so.114.0.11
b62a5000-b62a6000 ---p 00033000 08:01 3755025    /usr/lib/libgsf-1.so.114.0.11
b62a6000-b62a8000 r--p 00033000 08:01 3755025    /usr/lib/libgsf-1.so.114.0.11
b62a8000-b62a9000 rw-p 00035000 08:01 3755025    /usr/lib/libgsf-1.so.114.0.11
b62a9000-b62aa000 rw-p b62a9000 00:00 0 
b62aa000-b62db000 r-xp 00000000 08:01 3755403    /usr/lib/librsvg-2.so.2.26.0
b62db000-b62dc000 r--p 00031000 08:01 3755403    /usr/lib/librsvg-2.so.2.26.0
b62dc000-b62dd000 rw-p 00032000 08:01 3755403    /usr/lib/librsvg-2.so.2.26.0
b62eb000-b6303000 r--s 00000000 08:01 3843007    /usr/share/mime/mime.cache
b6303000-b6312000 r-xp 00000000 08:01 3777155    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b6312000-b6313000 r--p 0000e000 08:01 3777155    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b6313000-b6314000 rw-p 0000f000 08:01 3777155    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b6314000-b6326000 r-xp 00000000 08:01 3753279    /usr/lib/libgvfscommon.so.0.0.0
b6326000-b6327000 r--p 00012000 08:01 3753279    /usr/lib/libgvfscommon.so.0.0.0
b6327000-b6328000 rw-p 00013000 08:01 3753279    /usr/lib/libgvfscommon.so.0.0.0
b6333000-b6334000 r-xp 00000000 08:01 3777865    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b6334000-b6335000 r--p 00000000 08:01 3777865    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b6335000-b6336000 rw-p 00001000 08:01 3777865    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b6336000-b6350000 r-xp 00000000 08:01 3777156    /usr/lib/gio/modules/libgvfsdbus.so
b6350000-b6351000 r--p 00019000 08:01 3777156    /usr/lib/gio/modules/libgvfsdbus.so
b6351000-b6352000 rw-p 0001a000 08:01 3777156    /usr/lib/gio/modules/libgvfsdbus.so
b6352000-b639c000 r--p 00000000 08:01 3893377    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono-Bold.ttf
b639c000-b63eb000 r--p 00000000 08:01 3893378    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
b63eb000-b63ec000 r--p 00000000 08:01 4073166    /usr/share/vte/termcap/xterm
b63ec000-b6484000 r--p 00000000 08:01 3893376    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b6484000-b6486000 r-xp 00000000 08:01 3819428    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6486000-b6487000 r--p 00001000 08:01 3819428    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6487000-b6488000 rw-p 00002000 08:01 3819428    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6Aborted

```

---

### Post by human39 on 2009-08-17
I'm still at a lost with this, I'm unsure on what's going on here.  Can I get any more information for people?

---

### Post by Calyce on 2009-09-05
Hi Human39,

I used to have the exact same problem. I "solved" it by deselecting "Add ID3v2 tags to encoded files" in the config/ID3 tab.

Hope it helps ;-)

---

