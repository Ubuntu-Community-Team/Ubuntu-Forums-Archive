---
title: "Rhythmbox wont start"
date: 2010-05-09
forum: Multimedia Software
---

### Post by breimer273 on 2010-05-09
Alright so here's the problem. Every time I try to start rhythmbox all it does is open for like a split second and then close again. Only thing I did was install updates and then this started happening. Any ideas?

---

### Post by beanstalker on 2010-05-09
I have exactly the same problem. I am running 10.04 on MacBook Pro 5,3. I have tried completely removing and reinstalling but to no avail.
Would greatly appreciate any help on this.

Cheers.

---

### Post by breimer273 on 2010-05-09
I forgot to mention this is 10.04 on a MBP 5.5

---

### Post by Yellow Pasque on 2010-05-09
Try opening it in a terminal.

---

### Post by breimer273 on 2010-05-10
Alright when opening rhythmbox in terminal this is what I get
> *** glibc detected *** rhythmbox: free(): invalid pointer: 0xb697e518 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(+0x6b591)[0xb6892591]
/lib/tls/i686/cmov/libc.so.6(+0x6cde8)[0xb6893de8]
/lib/tls/i686/cmov/libc.so.6(cfree+0x6d)[0xb6896ecd]
/lib/libusb-0.1.so.4(usb_destroy_configuration+0xdb)[0xb34e4c6b]
/lib/libusb-0.1.so.4(usb_free_dev+0x22)[0xb34e43a2]
/lib/libusb-0.1.so.4(usb_find_devices+0xe0)[0xb34e4820]
/usr/lib/libmtp.so.8(+0x162fe)[0xb35022fe]
/usr/lib/libmtp.so.8(LIBMTP_Detect_Raw_Devices+0x19)[0xb3504149]
/usr/lib/rhythmbox/plugins/mtpdevice/libmtpdevice.so(+0x5d4e)[0xb353ad4e]
/usr/lib/librhythmbox-core.so.0(rb_marshal_OBJECT__OBJECT+0x94)[0xb78384b4]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1b2)[0xb6ccf252]
/usr/lib/libgobject-2.0.so.0(+0x1f99d)[0xb6ce399d]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x5d3)[0xb6ce4c33]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26)[0xb6ce5256]
/usr/lib/librhythmbox-core.so.0(+0x4915b)[0xb77ab15b]
/usr/lib/librhythmbox-core.so.0(rb_removable_media_manager_scan+0x23e)[0xb77ab41e]
/usr/lib/librhythmbox-core.so.0(+0x35a25)[0xb7797a25]
/lib/libglib-2.0.so.0(+0x39661)[0xb6c24661]
/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1d5)[0xb6c265e5]
/lib/libglib-2.0.so.0(+0x3f2d8)[0xb6c2a2d8]
/lib/libglib-2.0.so.0(g_main_loop_run+0x187)[0xb6c2a817]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9)[0xb7463299]
rhythmbox(main+0x4ae)[0x804b33e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0xb683dbd6]
rhythmbox[0x804ad21]
======= Memory map: ========
08048000-0804e000 r-xp 00000000 08:02 2124       /usr/bin/rhythmbox
0804e000-0804f000 r--p 00006000 08:02 2124       /usr/bin/rhythmbox
0804f000-08050000 rw-p 00007000 08:02 2124       /usr/bin/rhythmbox
09f70000-0a9ee000 rw-p 00000000 00:00 0          [heap]
b31f5000-b3255000 rw-s 00000000 00:04 2949153    /SYSV00000000 (deleted)
b3255000-b328e000 r-xp 00000000 08:02 1522       /usr/lib/libibus.so.1.0.0
b328e000-b328f000 r--p 00039000 08:02 1522       /usr/lib/libibus.so.1.0.0
b328f000-b3290000 rw-p 0003a000 08:02 1522       /usr/lib/libibus.so.1.0.0
b32a0000-b3300000 rw-s 00000000 00:04 2916384    /SYSV00000000 (deleted)
b3300000-b3359000 rw-p 00000000 00:00 0 
b3359000-b3400000 ---p 00000000 00:00 0 
b3400000-b3405000 r-xp 00000000 08:02 918159     /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
b3405000-b3406000 r--p 00004000 08:02 918159     /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
b3406000-b3407000 rw-p 00005000 08:02 918159     /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
b3407000-b3493000 r--p 00000000 08:02 525339     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b3493000-b349a000 r-xp 00000000 08:02 865        /usr/lib/libdbusmenu-gtk.so.1.0.6
b349a000-b349b000 r--p 00006000 08:02 865        /usr/lib/libdbusmenu-gtk.so.1.0.6
b349b000-b349c000 rw-p 00007000 08:02 865        /usr/lib/libdbusmenu-gtk.so.1.0.6
b349c000-b34ae000 r-xp 00000000 08:02 2791       /usr/lib/libjson-glib-1.0.so.0.706.0
b34ae000-b34af000 r--p 00011000 08:02 2791       /usr/lib/libjson-glib-1.0.so.0.706.0
b34af000-b34b0000 rw-p 00012000 08:02 2791       /usr/lib/libjson-glib-1.0.so.0.706.0
b34b0000-b34b9000 r-xp 00000000 08:02 940        /usr/lib/libindicator.so.0.0.0
b34b9000-b34ba000 r--p 00008000 08:02 940        /usr/lib/libindicator.so.0.0.0
b34ba000-b34bb000 rw-p 00009000 08:02 940        /usr/lib/libindicator.so.0.0.0
b34bb000-b34c8000 r-xp 00000000 08:02 802        /usr/lib/libdbusmenu-glib.so.1.0.6
b34c8000-b34c9000 r--p 0000c000 08:02 802        /usr/lib/libdbusmenu-glib.so.1.0.6
b34c9000-b34ca000 rw-p 0000d000 08:02 802        /usr/lib/libdbusmenu-glib.so.1.0.6
b34ca000-b34d1000 r-xp 00000000 08:02 2420       /usr/lib/libappindicator.so.0.0.0
b34d1000-b34d2000 r--p 00006000 08:02 2420       /usr/lib/libappindicator.so.0.0.0
b34d2000-b34d3000 rw-p 00007000 08:02 2420       /usr/lib/libappindicator.so.0.0.0
b34d4000-b34e1000 r-xp 00000000 08:02 659367     /usr/lib/rhythmbox/plugins/visualizer/libvisualizer.so
b34e1000-b34e2000 r--p 0000c000 08:02 659367     /usr/lib/rhythmbox/plugins/visualizer/libvisualizer.so
b34e2000-b34e3000 rw-p 0000d000 08:02 659367     /usr/lib/rhythmbox/plugins/visualizer/libvisualizer.so
b34e3000-b34e9000 r-xp 00000000 08:02 2795       /lib/libusb-0.1.so.4.4.4
b34e9000-b34ea000 r--p 00005000 08:02 2795       /lib/libusb-0.1.so.4.4.4
b34ea000-b34ec000 rw-p 00006000 08:02 2795       /lib/libusb-0.1.so.4.4.4
b34ec000-b351e000 r-xp 00000000 08:02 1030       /usr/lib/libmtp.so.8.3.2
b351e000-b351f000 ---p 00032000 08:02 1030       /usr/lib/libmtp.so.8.3.2
b351f000-b3524000 r--p 00032000 08:02 1030       /usr/lib/libmtp.so.8.3.2
b3524000-b3525000 rw-p 00037000 08:02 1030       /usr/lib/libmtp.so.8.3.2
b352b000-b3533000 r-xp 00000000 08:02 659353     /usr/lib/rhythmbox/plugins/status-icon/libstatus-icon.so
b3533000-b3534000 r--p 00007000 08:02 659353     /usr/lib/rhythmbox/plugins/status-icon/libstatus-icon.so
b3534000-b3535000 rw-p 00008000 08:02 659353     /usr/lib/rhythmbox/plugins/status-icon/libstatus-icon.so
b3535000-b3545000 r-xp 00000000 08:02 659294     /usr/lib/rhythmbox/plugins/mtpdevice/libmtpdevice.so
b3545000-b3546000 r--p 0000f000 08:02 659294     /usr/lib/rhythmbox/plugins/mtpdevice/libmtpdevice.so
b3546000-b3547000 rw-p 00010000 08:02 659294     /usr/lib/rhythmbox/plugins/mtpdevice/libmtpdevice.so
b3547000-b360a000 r-xp 00000000 08:02 658        /usr/lib/libasound.so.2.0.0
b360a000-b360e000 r--p 000c2000 08:02 658        /usr/lib/libasound.so.2.0.0
b360e000-b360f000 rw-p 000c6000 08:02 658        /usr/lib/libasound.so.2.0.0
b360f000-b3631000 r-xp 00000000 08:02 140        /usr/lib/libaudiofile.so.0.0.2
b3631000-b3632000 r--p 00021000 08:02 140        /usr/lib/libaudiofile.so.0.0.2
b3632000-b3634000 rw-p 00022000 08:02 140        /usr/lib/libaudiofile.so.0.0.2
b3634000-b363d000 r-xp 00000000 08:02 1266       /usr/lib/libesd.so.0.2.39
b363d000-b363e000 r--p 00008000 08:02 1266       /usr/lib/libesd.so.0.2.39
b363e000-b363f000 rw-p 00009000 08:02 1266       /usr/lib/libesd.so.0.2.39
b363f000-b3698000 r-xp 00000000 08:02 3296       /usr/lib/libgnomevfs-2.so.0.2400.2
b3698000-b369a000 r--p 00058000 08:02 3296       /usr/lib/libgnomevfs-2.so.0.2400.2
b369a000-b369c000 rw-p 0005a000 08:02 3296       /usr/lib/libgnomevfs-2.so.0.2400.2
b369c000-b36af000 r-xp 00000000 08:02 2173       /usr/lib/libbonobo-activation.so.4.0.0
b36af000-b36b0000 r--p 00012000 08:02 2173       /usr/lib/libbonobo-activation.so.4.0.0
b36b0000-b36b1000 rw-p 00013000 08:02 2173       /usr/lib/libbonobo-activation.so.4.0.0
b36b1000-b36b2000 rw-p 00000000 00:00 0 
b36b2000-b3703000 r-xp 00000000 08:02 2172       /usr/lib/libbonobo-2.so.0.0.0
b3703000-b3704000 ---p 00051000 08:02 2172       /usr/lib/libbonobo-2.so.0.0.0Aborted


