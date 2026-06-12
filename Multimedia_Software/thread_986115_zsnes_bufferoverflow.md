---
title: "zsnes bufferoverflow"
date: 2008-11-18
forum: Multimedia Software
---

### Post by anxean on 2008-11-18
i loved previous ubuntu but this one intrepid is quite unreliable it seems anyone have an idea?

dro@dro:~$ zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
*** buffer overflow detected ***: zsnes terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7c73558]
/lib/tls/i686/cmov/libc.so.6[0xb7c71680]
zsnes[0x8056c1b]
======= Memory map: ========
08048000-08303000 r-xp 00000000 fe:01 14827624   /usr/bin/zsnes
08303000-08304000 r--p 002ba000 fe:01 14827624   /usr/bin/zsnes
08304000-08343000 rw-p 002bb000 fe:01 14827624   /usr/bin/zsnes
08343000-088f7000 rw-p 08343000 00:00 0 
0a7d0000-0a819000 rw-p 0a7d0000 00:00 0          [heap]
b6c4a000-b7779000 rw-p b6c4a000 00:00 0 
b7779000-b779b000 r-xp 00000000 fe:01 9310062    /usr/lib/libaudiofile.so.0.0.2
b779b000-b779e000 rw-p 00021000 fe:01 9310062    /usr/lib/libaudiofile.so.0.0.2
b779e000-b77a7000 r-xp 00000000 fe:01 9310066    /usr/lib/libesd.so.0.2.39
b77a7000-b77a8000 r--p 00008000 fe:01 9310066    /usr/lib/libesd.so.0.2.39
b77a8000-b77a9000 rw-p 00009000 fe:01 9310066    /usr/lib/libesd.so.0.2.39
b77a9000-b77f6000 r-xp 00000000 fe:01 9309644    /usr/lib/libXt.so.6.0.0
b77f6000-b77fa000 rw-p 0004c000 fe:01 9309644    /usr/lib/libXt.so.6.0.0
b77fa000-b7810000 r-xp 00000000 fe:01 14852128   /usr/lib/libaudio.so.2.4
b7810000-b7811000 r--p 00015000 fe:01 14852128   /usr/lib/libaudio.so.2.4
b7811000-b7812000 rw-p 00016000 fe:01 14852128   /usr/lib/libaudio.so.2.4
b781c000-b781e000 r-xp 00000000 fe:01 9552119    /usr/lib/ao/plugins-2/liboss.so
b781e000-b7820000 rw-p 00001000 fe:01 9552119    /usr/lib/ao/plugins-2/liboss.so
b7820000-b7823000 r-xp 00000000 fe:01 12574961   /lib/libcap.so.1.10
b7823000-b7824000 rw-p 00002000 fe:01 12574961   /lib/libcap.so.1.10
b7824000-b7839000 r-xp 00000000 fe:01 9309640    /usr/lib/libICE.so.6.3.0
b7839000-b783a000 rw-p 00014000 fe:01 9309640    /usr/lib/libICE.so.6.3.0
b783a000-b783c000 rw-p b783a000 00:00 0 
b783c000-b788a000 r-xp 00000000 fe:01 9310619    /usr/lib/libpulse.so.0.4.1
b788a000-b788b000 r--p 0004d000 fe:01 9310619    /usr/lib/libpulse.so.0.4.1
b788b000-b788c000 rw-p 0004e000 fe:01 9310619    /usr/lib/libpulse.so.0.4.1
b788c000-b7898000 r-xp 00000000 fe:01 9310620    /usr/lib/libpulse-simple.so.0.0.1
b7898000-b7899000 r--p 0000b000 fe:01 9310620    /usr/lib/libpulse-simple.so.0.0.1
b7899000-b789a000 rw-p 0000c000 fe:01 9310620    /usr/lib/libpulse-simple.so.0.0.1
b789d000-b789e000 r-xp 00000000 fe:01 9552117    /usr/lib/ao/plugins-2/libesd.so
b789e000-b78a0000 rw-p 00000000 fe:01 9552117    /usr/lib/ao/plugins-2/libesd.so
b78a0000-b78a1000 r-xp 00000000 fe:01 9552118    /usr/lib/ao/plugins-2/libnas.so
b78a1000-b78a3000 rw-p 00000000 fe:01 9552118    /usr/lib/ao/plugins-2/libnas.so
b78a3000-b78a6000 r-xp 00000000 fe:01 9552115    /usr/lib/ao/plugins-2/libalsa09.so
b78a6000-b78a8000 rw-p 00002000 fe:01 9552115    /usr/lib/ao/plugins-2/libalsa09.so
b78a8000-b78b2000 r-xp 00000000 fe:01 12574880   /lib/tls/i686/cmov/libnss_files-2.8.90.so
b78b2000-b78b3000 r--p 00009000 fe:01 12574880   /lib/tls/i686/cmov/libnss_files-2.8.90.so
b78b3000-b78b4000 rw-p 0000a000 fe:01 12574880   /lib/tls/i686/cmov/libnss_files-2.8.90.so
b78b4000-b78bd000 r-xp 00000000 fe:01 12574883   /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b78bd000-b78be000 r--p 00008000 fe:01 12574883   /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b78be000-b78bf000 rw-p 00009000 fe:01 12574883   /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b78bf000-b78d4000 r-xp 00000000 fe:01 12574877   /lib/tls/i686/cmov/libnsl-2.8.90.so
b78d4000-b78d5000 r--p 00014000 fe:01 12574877   /lib/tls/i686/cmov/libnsl-2.8.90.so
b78d5000-b78d6000 rw-p 00015000 fe:01 12574877   /lib/tls/i686/cmov/libnsl-2.8.90.so
b78d6000-b78d8000 rw-p b78d6000 00:00 0 
b78d8000-b78df000 r-xp 00000000 fe:01 12574878   /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b78df000-b78e0000 r--p 00006000 fe:01 12574878   /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b78e0000-b78e1000 rw-p 00007000 fe:01 12574878   /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b78e1000-b78e3000 rw-p b78e1000 00:00 0 
b78e3000-b78e7000 r-xp 00000000 fe:01 9309622    /usr/lib/libXdmcp.so.6.0.0
b78e7000-b78e8000 rw-p 00003000 fe:01 9309622    /usr/lib/libXdmcp.so.6.0.0
b78e8000-b78ff000 r-xp 00000000 fe:01 9309624    /usr/lib/libxcb.so.1.0.0
b78ff000-b7900000 r--p 00016000 fe:01 9309624    /usr/lib/libxcb.so.1.0.0
b7900000-b7901000 rw-p 00017000 fe:01 9309624    /usr/lib/libxcb.so.1.0.0
b7901000-b7902000 r-xp 00000000 fe:01 9309626    /usr/lib/libxcb-xlib.so.0.0.0
b7902000-b7903000 r--p 00000000 fe:01 9309626    /usr/lib/libxcb-xlib.so.0.0.0
b7903000-b7904000 rw-p 00001000 fe:01 9309626    /usr/lib/libxcb-xlib.so.0.0.0
b7904000-b7905000 rw-p b7904000 00:00 0 
b7905000-b7907000 r-xp 00000000 fe:01 9309620    /usr/lib/libXau.so.6.0.0
b7907000-b7908000 rw-p 00001000 fe:01 9309620    /usr/lib/libXau.so.6.0.0
b7908000-b79f3000 r-xp 00000000 fe:01 9309628    /usr/lib/libX11.so.6.2.0
b79f3000-b79f4000 r--p 000ea000 fe:01 9309628    /usr/lib/libX11.so.6.2.0
b79f4000-b79f6000 rw-p 000eb000 fe:01 9309628    /usr/lib/libX11.so.6.2.0
b79f6000-b79f7000 rw-p b79f6000 00:00 0 
b79f7000-b79fe000 r-xp 00000000 fe:01 12574889   /lib/tls/i686/cmov/librt-2.8.90.so
b79fe000-b79ff000 r--p 00007000 fe:01 12574889   /lib/tls/i686/cmov/librt-2.8.90.so
b79ff000-b7a00000 rw-p 00008000 fe:01 12574889   /lib/tls/i686/cmov/librt-2.8.90.so
b7a00000-b7a0d000 r-xp 00000000 fe:01 9309634    /usr/lib/libXext.so.6.4.0
b7a0d000-b7a0f000 rw-p 0000c000 fe:01 9309634    /usr/lib/libXext.so.6.4.0
b7a0f000-b7a22000 r-xp 00000000 fe:01 9312189    /usr/lib/libdirect-1.0.so.0.1.0
b7a22000-b7a23000 r--p 00012000 fe:01 9312189    /usr/lib/libdirect-1.0.so.0.1.0
b7a23000-b7a24000 rw-p 00013000 fe:01 9312189    /usr/lib/libdirect-1.0.so.0.1.0
b7a24000-b7a2b000 r-xp 00000000 fe:01 9312191    /usr/lib/libfusion-1.0.so.0.1.0
b7a2b000-b7a2c000 r--p 00006000 fe:01 9312191    /usr/lib/libfusion-1.0.so.0.1.0
b7a2c000-b7a2d000 rw-p 00007000 fe:01 9312191    /usr/lib/libfusion-1.0.so.0.1.0
b7a2d000-b7a2e000 rw-p b7a2d000 00:00 0 
b7a2e000-b7a92000 r-xp 00000000 fe:01 9312190    /usr/lib/libdirectfb-1.0.so.0.1.0
b7a92000-b7a93000 r--p 00063000 fe:01 9312190    /usr/lib/libdirectfb-1.0.so.0.1.0
b7a93000-b7a94000 rw-p 00064000 fe:01 9312190    /usr/lib/libdirectfb-1.0.so.0.1.0
b7a94000-b7a96000 r-xp 00000000 fe:01 12574873   /lib/tls/i686/cmov/libdl-2.8.90.so
b7a96000-b7a97000 r--p 00001000 fe:01 12574873   /lib/tls/i686/cmov/libdl-2.8.90.so
b7a97000-b7a98000 rw-p 00002000 fe:01 12574873   /lib/tls/i686/cmov/libdl-2.8.90.so
b7a98000-b7b5b000 r-xp 00000000 fe:01 9310064    /usr/lib/libasound.so.2.0.0
b7b5b000-b7b5d000 r--p 000c2000 fe:01 9310064    /usr/lib/libasound.so.2.0.0
b7b5d000-b7b60000 rw-p 000c4000 fe:01 9310064    /usr/lib/libasound.so.2.0.0
b7b60000-b7b75000 r-xp 00000000 fe:01 12574886   /lib/tls/i686/cmov/libpthread-2.8.90.so
b7b75000-b7b76000 r--p 00014000 fe:01 12574886   /lib/tls/i686/cmov/libpthread-2.8.90.so
b7b76000-b7b77000 rw-p 00015000 fe:01 12574886   /lib/tls/i686/cmov/libpthread-2.8.90.so
b7b77000-b7b79000 rw-p b7b77000 00:00 0 
b7b79000-b7cd1000 r-xp 00000000 fe:01 12574868   /lib/tls/i686/cmov/libc-2.8.90.so
b7cd1000-b7cd3000 r--p 00158000 fe:01 12574868   /lib/tls/i686/cmov/libc-2.8.90.so
b7cd3000-b7cd4000 rw-p 0015a000 fe:01 12574868   /lib/tls/i686/cmov/libc-2.8.90.so
b7cd4000-b7cd8000 rw-p b7cd4000 00:00 0 
b7cd8000-b7ce5000 r-xp 00000000 fe:01 12574735   /lib/libgcc_s.so.1
b7ce5000-b7ce6000 r--p 0000c0Aborted

---

