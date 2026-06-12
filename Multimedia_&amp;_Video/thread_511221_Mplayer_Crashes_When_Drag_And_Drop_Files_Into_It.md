---
title: "Mplayer Crashes When Drag And Drop Files Into It"
date: 2007-07-27
forum: Multimedia &amp; Video
---

### Post by goginot on 2007-07-27
I run MPlayer on Edgy.

When I drag and drop any file to it, it crashes with following output:

Wierd selection owner... QT?
*** glibc detected *** mplayer: munmap_chunk(): invalid pointer: 0x08c27894 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x18a)[0xb700cb4a]
mplayer(gconvert_uri_to_filename+0x1a5)[0x810e094]
======= Memory map: ========
08048000-08850000 r-xp 00000000 08:04 856667     /usr/local/bin/mplayer
08850000-088bb000 rw-p 00808000 08:04 856667     /usr/local/bin/mplayer
088bb000-08c34000 rw-p 088bb000 00:00 0          [heap]
b57a3000-b581b000 r--p 00000000 08:04 933922     /usr/share/fonts/truetype/freefont/FreeSans.ttf
b581b000-b58dc000 rw-p b581b000 00:00 0
b5952000-b5985000 rw-s 00000000 00:08 26345479   /SYSV00000000 (deleted)
b5985000-b59a1000 rw-s 00000000 00:08 26312710   /SYSV00000000 (deleted)
b59a1000-b59c2000 rw-s 00000000 00:08 26279941   /SYSV00000000 (deleted)
b59c2000-b59e4000 rw-p b59c2000 00:00 0
b59e4000-b5a33000 rw-s 00000000 00:08 26247170   /SYSV00000000 (deleted)
b5a33000-b5a82000 rw-p b5a33000 00:00 0
b5a90000-b5b3d000 rw-p b5a90000 00:00 0
b5b3d000-b5b9d000 rw-s 00000000 00:08 26181633   /SYSV00000000 (deleted)
b5b9d000-b5bc7000 r-xp 00000000 08:04 723114     /usr/lib/libkdefx.so.4.2.0
b5bc7000-b5bc8000 rw-p 00029000 08:04 723114     /usr/lib/libkdefx.so.4.2.0
b5bdb000-b5bf9000 r-xp 00000000 08:04 770329     /usr/lib/kde3/plugins/styles/plastik.so
b5bf9000-b5bfa000 rw-p 0001e000 08:04 770329     /usr/lib/kde3/plugins/styles/plastik.so
b5bfa000-b5cd1000 r--p 00000000 08:04 771198     /usr/lib/locale/en_US.utf8/LC_COLLATE
b5cd1000-b5ce2000 r-xp 00000000 08:04 722388     /usr/lib/libXft.so.2.1.2
b5ce2000-b5ce3000 rw-p 00010000 08:04 722388     /usr/lib/libXft.so.2.1.2
b5ce3000-b6478000 r-xp 00000000 08:04 721027     /usr/lib/libqt-mt.so.3.3.6
b6478000-b64be000 rw-p 00795000 08:04 721027     /usr/lib/libqt-mt.so.3.3.6
b64be000-b64c2000 rw-p b64be000 00:00 0
b64c2000-b64e0000 r-xp 00000000 08:04 770414     /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so
b64e0000-b64e1000 rw-p 0001e000 08:04 770414     /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so
b64e1000-b64ea000 r-xp 00000000 08:04 1704403    /lib/tls/i686/cmov/libnss_files-2.4.so
b64ea000-b64ec000 rw-p 00008000 08:04 1704403    /lib/tls/i686/cmov/libnss_files-2.4.so
b64ec000-b64f4000 r-xp 00000000 08:04 1704405    /lib/tls/i686/cmov/libnss_nis-2.4.so
b64f4000-b64f6000 rw-p 00007000 08:04 1704405    /lib/tls/i686/cmov/libnss_nis-2.4.so
b64f6000-b6508000 r-xp 00000000 08:04 1704400    /lib/tls/i686/cmov/libnsl-2.4.so
b6508000-b650a000 rw-p 00011000 08:04 1704400    /lib/tls/i686/cmov/libnsl-2.4.so
b650a000-b650c000 rw-p b650a000 00:00 0
b6510000-b6511000 rw-p b6510000 00:00 0
b6511000-b6517000 r-xp 00000000 08:04 770709     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b6517000-b6518000 rw-p 00005000 08:04 770709     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b6518000-b6519000 r-xp 00000000 08:04 770446     /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
b6519000-b651a000 rw-p 00000000 08:04 770446     /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
b651a000-b651b000 r--p 00000000 08:04 771204     /usr/lib/locale/en_US.utf8/LC_NUMERIC
b651b000-b651c000 r--p 00000000 08:04 771207     /usr/lib/locale/en_US.utf8/LC_TIME
b651c000-b651d000 r--p 00000000 08:04 771202     /usr/lib/locale/en_US.utf8/LC_MONETARY
b651d000-b651e000 r--p 00000000 08:04 786440     /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b651e000-b651f000 r--p 00000000 08:04 771205     /usr/lib/locale/en_US.utf8/LC_PAPER
b651f000-b6524000 r-xp 00000000 08:04 770447     /usr/lib/X11/locale/common/xlibi18n.so.2.0.0
b6524000-b6525000 rw-p 00004000 08:04 770447     /usr/lib/X11/locale/common/xlibi18n.so.2.0.0
b6525000-b6526000 rw-p b6525000 00:00 0
b6526000-b652d000 r--s 00000000 08:04 737636     /usr/lib/gconv/gconv-modules.cache
b652d000-b6560000 r--p 00000000 08:04 771199     /usr/lib/locale/en_US.utf8/LC_CTYPE
b6560000-b65c5000 rw-p b6560000 00:00 0
b65c5000-b65cf000 r-xp 00000000 08:04 1671235    /lib/libgcc_s.so.1
b65cf000-b65d0000 rw-p 00009000 08:04 1671235    /lib/libgcc_s.so.1
b65d0000-b65ec000 r-xp 00000000 08:04 722570     /usr/lib/libexpat.so.1.0.0
b65ec000-b65ee000 rw-p 0001c000 08:04 722570     /usr/lib/libexpat.so.1.0.0
b65ee000-b65ef000 rw-p b65ee000 00:00 0
b65ef000-b6619000 r-xp 00000000 08:04 723188     /usr/lib/libpangoft2-1.0.so.0.1400.5
b6619000-b661a000 rw-p 00029000 08:04 723188     /usr/lib/libpangoft2-1.0.so.0.1400.5
b661a000-b66b2000 r-xp 00000000 08:04 723523     /usr/lib/libmp4v2.so.0.0.0
b66b2000-b66b6000 rw-p 00098000 08:04 723523     /usr/lib/libmp4v2.so.0.0.0
b66b6000-b66b7000 rw-p b66b6000 00:00 0
b66b7000-b678b000 r-xp 00000000 08:04 723294     /usr/lib/libstdc++.so.6.0.8
b678b000-b678e000 r--p 000d4000 08:04 723294     /usr/lib/libstdc++.so.6.0.8
b678e000-b6790000 rw-p 000d7000 08:04 723294     /usr/lib/libstdc++.so.6.0.8
b6790000-b6796000 rw-p b6790000 00:00 0
b6796000-b679d000 r-xp 00000000 08:04 1704410    /lib/tls/i686/cmov/librt-2.4.so
b679d000-b679f000 rw-p 00006000 08:04 1704410    /lib/tls/i686/cmov/librt-2.4.so
b679f000-b67b4000 r-xp 00000000 08:04 722296     /usr/lib/libICE.so.6.3.0
b67b4000-b67b5000 rw-p 00014000 08:04 722296     /usr/lib/libICE.so.6.3.0
b67b5000-b67b8000 rw-p b67b5000 00:00 0
b67b8000-b67c0000 r-xp 00000000 08:04 722361     /usr/lib/libSM.so.6.0.0
b6

MPlayer interrupted by signal 6 in module: unknown
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.



Any solutions?

---

### Post by drewcoll on 2007-07-30
I have the same problem, didn't notice it was drag and drop that was causing it until you mentioned this.  Thanks.

I'm hoping there's a solution!

---

### Post by sdowney717 on 2007-07-30
have you tried smplayer?
it uses mplayer engine with a nice gui front end

---

### Post by goginot on 2007-08-02
Well, smplayer looks very promising...
I will try it soon.
thanks, sdowney717

---

