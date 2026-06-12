---
title: "Buffer Overflow detected"
date: 2009-05-01
forum: Multimedia Software
---

### Post by Paresh on 2009-05-01
RhythmBox on 9.04 works fine for mp3s on my laptop, but inserting an audio CD causes it to abort.

Running it from shell gave me the following error report:

```

*** buffer overflow detected ***: rhythmbox terminated
======= Backtrace: =========
/lib/libc.so.6(__fortify_fail+0x37)[0x7f29b4efe2c7]
/lib/libc.so.6[0x7f29b4efc170]
/lib/libc.so.6[0x7f29b4efb519]
/lib/libc.so.6(_IO_default_xsputn+0x96)[0x7f29b4e75426]
/lib/libc.so.6(_IO_vfprintf+0x1c1c)[0x7f29b4e465bc]
/lib/libc.so.6(__vsprintf_chk+0x99)[0x7f29b4efb5b9]
/lib/libc.so.6(__sprintf_chk+0x80)[0x7f29b4efb500]
/usr/lib/libmusicbrainz.so.4(_ZN10RDFExtractC1ERKSsb+0x105)[0x7f29a5b62e55]
/usr/lib/libmusicbrainz.so.4(_ZN11MusicBrainz5QueryERKSsPSt6vectorISsSaISsEE+0x7ce)[0x7f29a5b5761e]
/usr/lib/libmusicbrainz.so.4(mb_Query+0x30)[0x7f29a5b4ba10]
/usr/lib/rhythmbox/plugins/audiocd/libaudiocd.so[0x7f29a619368f]
/usr/lib/rhythmbox/plugins/audiocd/libaudiocd.so[0x7f29a61926d3]
/usr/lib/libglib-2.0.so.0[0x7f29b5613ae4]
/lib/libpthread.so.0[0x7f29bbf343ba]
/lib/libc.so.6(clone+0x6d)[0x7f29b4ee4fcd]
======= Memory map: ========
00400000-004a3000 r-xp 00000000 08:06 1196855                            /usr/bin/rhythmbox
006a3000-006a7000 r--p 000a3000 08:06 1196855                            /usr/bin/rhythmbox
006a7000-006af000 rw-p 000a7000 08:06 1196855                            /usr/bin/rhythmbox
006af000-006b0000 rw-p 006af000 00:00 0 
01cec000-0325e000 rw-p 01cec000 00:00 0                                  [heap]
7f299c000000-7f299c1e8000 rw-p 7f299c000000 00:00 0 
7f299c1e8000-7f29a0000000 ---p 7f299c1e8000 00:00 0 
7f29a15da000-7f29a15df000 r-xp 00000000 08:06 1507550                    /lib/libnss_dns-2.9.so
7f29a15df000-7f29a17de000 ---p 00005000 08:06 1507550                    /lib/libnss_dns-2.9.so
7f29a17de000-7f29a17df000 r--p 00004000 08:06 1507550                    /lib/libnss_dns-2.9.so
7f29a17df000-7f29a17e0000 rw-p 00005000 08:06 1507550                    /lib/libnss_dns-2.9.so
7f29a17e0000-7f29a17e2000 r-xp 00000000 08:06 1507422                    /lib/libnss_mdns4_minimal.so.2
7f29a17e2000-7f29a19e1000 ---p 00002000 08:06 1507422                    /lib/libnss_mdns4_minimal.so.2
7f29a19e1000-7f29a19e2000 rw-p 00001000 08:06 1507422                    /lib/libnss_mdns4_minimal.so.2
7f29a1a05000-7f29a1a06000 ---p 7f29a1a05000 00:00 0 
7f29a1a06000-7f29a1a46000 rw-p 7f29a1a06000 00:00 0 
7f29a1a46000-7f29a1a47000 ---p 7f29a1a46000 00:00 0 
7f29a1a47000-7f29a2247000 rw-p 7f29a1a47000 00:00 0 
7f29a2247000-7f29a2248000 ---p 7f29a2247000 00:00 0 
7f29a2248000-7f29a2a48000 rw-p 7f29a2248000 00:00 0 
7f29a2a48000-7f29a2a73000 r-xp 00000000 08:06 1171459                    /usr/lib/gstreamer-0.10/libgstcoreelements.so
7f29a2a73000-7f29a2c72000 ---p 0002b000 08:06 1171459                    /usr/lib/gstreamer-0.10/libgstcoreelements.so
7f29a2c72000-7f29a2c73000 r--p 0002a000 08:06 1171459                    /usr/lib/gstreamer-0.10/libgstcoreelements.so
7f29a2c73000-7f29a2c75000 rw-p 0002b000 08:06 1171459                    /usr/lib/gstreamer-0.10/libgstcoreelements.so
7f29a2c75000-7f29a2c7d000 r-xp 00000000 08:06 1199674                    /usr/lib/libcdda_paranoia.so.0.10.2
7f29a2c7d000-7f29a2e7c000 ---p 00008000 08:06 1199674                    /usr/lib/libcdda_paranoia.so.0.10.2
7f29a2e7c000-7f29a2e7d000 r--p 00007000 08:06 1199674                    /usr/lib/libcdda_paranoia.so.0.10.2
7f29a2e7d000-7f29a2e7e000 rw-p 00008000 08:06 1199674                    /usr/lib/libcdda_paranoia.so.0.10.2
7f29a2e7e000-7f29a2e8e000 r-xp 00000000 08:06 1197195                    /usr/lib/libcdda_interface.so.0.10.2
7f29a2e8e000-7f29a308d000 ---p 00010000 08:06 1197195                    /usr/lib/libcdda_interface.so.0.10.2
7f29a308d000-7f29a308e000 r--p 0000f000 08:06 1197195                    /usr/lib/libcdda_interface.so.0.10.2
7f29a308e000-7f29a308f000 rw-p 00010000 08:06 1197195                    /usr/lib/libcdda_interface.so.0.10.2
7f29a308f000-7f29a3093000 r-xp 00000000 08:06 1171523                    /usr/lib/gstreamer-0.10/libgstcdparanoia.so
7f29a3093000-7f29a3293000 ---p 00004000 08:06 1171523                    /usr/lib/gstreamer-0.10/libgstcdparanoia.so
7f29a3293000-7f29a3294000 r--p 00004000 08:06 1171523                    /usr/lib/gstreamer-0.10/libgstcdparanoia.so
7f29a3294000-7f29a3295000 rw-p 00005000 08:06 1171523                    /usr/lib/gstreamer-0.10/libgstcdparanoia.so
7f29a3295000-7f29a32f5000 rw-s 00000000 00:09 5505058                    /SYSV00000000 (deleted)
7f29a32f5000-7f29a3355000 rw-s 00000000 00:09 5472289                    /SYSV00000000 (deleted)
7f29a3355000-7f29a33e1000 r--p 00000000 08:06 1499765                    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
7f29a33e1000-7f29a33e2000 ---p 7f29a33e1000 00:00 0 
7f29a33e2000-7f29a3be2000 rw-p 7f29a33e2000 00:00 0 
7f29a3be2000-7f29a3be5000 r-xp 00000000 08:06 1228812                    /usr/lib/libglade/2.0/libbonobo.so
7f29a3be5000-7f29a3de4000 ---p 00003000 08:06 1228812                    /usr/lib/libglade/2.0/libbonobo.so
7f29a3de4000-7f29a3de5000 r--p 00002000 08:06 1228812                    /usr/lib/libglade/2.0/libbonobo.so
7f29a3de5000-7f29a3de6000 rw-p 00003000 08:06 1228812                    /usr/lib/libglade/2.0/libbonobo.so
7f29a3de6000-7f29a3ded000 r-xp 00000000 08:06 155649                     /usr/lib/libglade/2.0/libgnome.so
7f29a3ded000-7f29a3fed000 ---p 00007000 08:06 155649                     /usr/lib/libglade/2.0/libgnome.so
7f29a3fed000-7f29a3fef000 r--p 00007000 08:06 155649                     /usr/lib/libglade/2.0/libgnome.so
7f29a3fef000-7f29a3ff0000 rw-p 00009000 08:06 155649                     /usr/lib/libglade/2.0/libgnome.so
7f29a3ff0000-7f29a4000000 r-xp 00000000 08:06 1433712                    /usr/lib/rhythmbox/plugins/visualizer/libvisualizer.so
7f29a4000000-7f29a4200000 ---p 00010000 08:06 1433712                    /usr/lib/rhythmbox/plugins/visualizer/libvisualizer.so
7f29a4200000-7f29a4201000 r--p 00010000 08:06 1433712                    /usr/lib/rhythmbox/plugins/visualizer/libvisualizer.so
7f29a4201000-7f29a4202000 rw-p 00011000 08:06 1433712                    /usr/lib/rhythmbox/plugins/visualizer/libvisualizer.so
7f29a4202000-7f29a4237000 r-xp 00000000 08:06 1287922                    /usr/lib/python2.6/lib-dynload/pyexpat.so
7f29a4237000-7f29a4436000 ---p 00035000 08:06 1287922                    /usr/lib/python2.6/lib-dynload/pyexpat.so
7f29a4436000-7f29a4439000 r--p 00034000 08:06 1287922                    /usr/lib/python2.6/lib-dynload/pyexpat.so
7f29a4439000-7f29a443b000 rw-p 00037000 08:06 1287922                    /usr/lib/python2.6/lib-dynload/pyexpat.so
7f29a443b000-7f29a4445000 r-xp 00000000 08:06 1287923                    /usr/lib/python2.6/lib-dynload/_elementtree.so
7f29a4445000-7f29a4644000 ---p 0000a000 08:06 1287923                    /usr/lib/python2.6/lib-dynload/_elementtree.so
7f29a4644000-7f29a4645000 r--p 00009000 08:06 1287923                    /usr/lib/python2.6/lib-dynload/_elementtree.so
7f29a4645000-7f29a4646000 rw-p 0000a000 08:06 1287923                    /usr/lib/python2.6/lib-dynload/_elementtree.so
7f29a4646000-7f29a4657000 r-xp 00000000 08:06 1689382                    /usr/lib/python-support/python-gconf/python2.6/gtk-2.0/gconf.so
7f29a4657000-7f29a4856000 ---p 00011000 08:06 1689382                    /usr/lib/python-support/python-gconf/python2.6/gtk-2.0/gconf.so
7f29a4856000-7f29a4858000 r--p 00010000 08:06 1689382                    /usr/lib/python-support/python-gconf/python2.6/gtk-2.0/gconf.so
7f29a4858000-7f29a485a000 rw-p 00012000 08:06 1689382                    /usr/lib/python-support/python-gconf/python2.6/gtk-2.0/gconf.so
7f29a485a000-7f29a485f000 r-xp 00000000 08:06 1605893                    /usr/lib/python-support/python-glade2/python2.6/gtk-2.0/gtk/glade.so
7f29a485f000-7f29a4a5e000 ---p 00005000 08:06 1605893                    /usr/lib/python-support/python-glade2/python2.6/gtk-2.0/gtk/glade.so
7f29a4a5e000-7f29a4a5f000 r--p 00004000 08:06 1605893                    /usr/lib/python-support/python-glade2/python2.6/gtk-2.0/gtk/glade.so
7f29a4a5f000-7f29a4a60000 rw-p 00005000 08:06 1605893                    /usr/lib/python-support/python-glade2/python2.6/gtk-2.0/gtk/glade.so
7f29a4a60000-7f29a4a6a000 r-xp 00000000 08:06 1433705                    /usr/lib/rhythmbox/plugins/iradio/libiradio.so
7f29a4a6a000-7f29a4c69000 ---p 0000a000 08:06 1433705                    /usr/lib/rhythmbox/plugins/iradio/libiradio.so
7f29a4c69000-7f29a4c6a000 r--p 00009000 08:06 1433705                    /usr/lib/rhythmbox/plugins/iradio/libiradio.so
7f29a4c6a000-7f29a4c6b000 rw-p 0000a000 08:06 1433705                    /usr/lib/rhythmbox/plugins/iradio/libiradio.so
7f29a4c6b000-7f29a4cc5000 r-xp 00000000 08:06 1196217                    /usr/lib/libgpod.so.4.0.0
7f29a4cc5000-7f29a4ec4000 ---p 0005a000 08:06 1196217                    /usr/lib/libgpod.so.4.0.0
7f29a4ec4000-7f29a4ec8000 r--p 00059000 08:06 1196217                    /usr/lib/libgpod.so.4.0.0
7f29a4ec8000-7f29a4ec9000 rw-p 0005d000 08:06 1196217                    /usr/lib/libgpod.so.4.0.0
7f29a4ec9000-7f29a4eda000 r-xp 00000000 08:06 1434181                    /usr/lib/rhythAborted

```

Can anyone point me towards a fix...?

---

