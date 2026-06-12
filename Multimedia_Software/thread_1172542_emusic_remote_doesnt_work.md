---
title: "emusic remote doesnt work"
date: 2009-05-28
forum: Multimedia Software
---

### Post by max_power on 2009-05-28
Has anyone had any luck getting emusic-remote to work? Im using 9.04 here is my log

```
*** buffer overflow detected ***: /usr/lib/xulrunner/xulrunner-bin terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb710ada8]
/lib/tls/i686/cmov/libc.so.6[0xb7108eb0]
/lib/tls/i686/cmov/libc.so.6[0xb7109618]
/usr/lib/libxul.so.0d(XRE_GetFileFromPath+0x54)[0xb748fc54]
/usr/lib/xulrunner/xulrunner-bin[0x804925b]
/usr/lib/xulrunner/xulrunner-bin[0x8049b80]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7023775]
/usr/lib/xulrunner/xulrunner-bin[0x8049091]
======= Memory map: ========
08048000-0804c000 r-xp 00000000 08:01 1868659    /usr/lib/xulrunner/xulrunner-bin
0804c000-0804d000 r-xp 00003000 08:01 1868659    /usr/lib/xulrunner/xulrunner-bin
0804d000-0804e000 rwxp 00004000 08:01 1868659    /usr/lib/xulrunner/xulrunner-bin
08c01000-08c22000 rwxp 08c01000 00:00 0          [heap]
b63ee000-b63f1000 rwxp b63ee000 00:00 0 
b63f1000-b63f4000 r-xp 00000000 08:01 1007764    /lib/libuuid.so.1.2
b63f4000-b63f5000 r-xp 00002000 08:01 1007764    /lib/libuuid.so.1.2
b63f5000-b63f6000 rwxp 00003000 08:01 1007764    /lib/libuuid.so.1.2
b63f6000-b640b000 r-xp 00000000 08:01 1517063    /usr/lib/libICE.so.6.3.0
b640b000-b640c000 rwxp 00014000 08:01 1517063    /usr/lib/libICE.so.6.3.0
b640c000-b640e000 rwxp b640c000 00:00 0 
b640e000-b6426000 r-xp 00000000 08:01 1007740    /lib/libselinux.so.1
b6426000-b6427000 r-xp 00017000 08:01 1007740    /lib/libselinux.so.1
b6427000-b6428000 rwxp 00018000 08:01 1007740    /lib/libselinux.so.1
b6428000-b6429000 rwxp b6428000 00:00 0 
b6429000-b642d000 r-xp 00000000 08:01 1517113    /usr/lib/libXdmcp.so.6.0.0
b642d000-b642e000 rwxp 00003000 08:01 1517113    /usr/lib/libXdmcp.so.6.0.0
b642e000-b6430000 r-xp 00000000 08:01 1517102    /usr/lib/libXau.so.6.0.0
b6430000-b6431000 r-xp 00001000 08:01 1517102    /usr/lib/libXau.so.6.0.0
b6431000-b6432000 rwxp 00002000 08:01 1517102    /usr/lib/libXau.so.6.0.0
b6432000-b6439000 r-xp 00000000 08:01 1024949    /lib/tls/i686/cmov/librt-2.9.so
b6439000-b643a000 r-xp 00006000 08:01 1024949    /lib/tls/i686/cmov/librt-2.9.so
b643a000-b643b000 rwxp 00007000 08:01 1024949    /lib/tls/i686/cmov/librt-2.9.so
b643b000-b6442000 r-xp 00000000 08:01 1517094    /usr/lib/libSM.so.6.0.0
b6442000-b6443000 r-xp 00006000 08:01 1517094    /usr/lib/libSM.so.6.0.0
b6443000-b6444000 rwxp 00007000 08:01 1517094    /usr/lib/libSM.so.6.0.0
b6444000-b6474000 r-xp 00000000 08:01 1007728    /lib/libpcre.so.3.12.1
b6474000-b6475000 r-xp 0002f000 08:01 1007728    /lib/libpcre.so.3.12.1
b6475000-b6476000 rwxp 00030000 08:01 1007728    /lib/libpcre.so.3.12.1
b6476000-b6477000 rwxp b6476000 00:00 0 
b6477000-b649b000 r-xp 00000000 08:01 1517366    /usr/lib/libexpat.so.1.5.2
b649b000-b649d000 r-xp 00023000 08:01 1517366    /usr/lib/libexpat.so.1.5.2
b649d000-b649e000 rwxp 00025000 08:01 1517366    /usr/lib/libexpat.so.1.5.2
b649e000-b64a4000 r-xp 00000000 08:01 1518077    /usr/lib/libxcb-render.so.0.0.0
b64a4000-b64a5000 r-xp 00005000 08:01 1518077    /usr/lib/libxcb-render.so.0.0.0
b64a5000-b64a6000 rwxp 00006000 08:01 1518077    /usr/lib/libxcb-render.so.0.0.0
b64a6000-b64a9000 r-xp 00000000 08:01 1518075    /usr/lib/libxcb-render-util.so.0.0.0
b64a9000-b64aa000 r-xp 00002000 08:01 1518075    /usr/lib/libxcb-render-util.so.0.0.0
b64aa000-b64ab000 rwxp 00003000 08:01 1518075    /usr/lib/libxcb-render-util.so.0.0.0
b64ab000-b64be000 r-xp 00000000 08:01 1517304    /usr/lib/libdirect-1.0.so.0.1.0
b64be000-b64bf000 r-xp 00012000 08:01 1517304    /usr/lib/libdirect-1.0.so.0.1.0
b64bf000-b64c0000 rwxp 00013000 08:01 1517304    /usr/lib/libdirect-1.0.so.0.1.0
b64c0000-b64c7000 r-xp 00000000 08:01 1517388    /usr/lib/libfusion-1.0.so.0.1.0
b64c7000-b64c8000 r-xp 00006000 08:01 1517388    /usr/lib/libfusion-1.0.so.0.1.0
b64c8000-b64c9000 rwxp 00007000 08:01 1517388    /usr/lib/libfusion-1.0.so.0.1.0
b64c9000-b652d000 r-xp 00000000 08:01 1517306    /usr/lib/libdirectfb-1.0.so.0.1.0
b652d000-b652e000 r-xp 00063000 08:01 1517306    /usr/lib/libdirectfb-1.0.so.0.1.0
b652e000-b652f000 rwxp 00064000 08:01 1517306    /usr/lib/libdirectfb-1.0.so.0.1.0
b652f000-b6530000 rwxp b652f000 00:00 0 
b6530000-b6570000 r-xp 00000000 08:01 1517860    /usr/lib/libpixman-1.so.0.13.2
b6570000-b6572000 r-xp 0003f000 08:01 1517860    /usr/lib/libpixman-1.so.0.13.2
b6572000-b6573000 rwxp 00041000 08:01 1517860    /usr/lib/libpixman-1.so.0.13.2
b6573000-b6576000 r-xp 00000000 08:01 1516933    /usr/lib/libgmodule-2.0.so.0.2000.1
b6576000-b6577000 r-xp 00002000 08:01 1516933    /usr/lib/libgmodule-2.0.so.0.2000.1
b6577000-b6578000 rwxp 00003000 08:01 1516933    /usr/lib/libgmodule-2.0.so.0.2000.1
b6578000-b65e3000 r-xp 00000000 08:01 1515856    /usr/lib/libgio-2.0.so.0.2000.1
b65e3000-b65e4000 ---p 0006b000 08:01 1515856    /usr/lib/libgio-2.0.so.0.2000.1
b65e4000-b65e5000 r-xp 0006b000 08:01 1515856    /usr/lib/libgio-2.0.so.0.2000.1
b65e5000-b65e6000 rwxp 0006c000 08:01 1515856    /usr/lib/libgio-2.0.so.0.2000.1
b65e6000-b65ea000 r-xp 00000000 08:01 1517117    /usr/lib/libXfixes.so.3.1.0
b65ea000-b65eb000 rwxp 00003000 08:01 1517117    /usr/lib/libXfixes.so.3.1.0
b65eb000-b65ed000 r-xp 00000000 08:01 1517111    /usr/lib/libXdamage.so.1.1.0
b65ed000-b65ee000 rwxp 00001000 08:01 1517111    /usr/lib/libXdamage.so.1.1.0
b65ee000-b65ef000 rwxp b65ee000 00:00 0 
b65ef000-b65f1000 r-xp 00000000 08:01 1517107    /usr/lib/libXcomposite.so.1.0.0
b65f1000-b65f2000 r-xp 00001000 08:01 1517107    /usr/lib/libXcomposite.so.1.0.0
b65f2000-b65f3000 rwxp 00002000 08:01 1517107    /usr/lib/libXcomposite.so.1.0.0
b65f3000-b65fd000 r-xp 00000000 08:01 1516937    /usr/lib/libpangocairo-1.0.so.0.2400.1
b65fd000-b65fe000 r-xp 00009000 08:01 1516937    /usr/lib/libpangocairo-1.0.so.0.2400.1
b65fe000-b65ff000 rwxp 0000a000 08:01 1516937    /usr/lib/libpangocairo-1.0.so.0.2400.1
b65ff000-b6607000 r-xp 00000000 08:01 1517109    /usr/lib/libXcursor.so.1.0.2
b6607000-b6608000 rwxp 00007000 08:01 1517109    /usr/lib/libXcursor.so.1.0.2
b6608000-b660e000 r-xp 00000000 08:01 1517029    /usr/lib/libXrandr.so.2.2.0
b660e000-b660f000 r-xp 00006000 08:01 1517029    /usr/lib/libXrandr.so.2.2.0
b660f000-b6610000 rwxp 00007000 08:01 1517029    /usr/lib/libXrandr.so.2.2.0
b6610000-b6618000 r-xp 00000000 08:01 1517123    /usr/lib/libXi.so.6.0.0
b6618000-b6619000 r-xp 00007000 08:01 1517123    /usr/lib/libXi.so.6.0.0
b6619000-b661a000 rwxp 00008000 08:01 1517123    /usr/lib/libXi.so.6.0.0
b661a000-b661b000 rwxp b661a000 00:00 0 
b661b000-b6633000 r-xp 00000000 08:01 1518079    /usr/lib/libxcb.so.1.1.0
b6633000-b6634000 r-xp 00017000 08:01 1518079    /usr/lib/libxcb.so.1.1.0
b6634000-b6635000 rwxp 00018000 08:01 1518079    /usr/lib/libxcb.so.1.1.0
b6635000-b6643000 r-xp 00000000 08:01 1515765    /usr/lib/libXext.so.6.4.0
b6643000-b6644000 r-xp 0000d000 08:01 1515765    /usr/lib/libXext.so.6.4.0
b6644000-b6645000 rwxp 0000e000 08:01 1515765    /usr/lib/libXext.so.6.4.0
b6645000-b6652000 r-xp 00000000 08:01 1009130    /lib/libgcc_s.so.1
b6652000-b6653000 r-xp 0000c000 08:01 1009130    /lib/libgcc_s.so.1
b6653000-b6654000 rwxp 0000d000 08:01 1009130    /lib/libgcc_s.so.1
b6654000-b6678000 r-xp 00000000 08:01 1024927    /lib/tls/i686/cmov/libm-2.9.so
b6678000-b6679000 r-xp 00023000 08:01 1024927    /lib/tls/i686/cmov/libm-2.9.so
b6679000-b667a000 rwxp 00024000 08:01 1024927    /lib/tls/i686/cmov/libm-2.9.so
b667a000-b6682000 r-xp 00000000 08:01 1517137    /usr/lib/libXrender.so.1.3.0
b6682000-b6683000 r-xp 00007000 08:01 1517137    /usr/lib/libXrender.so.1.3.0
b6683000-b6684000 rwxp 00008000 08:01 1517137    /usr/lib/libXrender.so.1.3.0
b6684000-b6685000 rwxp b6684000 00:00 0 
b6685000-b6689000 r-xp 00000000 08:01 1516935    /usr/lib/libgthread-2.0.so.0.2000.1
b6689000-b668a000 r-xp 00003000 08:01 1516935    /usr/lib/libgthread-2.0.so.0.2000.1
b668a000-b668b000 rwxp 00004000 08:01 1516935    /usr/lib/libgthread-2.0.so.0.2000.1
b668b000-b66da000 r-xp 00000000 08:01 1515854    /usr/lib/libXt.so.6.0.0
b66da000-b66db000 r-xp 0004f000 08:01 1515854    /usr/lib/libXt.so.6.0.0
b66db000-b66de000 rwxp 00050000 08:01 1515854    /usr/lib/libXt.so.6.0.0
b66de000-b6794000 r-xp 00000000 08:01 1516932    /usr/lib/libglib-2.0.so.0.2000.1
b6794000-b6795000 r-xp 000b5000 08:01 1516932    /usr/lib/libglib-2.0.so.0.2000.1
b6795000-b6796000 rwxp 000b6000 08:01 1516932    /usr/lib/libglib-2.0.so.0.2000.1
b6796000-b67d2000 r-xp 00000000 08:01 1516934    /usr/lib/libgobject-2.0.so.0.2000.1
b67d2000-b67d3000 r-xp 0003b000 08:01 1516934    /usr/lib/libgobject-2.0.so.0.2000.1
b67d3000-b67d4000 rwxp 0003c000 08:01 1516934    /usr/lib/libgobject-2.0.so.0.2000.1
b67d4000-b67ff000 r-xp 00000000 08:01 1516958    /usr/lib/libfontconfig.so.1.3.0
b67fAborted

```

---