---

### Post by vegham on 2010-05-10
Have exactly the same problem on MBP5,3.

---

### Post by StewD on 2010-05-10
I've just had the same problem...I resolved it by using "Ubunutu Software Centre" to remove Rythmbox and then the same application to reinstall.

Might be worth ago?

---

### Post by breimer273 on 2010-05-10
> **StewD said:**
> I've just had the same problem...I resolved it by using "Ubunutu Software Centre" to remove Rythmbox and then the same application to reinstall.

Might be worth ago?

I have already tried that solution. I might try it again just to make sure but it didn't work for me the first time.

---

### Post by breimer273 on 2010-05-15
Ok I just wanted to give a little update because I am still having the problem. I tried uninstalling and reinstalling Rhythmbox and that worked until...I restarted the computer. Once I restarted the computer it started happening again. I don't know if this is normal or what but it really is kind of annoying. If you guys need anymore information I can give it to you but I don't know what you would be looking for.

---

### Post by nmyrick on 2010-05-16
Have you tried Banshee Media Player?  I like it better than RhythmBox anyway. 

One thing about Banshee though, if you have an IPod, and it doesn't recognize it, then you need to install Podsleuth to get it to recognize the IPod.

---

### Post by WinterRain on 2010-05-16
Sometimes rhythmbox opens without seeing it on the screen. Check your panel for a little icon for rhythmbox and click it to "show rhythmbox".

