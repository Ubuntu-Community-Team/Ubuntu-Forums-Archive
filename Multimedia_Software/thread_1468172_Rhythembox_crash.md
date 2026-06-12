---
title: "Rhythembox crash"
date: 2010-05-01
forum: Multimedia Software
---

### Post by wutzi on 2010-05-01
Hi 
I got a fresh install of 10.04. Whenever I try to launch Rhythembox I get this

*** glibc detected *** rhythmbox: free(): invalid pointer: 0x00007f65b6dcf588 ***
======= Backtrace: =========
/lib/libc.so.6(+0x775b6)[0x7f65b6ac85b6]
/lib/libc.so.6(cfree+0x73)[0x7f65b6acee53]
/lib/libusb-0.1.so.4(usb_destroy_configuration+0xc3)[0x7f65a0200113]
/lib/libusb-0.1.so.4(usb_free_dev+0x9)[0x7f65a01ff8c9]
/lib/libusb-0.1.so.4(usb_find_devices+0xce)[0x7f65a01ffc9e]
/usr/lib/libmtp.so.8(+0x1caf5)[0x7f65a0423af5]
/usr/lib/libmtp.so.8(LIBMTP_Detect_Raw_Devices+0x1f)[0x7f65a042547f]
/usr/lib/rhythmbox/plugins/mtpdevice/libmtpdevice.so(+0x7a08)[0x7f65a0655a08]
/usr/lib/librhythmbox-core.so.0(rb_marshal_OBJECT__OBJECT+0x98)[0x7f65bbe61ec8]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x15e)[0x7f65b7b925de]
/usr/lib/libgobject-2.0.so.0(+0x21598)[0x7f65b7ba6598]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x639)[0x7f65b7ba78b9]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x7f65b7ba8033]
/usr/lib/librhythmbox-core.so.0(+0x5979a)[0x7f65bbde479a]
/usr/lib/librhythmbox-core.so.0(rb_removable_media_manager_scan+0x20d)[0x7f65bbde4a1d]
/usr/lib/librhythmbox-core.so.0(+0x48235)[0x7f65bbdd3235]
/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1f2)[0x7f65b74d98c2]
/lib/libglib-2.0.so.0(+0x42748)[0x7f65b74dd748]
/lib/libglib-2.0.so.0(g_main_loop_run+0x195)[0x7f65b74ddc55]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xa7)[0x7f65bb037af7]
rhythmbox(main+0x3cb)[0x403e8b]
/lib/libc.so.6(__libc_start_main+0xfd)[0x7f65b6a6fc4d]
rhythmbox[0x403919]
======= Memory map: ========
00400000-00408000 r-xp 00000000 08:03 132266                             /usr/bin/rhythmbox
00607000-00608000 r--p 00007000 08:03 132266                             /usr/bin/rhythmbox
00608000-00609000 rw-p 00008000 08:03 132266                             /usr/bin/rhythmbox
008b6000-018bd000 rw-p 00000000 00:00 0                                  [heap]
7f659eef7000-7f659ef57000 rw-s 00000000 00:04 1376279                    /SYSV00000000 (deleted)
7f659ef57000-7f659ef96000 r-xp 00000000 08:03 134642                     /usr/lib/libibus.so.1.0.0
7f659ef96000-7f659f196000 ---p 0003f000 08:03 134642                     /usr/lib/libibus.so.1.0.0
7f659f196000-7f659f198000 r--p 0003f000 08:03 134642                     /usr/lib/libibus.so.1.0.0
7f659f198000-7f659f199000 rw-p 00041000 08:03 134642                     /usr/lib/libibus.so.1.0.0
7f659f199000-7f659f19a000 rw-p 00000000 00:00 0 
7f659f19a000-7f659f19f000 r-xp 00000000 08:03 138405                     /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
7f659f19f000-7f659f39f000 ---p 00005000 08:03 138405                     /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
7f659f39f000-7f659f3a0000 r--p 00005000 08:03 138405                     /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
7f659f3a0000-7f659f3a1000 rw-p 00006000 08:03 138405                     /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
7f659f3a1000-7f659f3af000 r-xp 00000000 08:03 661786                     /usr/lib/rhythmbox/plugins/visualizer/libvisualizer.so
7f659f3af000-7f659f5ae000 ---p 0000e000 08:03 661786                     /usr/lib/rhythmbox/plugins/visualizer/libvisualizer.so
7f659f5ae000-7f659f5af000 r--p 0000d000 08:03 661786                     /usr/lib/rhythmbox/plugins/visualizer/libvisualizer.so
7f659f5af000-7f659f5b0000 rw-p 0000e000 08:03 661786                     /usr/lib/rhythmbox/plugins/visualizer/libvisualizer.so
7f659f5b0000-7f659f5b8000 r-xp 00000000 08:03 134301                     /usr/lib/libdbusmenu-gtk.so.1.0.6
7f659f5b8000-7f659f7b7000 ---p 00008000 08:03 134301                     /usr/lib/libdbusmenu-gtk.so.1.0.6
7f659f7b7000-7f659f7b8000 r--p 00007000 08:03 134301                     /usr/lib/libdbusmenu-gtk.so.1.0.6
7f659f7b8000-7f659f7b9000 rw-p 00008000 08:03 134301                     /usr/lib/libdbusmenu-gtk.so.1.0.6
7f659f7b9000-7f659f7ce000 r-xp 00000000 08:03 134697                     /usr/lib/libjson-glib-1.0.so.0.706.0
7f659f7ce000-7f659f9cd000 ---p 00015000 08:03 134697                     /usr/lib/libjson-glib-1.0.so.0.706.0
7f659f9cd000-7f659f9ce000 r--p 00014000 08:03 134697                     /usr/lib/libjson-glib-1.0.so.0.706.0
7f659f9ce000-7f659f9cf000 rw-p 00015000 08:03 134697                     /usr/lib/libjson-glib-1.0.so.0.706.0
7f659f9cf000-7f659f9d9000 r-xp 00000000 08:03 134681                     /usr/lib/libindicator.so.0.0.0
7f659f9d9000-7f659fbd8000 ---p 0000a000 08:03 134681                     /usr/lib/libindicator.so.0.0.0
7f659fbd8000-7f659fbd9000 r--p 00009000 08:03 134681                     /usr/lib/libindicator.so.0.0.0
7f659fbd9000-7f659fbda000 rw-p 0000a000 08:03 134681                     /usr/lib/libindicator.so.0.0.0
7f659fbda000-7f659fbe8000 r-xp 00000000 08:03 134299                     /usr/lib/libdbusmenu-glib.so.1.0.6
7f659fbe8000-7f659fde8000 ---p 0000e000 08:03 134299                     /usr/lib/libdbusmenu-glib.so.1.0.6
7f659fde8000-7f659fde9000 r--p 0000e000 08:03 134299                     /usr/lib/libdbusmenu-glib.so.1.0.6
7f659fde9000-7f659fdea000 rw-p 0000f000 08:03 134299                     /usr/lib/libdbusmenu-glib.so.1.0.6
7f659fdea000-7f659fdf2000 r-xp 00000000 08:03 134155                     /usr/lib/libappindicator.so.0.0.0
7f659fdf2000-7f659fff1000 ---p 00008000 08:03 134155                     /usr/lib/libappindicator.so.0.0.0
7f659fff1000-7f659fff2000 r--p 00007000 08:03 134155                     /usr/lib/libappindicator.so.0.0.0
7f659fff2000-7f659fff3000 rw-p 00008000 08:03 134155                     /usr/lib/libappindicator.so.0.0.0
7f659fff3000-7f659fffc000 r-xp 00000000 08:03 661779                     /usr/lib/rhythmbox/plugins/status-icon/libstatus-icon.so
7f659fffc000-7f65a01fc000 ---p 00009000 08:03 661779                     /usr/lib/rhythmbox/plugins/status-icon/libstatus-icon.so
7f65a01fc000-7f65a01fd000 r--p 00009000 08:03 661779                     /usr/lib/rhythmbox/plugins/status-icon/libstatus-icon.so
7f65a01fd000-7f65a01fe000 rw-p 0000a000 08:03 661779                     /usr/lib/rhythmbox/plugins/status-icon/libstatus-icon.so
7f65a01fe000-7f65a0205000 r-xp 00000000 08:03 786703                     /lib/libusb-0.1.so.4.4.4
7f65a0205000-7f65a0404000 ---p 00007000 08:03 786703                     /lib/libusb-0.1.so.4.4.4
7f65a0404000-7f65a0405000 r--p 00006000 08:03 786703                     /lib/libusb-0.1.so.4.4.4
7f65a0405000-7f65a0407000 rw-p 00007000 08:03 786703                     /lib/libusb-0.1.so.4.4.4
7f65a0407000-7f65a0445000 r-xp 00000000 08:03 134762                     /usr/lib/libmtp.so.8.3.2
7f65a0445000-7f65a0644000 ---p 0003e000 08:03 134762                     /usr/lib/liAborted


I tried to reinstall it but it didn't help.
Any ideas?

Thank You

---

### Post by PinchedNerve on 2010-05-01
Mine works (sort of)

I was playing some MP3s & after about 5 folders (folders being full length Artist CDs) the player plays about the first 5 seconds of a song & then stops. Seems like its like a memory leak.  I look at the system monitor & it says I am only using 1 gig out of a total of 4.  No idea, it just stops now.


Edit: Reboot gets the player working properly again for me. But I don't think anyone will want to have to reboot just to have extended play.

---

