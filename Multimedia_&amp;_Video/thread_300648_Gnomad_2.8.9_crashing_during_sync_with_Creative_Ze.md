---
title: "Gnomad 2.8.9 crashing during sync with Creative Zen Vision:M (Edgy)"
date: 2006-11-16
forum: Multimedia &amp; Video
---

### Post by Xer0 Ph0kus on 2006-11-16
I finally got Gnomad2 working after a problem with a directory, but now when I try to place the songs on my ZV:M the thing crashes and I don't know why. It will sync a few files then crash. Then I restart it and it'll do a bit more than crash. Here is the log.

```
*** glibc detected *** gnomad2: malloc(): memory corruption: 0x085c0078 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb775f1cd]
/lib/tls/i686/cmov/libc.so.6(malloc+0x7f)[0xb776083f]
/usr/lib/libid3tag.so.0(id3_util_compress+0x36)[0xb7873ce0]
======= Memory map: ========
08048000-0806e000 r-xp 00000000 08:02 2474240    /usr/local/bin/gnomad2
0806e000-0806f000 rw-p 00026000 08:02 2474240    /usr/local/bin/gnomad2
0806f000-08606000 rw-p 0806f000 00:00 0          [heap]
b56ff000-b5700000 ---p b56ff000 00:00 0 
b5700000-b5fd0000 rw-p b5700000 00:00 0 
b5fd0000-b6000000 ---p b5fd0000 00:00 0 
b607e000-b6088000 r-xp 00000000 08:02 22544434   /lib/libgcc_s.so.1
b6088000-b6089000 rw-p 00009000 08:02 22544434   /lib/libgcc_s.so.1
b6098000-b6099000 rw-p b6098000 00:00 0 
b6099000-b60b8000 r--p 00000000 08:02 2637911    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-ExtraLight.ttf
b60b8000-b6124000 r--p 00000000 08:02 2637909    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b6124000-b6125000 ---p b6124000 00:00 0 
b6125000-b6925000 rw-p b6125000 00:00 0 
b6925000-b6985000 rw-s 00000000 00:07 6062096    /SYSV00000000 (deleted)
b6985000-b69f6000 r--p 00000000 08:02 2637913    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b69f6000-b69f8000 r-xp 00000000 08:02 21086212   /usr/lib/pango/1.5.0/modules/pango-basic-fc.so
b69f8000-b69f9000 rw-p 00001000 08:02 21086212   /usr/lib/pango/1.5.0/modules/pango-basic-fc.so
b69f9000-b6b98000 r--p 00000000 08:02 2737105    /usr/share/icons/hicolor/icon-theme.cache
b6b98000-b6b9f000 r--p 00000000 08:02 2932801    /usr/share/icons/crystalsvg/icon-theme.cache
b6b9f000-b71fb000 r--p 00000000 08:02 2737123    /usr/share/icons/gnome/icon-theme.cache
b71fb000-b7453000 r--p 00000000 08:02 2737122    /usr/share/icons/Tango/icon-theme.cache
b7453000-b74a4000 r--p 00000000 08:02 2737103    /usr/share/icons/Tangerine/icon-theme.cache
b74a4000-b74ab000 r--p 00000000 08:02 2721783    /usr/share/icons/Human/icon-theme.cache
b74ab000-b74bc000 r-xp 00000000 08:02 2523866    /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b74bc000-b74bd000 rw-p 00011000 08:02 2523866    /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b74bd000-b74c6000 r-xp 00000000 08:02 22544472   /lib/tls/i686/cmov/libnss_files-2.4.so
b74c6000-b74c8000 rw-p 00008000 08:02 22544472   /lib/tls/i686/cmov/libnss_files-2.4.so
b74c8000-b74d0000 r-xp 00000000 08:02 22544476   /lib/tls/i686/cmov/libnss_nis-2.4.so
b74d0000-b74d2000 rw-p 00007000 08:02 22544476   /lib/tls/i686/cmov/libnss_nis-2.4.so
b74d2000-b74e4000 r-xp 00000000 08:02 22544466   /lib/tls/i686/cmov/libnsl-2.4.so
b74e4000-b74e6000 rw-p 00011000 08:02 22544466   /lib/tls/i686/cmov/libnsl-2.4.so
b74e6000-b74e8000 rw-p b74e6000 00:00 0 
b74e8000-b74ef000 r-xp 00000000 08:02 22544468   /lib/tls/i686/cmov/libnss_compat-2.4.so
b74ef000-b74f1000 rw-p 00006000 08:02 22544468   /lib/tls/i686/cmov/libnss_compat-2.4.so
b74f7000-b74fb000 r-xp 00000000 08:02 2523286    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b74fb000-b74fc000 rw-p 00003000 08:02 2523286    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b74fc000-b74fd000 rw-p b74fc000 00:00 0 
b74fd000-b74fe000 r-xp 00000000 08:02 2415144    /usr/lib/gconv/ISO8859-1.so
b74fe000-b7500000 rw-p 00001000 08:02 2415144    /usr/lib/gconv/ISO8859-1.so
b7500000-b7501000 r-xp 00000000 08:02 2786264    /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
b7501000-b7502000 rw-p 00000000 08:02 2786264    /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
b7502000-b7535000 r--p 00000000 08:02 2474052    /usr/lib/locale/en_US.utf8/LC_CTYPE
b7535000-b7536000 r--p 00000000 08:02 2474053    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b7536000-b7537000 r--p 00000000 08:02 2802107    /usr/lib/locale/en_US.utf8/LC_TIME
b7537000-b760e000 r--p 00000000 08:02 2474055    /usr/lib/locale/en_US.utf8/LC_COLLATE
b760e000-b7610000 rw-p b760e000 00:00 0 
b7610000-b7614000 r-xp 00000000 08:02 2411347    /usr/lib/libXdmcp.so.6.0.0
b7614000-b7615000 rw-p 00003000 08:02 2411347    /usr/liAborted (core dumped)
alex@alex-desktop:~$ 
```

Thanks for any help

---

### Post by ivago on 2006-11-16
can just tell you that on my box gnomad 2.8.9 and my ZVM work without a problem on Edgy. The version of libmtp is 0.0.21 and libnjb is 2.2.5 maybe you need a to upgrade your libmtp?

---

### Post by ivago on 2006-11-16
can just tell you that on my box gnomad 2.8.9 and my ZVM work without a problem on Edgy. The version of libmtp is 0.0.21 and libnjb is 2.2.5 maybe you need a to upgrade your libmtp?

---

### Post by Xer0 Ph0kus on 2006-11-17
> **ivago said:**
> can just tell you that on my box gnomad 2.8.9 and my ZVM work without a problem on Edgy. The version of libmtp is 0.0.21 and libnjb is 2.2.5 maybe you need a to upgrade your libmtp?

Well i tried to update my libmtp to 0.0.21 but whenever I install things it puts it in the directory that the .tar.gz was in. How can I install it and place it in whatever dir it should be in? BTW what dir should I be installing it to?

Thanks

---

