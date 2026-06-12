---
title: "ipod: gtkpod will not run / Amarok cannot write"
date: 2007-03-18
forum: Multimedia &amp; Video
---

### Post by Apostata on 2007-03-18
Hello all,

  I'm having terrible luck finding an app that can do the basic work of transferring tracks to my ipod (mini).

  I dumped gtkpod for Amarok, which worked beautifully until recently...inexplicably, now whenever I copy songs over w/ Amarok my ipod simply can't play them.

  Rhythmbox is ok...in the barest sense of the word. It can't create or transfer playlists over to an ipod unfortunately.

  Yamipod is a joke. It looks and feels like a ten year old FTP client, albeit one that only shows you the remote server.

  So...I'm trying to use gtkpod again, but strangely it won't work now. Here's the error I get:

> me@computer:$ gtkpod
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
*** glibc detected *** gtkpod: realloc(): invalid next size: 0x085facd8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb75fe3aa]
/lib/tls/i686/cmov/libc.so.6(__libc_realloc+0xff)[0xb75fecdf]
/usr/lib/libglib-2.0.so.0(g_realloc+0x3b)[0xb77cebab]
/usr/lib/libglib-2.0.so.0[0xb77e30dc]
/usr/lib/libglib-2.0.so.0(g_string_insert_len+0x73)[0xb77e3603]
/usr/lib/libglib-2.0.so.0(g_string_append_len+0x46)[0xb77e3956]
/usr/lib/libglib-2.0.so.0[0xb77b90ec]
/usr/lib/libglib-2.0.so.0(g_build_filename+0x30)[0xb77b92f0]
/usr/lib/libgpod.so.0(itdb_resolve_path+0x9d)[0xb783728d]
/usr/lib/libgpod.so.0(itdb_get_control_dir+0x6c)[0xb783753c]
/usr/lib/libgpod.so.0[0xb78375ac]
/usr/lib/libgpod.so.0(itdb_device_read_sysinfo+0x6a)[0xb78473ea]
/usr/lib/libgpod.so.0(itdb_device_set_mountpoint+0x44)[0xb78475b4]
/usr/lib/libgpod.so.0(itdb_set_mountpoint+0x3a)[0xb783430a]
gtkpod(init_data+0x452)[0x8073e42]
gtkpod(main+0x1c2)[0x8089be2]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb75ab8cc]
gtkpod[0x805db81]
======= Memory map: ========
08048000-080b5000 r-xp 00000000 03:01 3007930    /usr/bin/gtkpod
080b5000-080b7000 rw-p 0006c000 03:01 3007930    /usr/bin/gtkpod
080b7000-08605000 rw-p 080b7000 00:00 0          [heap]
b5f00000-b5f21000 rw-p b5f00000 00:00 0
b5f21000-b6000000 ---p b5f21000 00:00 0
b60b9000-b60ba000 ---p b60b9000 00:00 0
b60ba000-b68ba000 rw-p b60ba000 00:00 0
b68ba000-b692b000 r--p 00000000 03:01 3042090    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b692b000-b6955000 r-xp 00000000 03:01 3005637    /usr/lib/libkdefx.so.4.2.0
b6955000-b6956000 rw-p 0002a000 03:01 3005637    /usr/lib/libkdefx.so.4.2.0
b6956000-b6978000 r-xp 00000000 03:01 3145325    /usr/lib/kde3/plugins/styles/lipstik.so
b6978000-b6979000 rw-p 00022000 03:01 3145325    /usr/lib/kde3/plugins/styles/lipstik.so
b6979000-b698e000 r-xp 00000000 03:01 2996598    /usr/lib/libICE.so.6.3.0
b698e000-b698f000 rw-p 00014000 03:01 2996598    /usr/lib/libICE.so.6.3.0
b698f000-b6991000 rw-p b698f000 00:00 0
b6991000-b6999000 r-xp 00000000 03:01 2996600    /usr/lib/libSM.so.6.0.0
b6999000-b699a000 rw-p 00007000 03:01 2996600    /usr/lib/libSM.so.6.0.0
b699a000-b69ab000 r-xp 00000000 03:01 2996596    /usr/lib/libXft.so.2.1.2
b69ab000-b69ac000 rw-p 00010000 03:01 2996596    /usr/lib/libXft.so.2.1.2
b69ac000-b69ca000 r-xp 00000000 03:01 2996939    /usr/lib/libjpeg.so.62.0.0
b69ca000-b69cb000 rw-p 0001d000 03:01 2996939    /usr/lib/libjpeg.so.62.0.0
b69cb000-b6a15000 r-xp 00000000 03:01 2996602    /usr/lib/libXt.so.6.0.0
b6a15000-b6a19000 rw-p 00049000 03:01 2996602    /usr/lib/libXt.so.6.0.0
b6a19000-b6a2e000 r-xp 00000000 03:01 2997202    /usr/lib/libaudio.so.2.4
b6a2e000-b6a2f000 rw-p 00014000 03:01 2997202    /usr/lib/libaudio.so.2.4
b6a2f000-b71c4000 r-xp 00000000 03:01 2997925    /usr/lib/libqt-mt.so.3.3.6
b71c4000-b720b000 rw-p 00794000 03:01 2997925    /usr/lib/libqt-mt.so.3.3.6
b720b000-b720e000 rw-p b720b000 00:00 0
b720e000-b722c000 r-xp 00000000 03:01 3188869    /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so
b722c000-b722d000 rw-p 0001e000 03:01 3188869    /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so
b722d000-b7236000 r-xp 00000000 03:01 65746      /lib/tls/i686/cmov/libnss_files-2.4.so
b7236000-b7238000 rw-p 00008000 03:01 65746      /lib/tls/i686/cmov/libnss_files-2.4.so
b7238000-b7240000 r-xp 00000000 03:01 65748      /lib/tls/i686/cmov/libnss_nis-2.4.so
b7240000-b7242000 rw-p 00007000 03:01 65748      /lib/tls/i686/cmov/libnss_nis-2.4.so
b7242000-b7254000 r-xp 00000000 03:01 65743      /lib/tls/i686/cmov/libnsl-2.4.so
b7254000-b7256000 rw-p 00011000 03:01 65743      /lib/tls/i686/cmov/libnsl-2.4.so
b7256000-b7258000 rw-p b7256000 00:00 0
b7258000-b725f000 r-xp 00000000 03:01 65744      /lib/tls/i686/cmov/libnss_compat-2.4.so
b725f000-b7261000 rw-p 00006000 03:01 65744      /lib/tls/i686/cmov/libnss_compat-2.4.so
b7273000-b7275000 r-xp 00000000 03:01 3076641    /usr/lib/pango/1.5.0/modules/pango-basic-fc.so
b7275000-b7276000 rw-p 00001000 03:01 3076641    /usr/lib/pango/1.5.0/modules/pango-basic-fc.so
b7276000-b727a000 r-xp 00000000 03:01 2681729    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b727a000-b727b000 rw-p 00003000 03:01 2681729    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b727b000-b7296000 r--p 00000000 03:01 3483121    /usr/share/locale/en_CA/LC_MESSAGES/gtk20-properties.mo
b7296000-b72a0000 r--p 00000000 03:01 3483120    /usr/share/locale/en_CA/LC_MESSAGES/gtk20.mo
b72a0000-b72a1000 r-xp 00000000 03:01 3041964    /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
b72a1000-b72a2000 rw-p 00000000 03:01 3041964    /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
b72a2000-b72d5000 r--p 00000000 03:01 3025781    /usr/lib/locale/en_CA.utf8/LC_CTYPE
b72d5000-b73ac000 r--p 00000000 03:01 3025784    /usr/lib/locale/en_CA.utf8/LC_COLLATE
b73ac000-b73ae000 rw-p b73ac000 00:00 0
b73ae000-b73b8000 r-xp 00000000 03:01 65424      /lib/libgcc_s.so.1
b73b8000-b73b9000 rw-p 00009000 03:01 65424      /lib/libgcc_s.so.1
b73b9000-b748d000 r-xp 00000000 03:01 2994969    /usr/lib/libstdc++.so.6.0.8
b748d000-b7490000 r--p 000d4000 03:01 2994969    /usr/lib/libstdc++.so.6.0.8
b7490000-b7492000 rw-p 000d7000 03:01 2994969    /usr/lib/libstdc++.so.6.0.8
b7492000-b7499000 rw-p b7492000 00:00 0
b7499000-b749d000 r-xp 00000000 03:01 2996535    /usr/lib/libXdmcp.so.6.0.0
b749d000-b749e000 rw-p 00003000 03:01 2996535    /usr/lib/libXdmcp.so.6.0.0
b749e000-b74c1000 r-xp 00000000 03:01 3002463    /usr/lib/libpng12.so.0.1.2.8
b74c1000-b74c2000 rw-p 00023000 03:01 3002463    /usr/lib/libpng12.so.0.1.2.8
b74c2000-b74c4000 r-xp 00000000 03:01 2996533    /usr/lib/libXau.so.6.0.0
b74c4000-b74c5000 rw-p 00001000 03:01 2996533    /usr/lib/libXau.so.6.0.0
b74c5000-b74e1000 r-xp 00000000 03:01 2996545    /usr/lib/libexpat.so.1.0.0
b74e1000-b74e3000 rw-p 0001c000 03:01 2996545    /usr/lib/libexpat.so.1.0.0
b74e3000-b754a000 r-xp 00000000 03:01 2996548    /usr/lib/libfreetype.so.6.3.10
b754a000-b754d000 rw-p 00067000 03:01 2996548    /usr/lib/libfreetype.so.6.3.10
b754d000-b754e000 rw-p b754d000 00:00 0
b754e000-b7578000 r-xp 00000000 03:01 2997284    /usr/lib/libpangoft2-1.0.so.0.1400.5
b7578000-b7579000 rw-p 00029000 03:01 2997284    /usr/lib/libpangoft2-1.0.so.0.1400.5
b7579000-b758c000 r-xp 00000000 03:01 2994571    /usr/lib/libz.so.1.2.3
b758c000-b758d000 rw-p 00012000 03:01 2994571    /usr/lib/libz.so.1.2.3
b758d000-b7594000 r-xp 00000000 03:01 65755      /lib/tls/i686/cmov/librt-2.4.so
b7594000-b7596000 rw-p 00006000 03:01 65755      /lib/tls/i686/cmov/librt-2.4.so
b7596000-b76c3000 r-xp 00000000 03:01 65737      /lib/tls/i686/cmov/libc-2.4.so
b76c3000-b76c5000 r--p 0012c000 03:01 65737      /lib/tls/i686/cmov/libc-2.4.so
b76c5000-b76c7000 rw-p 0012e000 03:01 65737      /lib/tls/i686/cmov/libc-2.4.so
b76c7000-b76ca000 rw-p b76c7000 00:00 0
b76ca000-b76d9000 r-xp 00000000 03:01 65753      /lib/tls/i686/cmov/libpthread-2.4.so
b76d9000-b76db000 rw-p 0000f000 03:01 65753      /lib/tls/i686/cmov/libpthread-2.4.so
b76db000-b76de000 rw-p b76db000 00:00 0
b76de000-b76ec000 r-xp 00000000 03:01 3001758    /usr/lib/libid3tag.so.0.3.0
b76ec000-b76ee000 rw-p 0000d000 03:01 3001758    /usr/lib/libid3tag.so.0.3.0
b76ee000-b7798000 r-xp 00000000 03:01 3002549    /usr/lib/libmp4v2.so.0.0.0
b7798000-b779c000 rw-p 000a9000 03:01 3002549    /usr/lib/libmp4v2.so.0.0.0
b779c000-b782d000 r-xp 00000000 03:01 2997227    /usr/lib/libglib-2.0.so.0.1200.4
b782d000-b782e000 rw-p 00091000 03:01 2997227    /usr/lib/libglib-2.0.so.0.1200.4
b782e000-b784b000 r-xp 00000000 03:01 2998662    /usr/lib/libgpod.so.0.400.0
b784b000-b784c000 rw-p 0001d000 03:01 2998662    /usr/lib/libgpod.so.0.400.0
b784c000-b784e000 r-xp 00000000 03:01 65740      /lib/tls/i686/cmov/libdl-2.4.so
b784e000-b7850000 rw-p 00001000 03:01 65740      /lib/tls/i686/cmov/libdl-2.4.so
b7850000-b7853000 r-xp 00000000 03:01 2997229    /usr/lib/libgmodule-2.0.so.0.1200.4
b7853000-b7854000 rw-p 00002000 03:01 2997229    /usr/lib/libgmodule-2.0.so.0.1200.4
b7854000-b7855000 rw-p b7854000 00:00 0
b7855000-b788e000 r-xp 00000000 03:01 2997228    /usr/lib/libgobject-2.0.so.0.1200.4
b788e000-b788f000 rw-p 00038000 03:01 2997228    /usr/lib/libgobject-2.0.so.0.1200.4
b788f000-b7955000 r-xp 00000000 03:01 2996537    /usr/lib/libX11.so.6.2.0
b7955000-b7958000 rw-p 000c5000 03:01 2996537    /usr/lib/libX11.so.6.2.0
b7958000-b79b8000 r-xp 00000000 03:01 2997205    /usr/lib/libcairo.so.2.9.2
b79b8000-b79ba000 rw-p 0005f000 03:01 2997205    /usr/lib/libcairo.so.2.9.2
b79ba000-b79f2000 r-xp 00000000 03:01 2997282    /usr/lib/libpango-1.0.so.0.1400.5
b79f2000-b79f4000 rw-p 00037000 03:01 2997282    /usr/lib/libpango-1.0.so.0.1400.5
b79f4000-b79f8000 r-xp 00000000 03:01 2996543    /usr/lib/libXfixes.so.3.1.0
b79f8000-b79f9000 rw-p 00003000 03:01 2996543    /usr/lib/libXfixes.so.3.1.0
b79f9000-b7a01000 r-xp 00000000 03:01 2996768    /usr/lib/libXcursor.so.1.0.2
b7a01000-b7a02000 rw-p 00007000 03:01 2996768    /usr/lib/libXcursor.so.1.0.2
b7a02000-b7a03000 rw-p b7a02000 00:00 0
b7a03000-b7a05000 r-xp 00000000 03:01 2996689    /usr/lib/libXrandr.so.2.0.0
b7a05000-b7a06000 rw-p 00002000 03:01 2996689    /usr/lib/libXrandr.so.2.0.0
b7a06000-b7a0d000 r-xp 00000000 03:01 2996615    /usr/lib/libXi.so.6.0.0
b7a0d000-b7a0e000 rw-p 00006000 03:01 2996615    /usr/lib/libXi.so.6.0.0
b7a0e000-b7a10000 r-xp 00000000 03:01 2996641    /usr/lib/libXinerama.so.1.0.0
b7a10000-b7a11000 rw-p 00001000 03:01 2996641    /usr/lib/libXinerama.so.1.0.0
b7a11000-b7a18000 r-xp 00000000 03:01 2996594    /usr/lib/libXrender.so.1.3.0
b7a18000-b7a19000 rw-p 00006000 03:01 2996594    /usr/lib/libXrender.so.1.3.0
b7a19000-b7a25000 r-xp 00000000 03:01 2996539    /usr/lib/libXext.so.6.4.0
b7a25000-b7a26000 rw-p 0000c000 03:01 2996539    /usr/lib/libXext.so.6.4.0
b7a26000-b7a4f000 r-xp 00000000 03:01 2996592    /usr/lib/libfontconfig.so.1.0.4
b7a4f000-b7a54000 rw-p 00028000 03:01 2996592    /usr/lib/libfontconfig.so.1.0.4
b7a54000-b7a56000 rw-p b7a54000 00:00 0
b7a56000-b7a5d000 r-xp 00000000 03:01 2997286    /usr/lib/libpangocairo-1.0.so.0.1400.5
b7a5d000-b7a5e000 rw-p 00006000 03:01 2997286    /usr/lib/libpangocairo-1.0.so.0.1400.5
b7a5e000-b7a82000 r-xp 00000000 03:01 65741      /lib/tls/i686/cmov/libm-2.4.so
b7a82000-b7a84000 rw-p 00023000 03:01 65741      /lib/tls/i686/cmov/libm-2.4.so
b7a84000-b7a99000 r-xp 00000000 03:01 2994327    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.6
b7a99000-b7a9a000 rw-p 00015000 03:01 2994327    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.6
b7a9a000-b7ab2000 r-xp 00000000 03:01 2997264    /usr/lib/libatk-1.0.so.0.1213.0
b7ab2000-b7ab4000 rw-p 00017000 03:01 2997264    /usr/lib/libatk-1.0.so.0.1213.0
b7ab4000-b7b35000 r-xp 00000000 03:01 2994328    /usr/lib/libgdk-x11-2.0.so.0.1000.6
b7b35000-b7b38000 rw-p 00081000 03:01 2994328    /usr/lib/libgdk-x11-2.0.so.0.1000.6
b7b38000-b7c4b000 r-xp 00000000 03:01 2996704    /usr/lib/libxml2.so.2.6.26
b7c4b000-b7c50000 rw-p 00113000 03:01 2996704    /usr/lib/libxml2.so.2.6.26
b7c50000-b7c51000 rw-p b7c50000 00:00 0
b7c51000-b7f9a000 r-xp 00000000 03:01 3000419    /usr/lib/libgtk-x11-2.0.so.0.1000.6
b7f9a000-b7fa0000 rw-p 00349000 03:01 3000419    /usr/lib/libgtk-x11-2.0.so.0.1000.6
b7fa0000-b7fa2000 rw-p b7fa0000 00:00 0
b7fa2000-b7fb9000 r-xp 00000000 03:01 2998383    /usr/lib/libglade-2.0.so.0.0.7
b7fb9000-b7fba000 rw-p 00016000 03:01 2998383    /usr/lib/libglade-2.0.so.0.0.7
b7fba000-b7fbe000 r-xp 00000000 03:01 2997230    /usr/lib/libgthread-2.0.so.0.1200.4
b7fbe000-b7fbf000 rw-p 00003000 03:01 2997230    /usr/lib/libgthread-2.0.so.0.1200.4
b7fc0000-b7fc1000 r-xp 00000000 03:01 3007590    /usr/lib/gconv/ISO8859-1.so
b7fc1000-b7fc3000 rw-p 00001000 03:01 3007590    /usr/lib/gconv/ISO8859-1.so
b7fc3000-b7fc4000 r--p 00000000 03:01 3025782    /usr/lib/locale/en_CA.utf8/LC_NUMERIC
b7fc4000-b7fc5000 r--p 00000000 03:01 3025783    /usr/lib/locale/en_CA.utf8/LC_TIME
b7fc5000-b7fc6000 r--p 00000000 03:01 3025785    /usr/lib/locale/en_CA.utf8/LC_MONETARY
b7fc6000-b7fc7000 r--p 00000000 03:01 3025787    /usr/lib/locale/en_CA.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7fc7000-b7fc8000 r--p 00000000 03:01 3025788    /usr/lib/locale/en_CA.utf8/LC_PAPER
b7fc8000-b7fc9000 r--p 00000000 03:01 3025789    /usr/lib/locale/en_CA.utf8/LC_NAME
b7fc9000-b7fca000 r--p 00000000 03:01 3025790    /usr/lib/locale/en_CA.utf8/LC_ADDRESS
b7fca000-b7fcb000 r--p 00000000 03:01 3025791    /usr/lib/locale/en_CA.utf8/LC_TELEPHONE
b7fcb000-b7fcc000 r--p 00000000 03:01 3025792    /usr/lib/locale/en_CA.utf8/LC_MEASUREMENT
b7fcc000-b7fd3000 r--s 00000000 03:01 2998588    /usr/lib/gconv/gconv-modules.cache
b7fd3000-b7fd4000 r--p 00000000 03:01 3025793    /usr/lib/locale/en_CA.utf8/LC_IDENTIFICATION
b7fd4000-b7fd6000 rw-p b7fd4000 00:00 0
b7fd6000-b7fef000 r-xp 00000000 03:01 65556      /lib/ld-2.4.so
b7fef000-b7ff1000 rw-p 00018000 03:01 65556      /lib/ld-2.4.so
bf852000-bf868000 rw-p bf852000 00:00 0          [stack]
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]
Aborted

I don't understand how two perfectly useable apps (gtkpod and Amarok) can suddenly *not* work for no reason (?). Any tips out there?

> version info:
Amarok 1.4.3
gtkpod 0.99.4

---