---

### Post by breimer273 on 2010-05-16
> **nmyrick said:**
> Have you tried Banshee Media Player?  I like it better than RhythmBox anyway. 

One thing about Banshee though, if you have an IPod, and it doesn't recognize it, then you need to install Podsleuth to get it to recognize the IPod.

I have not tried Banshee. I will give it a try though. Thanks for the tip I will let you know how it works out.

---

### Post by vkcaspervk on 2010-05-16
> **nmyrick said:**
> Have you tried Banshee Media Player?  I like it better than RhythmBox anyway. 

One thing about Banshee though, if you have an IPod, and it doesn't recognize it, then you need to install Podsleuth to get it to recognize the IPod.

Does that work for iphone also? I cant get mine to show in rhythmbox and 10.04...

I get "No iPods were found in the HAL device tree" when I use it... 

Tho I can browse it with nautilus... : shruggs :

---

### Post by nmyrick on 2010-05-16
As far as I know, it does not work for I-Phones.  Apple tries their best to keep their products from being compatible with other OS's.  The only reason they make their products compatible with Microsoft is because Microsoft has the lion share of the computer market.

---

### Post by superdexter on 2010-05-22
I'm having a very similar problem (rhytmbox opens and immediately closes) on my mbpro 5,2 with ubuntu dual-boot installed.   I'm curious if any of you have filed a bug that I might be able to follow?  If no one has, then please post so I'll know to go open a bug report.

---

### Post by Yellow Pasque on 2010-05-22
Possibly related:
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/549934](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/549934)

---

### Post by newb85 on 2010-05-25
Your problems may be caused by the Ubuntu One Music Store plugin.  If you don't use the plugin, you may disable it through gconf-editor (apps-rhythmbox-plugins-umusicstore, uncheck active) or remove it (in synaptic it's called rhythmbox-ubuntuone-music-store).

---

### Post by QB89Dragon on 2010-05-30
I have this same problem with a macbook pro 5,5. At first I thought it was a filesystem monitoring problem with the fact that it has a HFS+ partition. It has the same symptoms you describe, reboots triggering the problem etc. I went through every plugin in turn in GConf editor, and it turned out to be the MTP device plugin that was causing the problems. See if turning it off resolves your issue and then we have probably found the source of the bug and can contact the developer of that plugin.
Cheers y'all. :guitar:

---

### Post by proycon on 2010-05-31
I can confirm, unsetting /apps/rhythmbox/plugins/mtpdevice/active in gconf-editor resolved this bug for me. (and I also uninstalled the Ubuntu Music Store thing, not sure if it's related)

---

### Post by JohnAtilano on 2010-06-11
> **proycon said:**
> I can confirm, unsetting /apps/rhythmbox/plugins/mtpdevice/active in gconf-editor resolved this bug for me. (and I also uninstalled the Ubuntu Music Store thing, not sure if it's related)

I had the exact same problem.  Unchecking the /apps/rhythmbox/plugins/mtpdevice/active box in gconf-editor fixed the issue.

I'm an a MacBook Pro 5,1.  Ubuntu 10.04.

---

