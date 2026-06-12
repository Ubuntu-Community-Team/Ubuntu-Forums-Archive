---
title: "Unable to start JACK in Oneiric x64."
date: 2011-10-07
forum: Multimedia Software
---

### Post by techMOTION on 2011-10-07
I've recently upgraded from Ubuntu 64-bit 11.04 to 11.10 (which might be part of the issue), and after installing jackd and qjackctl, JACK will not start.  Here's the mess of a message I get when I try to start JACK from the terminal, using jackd.

======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x78a96)[0x7f7177489a96]
/lib/x86_64-linux-gnu/libc.so.6(cfree+0x6c)[0x7f717748dd7c]
/usr/lib/libffado.so.2(_ZN18DebugModuleManagerD2Ev+0x86)[0x7f717682a5d6]
/usr/lib/libffado.so.2(+0xb2396)[0x7f7176828396]
/lib64/ld-linux-x86-64.so.2(+0x13bd8)[0x7f71781a7bd8]
/lib64/ld-linux-x86-64.so.2(+0x1469e)[0x7f71781a869e]
/lib64/ld-linux-x86-64.so.2(+0xe996)[0x7f71781a2996]
/lib/x86_64-linux-gnu/libdl.so.2(+0x152f)[0x7f7176b6552f]
/lib/x86_64-linux-gnu/libdl.so.2(dlclose+0x1f)[0x7f7176b6500f]
/usr/lib/x86_64-linux-gnu/libjackserver.so.0(+0x4c333)[0x7f7177c55333]
/usr/lib/x86_64-linux-gnu/libjackserver.so.0(+0x4d39e)[0x7f7177c5639e]
/usr/lib/x86_64-linux-gnu/libjackserver.so.0(jackctl_server_create+0xf3d)[0x7f7177c5a1dd]
jackd[0x40258b]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed)[0x7f717743230d]
jackd[0x402ed1]
======= Memory map: ========
00400000-00406000 r-xp 00000000 08:01 57942310                           /usr/bin/jackd
00605000-00606000 r--p 00005000 08:01 57942310                           /usr/bin/jackd
00606000-00607000 rw-p 00006000 08:01 57942310                           /usr/bin/jackd
0200b000-0202c000 rw-p 00000000 00:00 0                                  [heap]
7f716c000000-7f716c021000 rw-p 00000000 00:00 0 
7f716c021000-7f7170000000 ---p 00000000 00:00 0 
7f7173daf000-7f7173db0000 ---p 00000000 00:00 0 
7f7173db0000-7f71747b1000 rw-p 00000000 00:00 0 
7f71747b1000-7f71747ec000 r-xp 00000000 08:01 34868921                   /lib/x86_64-linux-gnu/libpcre.so.3.12.1
7f71747ec000-7f71749eb000 ---p 0003b000 08:01 34868921                   /lib/x86_64-linux-gnu/libpcre.so.3.12.1
7f71749eb000-7f71749ec000 r--p 0003a000 08:01 34868921                   /lib/x86_64-linux-gnu/libpcre.so.3.12.1
7f71749ec000-7f71749ed000 rw-p 0003b000 08:01 34868921                   /lib/x86_64-linux-gnu/libpcre.so.3.12.1
7f71749ed000-7f71749f4000 r-xp 00000000 08:01 57936809                   /usr/lib/x86_64-linux-gnu/libffi.so.6.0.0
7f71749f4000-7f7174bf3000 ---p 00007000 08:01 57936809                   /usr/lib/x86_64-linux-gnu/libffi.so.6.0.0
7f7174bf3000-7f7174bf4000 r--p 00006000 08:01 57936809                   /usr/lib/x86_64-linux-gnu/libffi.so.6.0.0
7f7174bf4000-7f7174bf5000 rw-p 00007000 08:01 57936809                   /usr/lib/x86_64-linux-gnu/libffi.so.6.0.0
7f7174bf5000-7f7174bf9000 r-xp 00000000 08:01 57934181                   /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0.3000.0
7f7174bf9000-7f7174df8000 ---p 00004000 08:01 57934181                   /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0.3000.0
7f7174df8000-7f7174df9000 r--p 00003000 08:01 57934181                   /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0.3000.0
7f7174df9000-7f7174dfa000 rw-p 00004000 08:01 57934181                   /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0.3000.0
7f7174dfa000-7f7174e11000 r-xp 00000000 08:01 34868942                   /lib/x86_64-linux-gnu/libz.so.1.2.3.4
7f7174e11000-7f7175010000 ---p 00017000 08:01 34868942                   /lib/x86_64-linux-gnu/libz.so.1.2.3.4
7f7175010000-7f7175011000 r--p 00016000 08:01 34868942                   /lib/x86_64-linux-gnu/libz.so.1.2.3.4
7f7175011000-7f7175012000 rw-p 00017000 08:01 34868942                   /lib/x86_64-linux-gnu/libz.so.1.2.3.4
7f7175012000-7f7175106000 r-xp 00000000 08:01 34865243                   /lib/x86_64-linux-gnu/libglib-2.0.so.0.3000.0
7f7175106000-7f7175305000 ---p 000f4000 08:01 34865243                   /lib/x86_64-linux-gnu/libglib-2.0.so.0.3000.0
7f7175305000-7f7175306000 r--p 000f3000 08:01 34865243                   /lib/x86_64-linux-gnu/libglib-2.0.so.0.3000.0
7f7175306000-7f7175307000 rw-p 000f4000 08:01 34865243                   /lib/x86_64-linux-gnu/libglib-2.0.so.0.3000.0
7f7175307000-7f7175308000 rw-p 00000000 00:00 0 
7f7175308000-7f717530b000 r-xp 00000000 08:01 57934183                   /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.3000.0
7f717530b000-7f717550a000 ---p 00003000 08:01 57934183                   /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.3000.0
7f717550a000-7f717550b000 r--p 00002000 08:01 57934183                   /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.3000.0
7f717550b000-7f717550c000 rw-p 00003000 08:01 57934183                   /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.3000.0
7f717550c000-7f717555a000 r-xp 00000000 08:01 57934180                   /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.3000.0
7f717555a000-7f717575a000 ---p 0004e000 08:01 57934180                   /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.3000.0
7f717575a000-7f717575b000 r--p 0004e000 08:01 57934180                   /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.3000.0
7f717575b000-7f717575c000 rw-p 0004f000 08:01 57934180                   /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.3000.0
7f717575c000-7f717575d000 rw-p 00000000 00:00 0 
7f717575d000-7f7175761000 r-xp 00000000 08:01 57937445                   /usr/lib/libsigc-2.0.so.0.0.0
7f7175761000-7f7175960000 ---p 00004000 08:01 57937445                   /usr/lib/libsigc-2.0.so.0.0.0
7f7175960000-7f7175961000 r--p 00003000 08:01 57937445                   /usr/lib/libsigc-2.0.so.0.0.0
7f7175961000-7f7175962000 rw-p 00004000 08:01 57937445                   /usr/lib/libsigc-2.0.so.0.0.0
7f7175962000-7f7175ab3000 r-xp 00000000 08:01 57938682                   /usr/lib/libxml2.so.2.7.8
7f7175ab3000-7f7175cb2000 ---p 00151000 08:01 57938682                   /usr/lib/libxml2.so.2.7.8
7f7175cb2000-7f7175cba000 r--p 00150000 08:01 57938682                   /usr/lib/libxml2.so.2.7.8
7f7175cba000-7f7175cbc000 rw-p 00158000 08:01 57938682                   /usr/lib/libxml2.so.2.7.8
7f7175cbc000-7f7175cbd000 rw-p 00000000 00:00 0 
7f7175cbd000-7f7175d1f000 r-xp 00000000 08:01 57939868                   /usr/lib/libglibmm-2.4.so.1.3.0
7f7175d1f000-7f7175f1f000 ---p 00062000 08:01 57939868                   /usr/lib/libglibmm-2.4.so.1.3.0
7f7175f1f000-7f7175f21000 r--p 00062000 08:01 57939868                   /usr/lib/libglibmm-2.4.so.1.3.0
7f7175f21000-7f7175f23000 rw-p 00064000 08:01 57939868                   /usr/lib/libglibmm-2.4.so.1.3.0
7f7175f23000-7f7175f43000 r-xp 00000000 08:01 57942332                   /usr/lib/libxml++-2.6.so.2.0.7
7f7175f43000-7f7176142000 ---p 00020000 08:01 57942332                   /usr/lib/libxml++-2.6.so.2.0.7
7f7176142000-7f7176144000 r--p 0001f000 08:01 57942332                   /usr/lib/libxml++-2.6.so.2.0.7
7f7176144000-7f7176145000 rw-p 00021000 08:01 57942332                   /usr/lib/libxml++-2.6.so.2.0.7
7f7176145000-7f7176158000 r-xp 00000000 08:01 57942327                   /usr/lib/libconfig++.so.8.0.0
7f7176158000-7f7176358000 ---p 00013000 08:01 57942327                   /usr/lib/libconfig++.so.8.0.0
7f7176358000-7f7176359000 r--p 00013000 08:01 57942327                   /usr/lib/libconfig++.so.8.0.0
7f7176359000-7f717635a000 rw-p 00014000 08:01 57942327                   /usr/lib/libconfig++.so.8.0.0
7f717635a000-7f7176367000 r-xp 00000000 08:01 57940060                   /usr/lib/libraw1394.so.11.0.1
7f7176367000-7f7176567000 ---p 0000d000 08:01 57940060                   /usr/lib/libraw1394.so.11.0.1
7f7176567000-7f7176568000 r--p 0000d000 08:01 57940060                   /usr/lib/libraw1394.so.11.0.1
7f7176568000-7f7176569000 rw-p 0000e000 08:01 57940060                   /usr/lib/libraw1394.so.11.0.1
7f7176569000-7f7176575000 r-xp 00000000 08:01 57937942                   /usr/lib/libiec61883.so.0.1.1
7f7176575000-7f7176774000 ---p 0000c000 08:01 57937942                   /usr/lib/libiec61883.so.0.1.1
7f7176774000-7f7176775000 r--p 0000b000 08:01 57937942                   /usr/lib/libiec61883.so.0.1.1
7f7176775000-7f7176776000 rw-p 0000c000 08:01 57937942                   /usr/lib/libiec61883.so.0.1.1
7f7176776000-7f717693f000 r-xp 00000000 08:01 57942342                   /usr/lib/libffado.so.2.999.0
7f717693f000-7f7176940000 ---p 001c9000 08:01 57942342                   /usr/lib/libffado.so.2.999.0
7f7176940000-7f7176951000 r--p 001c9000 08:01 57942342                   /usr/lib/libffado.so.2.999.0
7f7176951000-7f7176959000 rw-p 001da000 08:01 57942342                   /usr/lib/libffado.so.2.999.0
7f7176959000-7f717695a000 rw-p 00000000 00:00 0 
7f717695a000-7f7176963000 r-xp 00000000 08:01 58068050                   /usr/lib/x86_64-linux-gnu/jack/jack_firewire.so
7f7176963000-7f7176b62000 ---p 00009000 08:01 58068050                   /usr/lib/x86_64-linux-gnu/jack/jack_firewire.so
7f7176b62000-7f7176b63000 r--p 00008000 08:01 58068050                   /usr/lib/x86_64-linux-gnu/jack/jack_firewire.so
7f7176b63000-7f7176b64000 rw-p 00009000 08:01 58068050                   /usr/lib/x86_64-linux-gnu/jack/jack_firewire.so
7f7176b64000-7f7176b66000 r-xp 00000000 08:01 34865415                   /lib/x86_64-linux-gnu/libdl-2.13.so
7f7176b66000-7f7176d66000 ---p 00002000 08:01 34865415                   /lib/x86_64-linux-gnu/libdl-2.13.so
7f7176d66000-7f7176d67000 r--p 00002000 08:01 34865415                   /lib/x86_64-linux-gnu/libdl-2.13.so
7f7176d67000-7f7176d68000 rw-p 00003000 08:01 34865415                   /lib/x86_64-linux-gnu/libdl-2.13.so
7f7176d68000-7f7176d6f000 r-xp 00000000 08:01 34865297                   /lib/x86_64-linux-gnu/librt-2.13.so
7f7176d6f000-7f7176f6e000 ---p 00007000 08:01 34865297                   /lib/x86_64-linux-gnu/librt-2.13.so
7f7176f6e000-7f7176f6f000 r--p 00006000 08:01 34865297                   /lib/x86_64-linux-gnu/librt-2.13.so
7f7176f6f000-7f7176f70000 rw-p 00007000 08:01 34865297                   /lib/x86_64-linux-gnu/librt-2.13.so
7f7176f70000-7f7176f88000 r-xp 00000000 08:01 34865429                   /lib/x86_64-linux-gnu/libpthread-2.13.so
7f7176f88000-7f7177187000 ---p 00018000 08:01 34865429                   /lib/x86_64-linux-gnu/libpthread-2.13.so
7f7177187000-7f7177188000 r--p 00017000 08:01 34865429                   /lib/x86_64-linux-gnu/libpthread-2.13.so
7f7177188000-7f7177189000 rw-p 00018000 08:01 34865429                   /lib/x86_64-linux-gnu/libpthread-2.13.so
7f7177189000-7f717718d000 rw-p 00000000 00:00 0 
7f717718d000-7f7177210000 r-xp 00000000 08:01 34865433                   /lib/x86_64-linux-gnu/libm-2.13.so
7f7177210000-7f717740f000 ---p 00083000 08:01 34865433                   /lib/x86_64-linux-gnu/libm-2.13.so
7f717740f000-7f7177410000 r--p 00082000 08:01 34865433                   /lib/x86_64-linux-gnu/libm-2.13.so
7f7177410000-7f7177411000 rw-p 00083000 08:01 34865433                   /lib/x86_64-linux-gnu/libm-2.13.so
7f7177411000-7f71775a6000 r-xp 00000000 08:01 34865413                   /lib/x86_64-linux-gnu/libc-2.13.so
7f71775a6000-7f71777a5000 ---p 00195000 08:01 34865413                   /lib/x86_64-linux-gnu/libc-2.13.so
7f71777a5000-7f71777a9000 r--p 00194000 08:01 34865413                   /lib/x86_64-linux-gnu/libc-2.13.so
7f71777a9000-7f71777aa000 rw-p 00198000 08:01 34865413                   /lib/x86_64-linux-gnu/libc-2.13.so
7f71777aa000-7f71777b0000 rw-p 00000000 00:00 0 
7f71777b0000-7f71777c5000 r-xp 00000000 08:01 34869204                   /lib/x86_64-linux-gnu/libgcc_s.so.1
7f71777c5000-7f71779c4000 ---p 00015000 08:01 34869204                   /lib/x86_64-linux-gnu/libgcc_s.so.1
7f71779c4000-7f71779c5000 r--p 00014000 08:01 34869204                   /lib/x86_64-linux-gnu/libgcc_s.so.1
7f71779c5000-7f71779c6000 rw-p 00015000 08:01 34869204                   /lib/x86_64-linux-gnu/libgcc_s.so.1
7f71779c6000-7f7177a08000 r-xp 00000000 08:01 34868847                   /lib/x86_64-linux-gnu/libdbus-1.so.3.5.7
7f7177a08000-7f7177c07000 ---p 00042000 08:01 34868847                   /lib/x86_64-linux-gnu/libdbus-1.so.3.5.7
7f7177c07000-7f7177c08000 r--p 00041000 08:01 34868847                   /lib/x86_64-linux-gnu/libdbus-1.so.3.5.7
7f7177c08000-7f7177c09000 rw-p 00042000 08:01 34868847                   /lib/x86_64-linux-gnu/libdbus-1.so.3.5.7
7f7177c09000-7f7177c87000 r-xp 00000000 08:01 57942323                   /usr/lib/x86_64-linux-gnu/libjackserver.so.0.1.0
7f7177c87000-7f7177e87000 ---p 0007e000 08:01 57942323                   /usr/lib/x86_64-linux-gnu/libjackserver.so.0.1.0
7f7177e87000-7f7177e8b000 r--p 0007e000 08:01 57942323                   /usr/lib/x86_64-linux-gnu/libjackserver.so.0.1.0
7f7177e8b000-7f7177e8d000 rw-p 00082000 08:01 57942323                   /usr/lib/x86_64-linux-gnu/libjackserver.so.0.1.0
7f7177e8d000-7f7177f75000 r-xp 00000000 08:01 57934308                   /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.16
7f7177f75000-7f7178175000 ---p 000e8000 08:01 57934308                   /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.16
7f7178175000-7f717817d000 r--p 000e8000 08:01 57934308                   /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.16
7f717817d000-7f717817f000 rw-p 000f0000 08:01 57934308                   /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.16
7f717817f000-7f7178194000 rw-p 00000000 00:00 0 
7f7178194000-7f71781b5000 r-xp 00000000 08:01 34865427                   /lib/x86_64-linux-gnu/ld-2.13.so
7f7178389000-7f7178390000 rw-p 00000000 00:00 0 
7f71783b1000-7f71783b4000 rw-p 00000000 00:00 0 
7f71783b4000-7f71783b5000 r--p 00020000 08:01 34865427                   /lib/x86_64-linux-gnu/ld-2.13.so
7f71783b5000-7f71783b7000 rw-p 00021000 08:01 34865427                   /lib/x86_64-linux-gnu/ld-2.13.so
7fff4bc97000-7fff4bcb8000 rw-p 00000000 00:00 0                          [stack]
7fff4bdff000-7fff4be00000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
Aborted (core dumped)
joshua@albatross:~$ cs
The program 'cs' is currently not installed.  You can install it by typing:
sudo apt-get install csound
joshua@albatross:~$ clear

joshua@albatross:~$ jackd
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2011 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Cannot create thread 1 Operation not permitted
Cleaning up leftover debug module: DeviceManager
*** glibc detected *** jackd: free(): invalid pointer: 0x00007f52bab21b20 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x78a96)[0x7f52bb652a96]
/lib/x86_64-linux-gnu/libc.so.6(cfree+0x6c)[0x7f52bb656d7c]
/usr/lib/libffado.so.2(_ZN18DebugModuleManagerD2Ev+0x86)[0x7f52ba9f35d6]
/usr/lib/libffado.so.2(+0xb2396)[0x7f52ba9f1396]
/lib64/ld-linux-x86-64.so.2(+0x13bd8)[0x7f52bc370bd8]
/lib64/ld-linux-x86-64.so.2(+0x1469e)[0x7f52bc37169e]
/lib64/ld-linux-x86-64.so.2(+0xe996)[0x7f52bc36b996]
/lib/x86_64-linux-gnu/libdl.so.2(+0x152f)[0x7f52bad2e52f]
/lib/x86_64-linux-gnu/libdl.so.2(dlclose+0x1f)[0x7f52bad2e00f]
/usr/lib/x86_64-linux-gnu/libjackserver.so.0(+0x4c333)[0x7f52bbe1e333]
/usr/lib/x86_64-linux-gnu/libjackserver.so.0(+0x4d39e)[0x7f52bbe1f39e]
/usr/lib/x86_64-linux-gnu/libjackserver.so.0(jackctl_server_create+0xf3d)[0x7f52bbe231dd]
jackd[0x40258b]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed)[0x7f52bb5fb30d]
jackd[0x402ed1]
======= Memory map: ========
00400000-00406000 r-xp 00000000 08:01 57942310                           /usr/bin/jackd
00605000-00606000 r--p 00005000 08:01 57942310                           /usr/bin/jackd
00606000-00607000 rw-p 00006000 08:01 57942310                           /usr/bin/jackd
02476000-02497000 rw-p 00000000 00:00 0                                  [heap]
7f52b0000000-7f52b0021000 rw-p 00000000 00:00 0 
7f52b0021000-7f52b4000000 ---p 00000000 00:00 0 
7f52b7f78000-7f52b7f79000 ---p 00000000 00:00 0 
7f52b7f79000-7f52b897a000 rw-p 00000000 00:00 0 
7f52b897a000-7f52b89b5000 r-xp 00000000 08:01 34868921                   /lib/x86_64-linux-gnu/libpcre.so.3.12.1
7f52b89b5000-7f52b8bb4000 ---p 0003b000 08:01 34868921                   /lib/x86_64-linux-gnu/libpcre.so.3.12.1
7f52b8bb4000-7f52b8bb5000 r--p 0003a000 08:01 34868921                   /lib/x86_64-linux-gnu/libpcre.so.3.12.1
7f52b8bb5000-7f52b8bb6000 rw-p 0003b000 08:01 34868921                   /lib/x86_64-linux-gnu/libpcre.so.3.12.1
7f52b8bb6000-7f52b8bbd000 r-xp 00000000 08:01 57936809                   /usr/lib/x86_64-linux-gnu/libffi.so.6.0.0
7f52b8bbd000-7f52b8dbc000 ---p 00007000 08:01 57936809                   /usr/lib/x86_64-linux-gnu/libffi.so.6.0.0
7f52b8dbc000-7f52b8dbd000 r--p 00006000 08:01 57936809                   /usr/lib/x86_64-linux-gnu/libffi.so.6.0.0
7f52b8dbd000-7f52b8dbe000 rw-p 00007000 08:01 57936809                   /usr/lib/x86_64-linux-gnu/libffi.so.6.0.0
7f52b8dbe000-7f52b8dc2000 r-xp 00000000 08:01 57934181                   /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0.3000.0
7f52b8dc2000-7f52b8fc1000 ---p 00004000 08:01 57934181                   /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0.3000.0
7f52b8fc1000-7f52b8fc2000 r--p 00003000 08:01 57934181                   /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0.3000.0
7f52b8fc2000-7f52b8fc3000 rw-p 00004000 08:01 57934181                   /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0.3000.0
7f52b8fc3000-7f52b8fda000 r-xp 00000000 08:01 34868942                   /lib/x86_64-linux-gnu/libz.so.1.2.3.4
7f52b8fda000-7f52b91d9000 ---p 00017000 08:01 34868942                   /lib/x86_64-linux-gnu/libz.so.1.2.3.4
7f52b91d9000-7f52b91da000 r--p 00016000 08:01 34868942                   /lib/x86_64-linux-gnu/libz.so.1.2.3.4
7f52b91da000-7f52b91db000 rw-p 00017000 08:01 34868942                   /lib/x86_64-linux-gnu/libz.so.1.2.3.4
7f52b91db000-7f52b92cf000 r-xp 00000000 08:01 34865243                   /lib/x86_64-linux-gnu/libglib-2.0.so.0.3000.0
7f52b92cf000-7f52b94ce000 ---p 000f4000 08:01 34865243                   /lib/x86_64-linux-gnu/libglib-2.0.so.0.3000.0
7f52b94ce000-7f52b94cf000 r--p 000f3000 08:01 34865243                   /lib/x86_64-linux-gnu/libglib-2.0.so.0.3000.0
7f52b94cf000-7f52b94d0000 rw-p 000f4000 08:01 34865243                   /lib/x86_64-linux-gnu/libglib-2.0.so.0.3000.0
7f52b94d0000-7f52b94d1000 rw-p 00000000 00:00 0 
7f52b94d1000-7f52b94d4000 r-xp 00000000 08:01 57934183                   /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.3000.0
7f52b94d4000-7f52b96d3000 ---p 00003000 08:01 57934183                   /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.3000.0
7f52b96d3000-7f52b96d4000 r--p 00002000 08:01 57934183                   /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.3000.0
7f52b96d4000-7f52b96d5000 rw-p 00003000 08:01 57934183                   /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.3000.0
7f52b96d5000-7f52b9723000 r-xp 00000000 08:01 57934180                   /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.3000.0
7f52b9723000-7f52b9923000 ---p 0004e000 08:01 57934180                   /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.3000.0
7f52b9923000-7f52b9924000 r--p 0004e000 08:01 57934180                   /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.3000.0
7f52b9924000-7f52b9925000 rw-p 0004f000 08:01 57934180                   /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.3000.0
7f52b9925000-7f52b9926000 rw-p 00000000 00:00 0 
7f52b9926000-7f52b992a000 r-xp 00000000 08:01 57937445                   /usr/lib/libsigc-2.0.so.0.0.0
7f52b992a000-7f52b9b29000 ---p 00004000 08:01 57937445                   /usr/lib/libsigc-2.0.so.0.0.0
7f52b9b29000-7f52b9b2a000 r--p 00003000 08:01 57937445                   /usr/lib/libsigc-2.0.so.0.0.0
7f52b9b2a000-7f52b9b2b000 rw-p 00004000 08:01 57937445                   /usr/lib/libsigc-2.0.so.0.0.0
7f52b9b2b000-7f52b9c7c000 r-xp 00000000 08:01 57938682                   /usr/lib/libxml2.so.2.7.8
7f52b9c7c000-7f52b9e7b000 ---p 00151000 08:01 57938682                   /usr/lib/libxml2.so.2.7.8
7f52b9e7b000-7f52b9e83000 r--p 00150000 08:01 57938682                   /usr/lib/libxml2.so.2.7.8
7f52b9e83000-7f52b9e85000 rw-p 00158000 08:01 57938682                   /usr/lib/libxml2.so.2.7.8
7f52b9e85000-7f52b9e86000 rw-p 00000000 00:00 0 
7f52b9e86000-7f52b9ee8000 r-xp 00000000 08:01 57939868                   /usr/lib/libglibmm-2.4.so.1.3.0
7f52b9ee8000-7f52ba0e8000 ---p 00062000 08:01 57939868                   /usr/lib/libglibmm-2.4.so.1.3.0
7f52ba0e8000-7f52ba0ea000 r--p 00062000 08:01 57939868                   /usr/lib/libglibmm-2.4.so.1.3.0
7f52ba0ea000-7f52ba0ec000 rw-p 00064000 08:01 57939868                   /usr/lib/libglibmm-2.4.so.1.3.0
7f52ba0ec000-7f52ba10c000 r-xp 00000000 08:01 57942332                   /usr/lib/libxml++-2.6.so.2.0.7
7f52ba10c000-7f52ba30b000 ---p 00020000 08:01 57942332                   /usr/lib/libxml++-2.6.so.2.0.7
7f52ba30b000-7f52ba30d000 r--p 0001f000 08:01 57942332                   /usr/lib/libxml++-2.6.so.2.0.7
7f52ba30d000-7f52ba30e000 rw-p 00021000 08:01 57942332                   /usr/lib/libxml++-2.6.so.2.0.7
7f52ba30e000-7f52ba321000 r-xp 00000000 08:01 57942327                   /usr/lib/libconfig++.so.8.0.0
7f52ba321000-7f52ba521000 ---p 00013000 08:01 57942327                   /usr/lib/libconfig++.so.8.0.0
7f52ba521000-7f52ba522000 r--p 00013000 08:01 57942327                   /usr/lib/libconfig++.so.8.0.0
7f52ba522000-7f52ba523000 rw-p 00014000 08:01 57942327                   /usr/lib/libconfig++.so.8.0.0
7f52ba523000-7f52ba530000 r-xp 00000000 08:01 57940060                   /usr/lib/libraw1394.so.11.0.1
7f52ba530000-7f52ba730000 ---p 0000d000 08:01 57940060                   /usr/lib/libraw1394.so.11.0.1
7f52ba730000-7f52ba731000 r--p 0000d000 08:01 57940060                   /usr/lib/libraw1394.so.11.0.1
7f52ba731000-7f52ba732000 rw-p 0000e000 08:01 57940060                   /usr/lib/libraw1394.so.11.0.1
7f52ba732000-7f52ba73e000 r-xp 00000000 08:01 57937942                   /usr/lib/libiec61883.so.0.1.1
7f52ba73e000-7f52ba93d000 ---p 0000c000 08:01 57937942                   /usr/lib/libiec61883.so.0.1.1
7f52ba93d000-7f52ba93e000 r--p 0000b000 08:01 57937942                   /usr/lib/libiec61883.so.0.1.1
7f52ba93e000-7f52ba93f000 rw-p 0000c000 08:01 57937942                   /usr/lib/libiec61883.so.0.1.1
7f52ba93f000-7f52bab08000 r-xp 00000000 08:01 57942342                   /usr/lib/libffado.so.2.999.0
7f52bab08000-7f52bab09000 ---p 001c9000 08:01 57942342                   /usr/lib/libffado.so.2.999.0
7f52bab09000-7f52bab1a000 r--p 001c9000 08:01 57942342                   /usr/lib/libffado.so.2.999.0
7f52bab1a000-7f52bab22000 rw-p 001da000 08:01 57942342                   /usr/lib/libffado.so.2.999.0
7f52bab22000-7f52bab23000 rw-p 00000000 00:00 0 
7f52bab23000-7f52bab2c000 r-xp 00000000 08:01 58068050                   /usr/lib/x86_64-linux-gnu/jack/jack_firewire.so
7f52bab2c000-7f52bad2b000 ---p 00009000 08:01 58068050                   /usr/lib/x86_64-linux-gnu/jack/jack_firewire.so
7f52bad2b000-7f52bad2c000 r--p 00008000 08:01 58068050                   /usr/lib/x86_64-linux-gnu/jack/jack_firewire.so
7f52bad2c000-7f52bad2d000 rw-p 00009000 08:01 58068050                   /usr/lib/x86_64-linux-gnu/jack/jack_firewire.so
7f52bad2d000-7f52bad2f000 r-xp 00000000 08:01 34865415                   /lib/x86_64-linux-gnu/libdl-2.13.so
7f52bad2f000-7f52baf2f000 ---p 00002000 08:01 34865415                   /lib/x86_64-linux-gnu/libdl-2.13.so
7f52baf2f000-7f52baf30000 r--p 00002000 08:01 34865415                   /lib/x86_64-linux-gnu/libdl-2.13.so
7f52baf30000-7f52baf31000 rw-p 00003000 08:01 34865415                   /lib/x86_64-linux-gnu/libdl-2.13.so
7f52baf31000-7f52baf38000 r-xp 00000000 08:01 34865297                   /lib/x86_64-linux-gnu/librt-2.13.so
7f52baf38000-7f52bb137000 ---p 00007000 08:01 34865297                   /lib/x86_64-linux-gnu/librt-2.13.so
7f52bb137000-7f52bb138000 r--p 00006000 08:01 34865297                   /lib/x86_64-linux-gnu/librt-2.13.so
7f52bb138000-7f52bb139000 rw-p 00007000 08:01 34865297                   /lib/x86_64-linux-gnu/librt-2.13.so
7f52bb139000-7f52bb151000 r-xp 00000000 08:01 34865429                   /lib/x86_64-linux-gnu/libpthread-2.13.so
7f52bb151000-7f52bb350000 ---p 00018000 08:01 34865429                   /lib/x86_64-linux-gnu/libpthread-2.13.so
7f52bb350000-7f52bb351000 r--p 00017000 08:01 34865429                   /lib/x86_64-linux-gnu/libpthread-2.13.so
7f52bb351000-7f52bb352000 rw-p 00018000 08:01 34865429                   /lib/x86_64-linux-gnu/libpthread-2.13.so
7f52bb352000-7f52bb356000 rw-p 00000000 00:00 0 
7f52bb356000-7f52bb3d9000 r-xp 00000000 08:01 34865433                   /lib/x86_64-linux-gnu/libm-2.13.so
7f52bb3d9000-7f52bb5d8000 ---p 00083000 08:01 34865433                   /lib/x86_64-linux-gnu/libm-2.13.so
7f52bb5d8000-7f52bb5d9000 r--p 00082000 08:01 34865433                   /lib/x86_64-linux-gnu/libm-2.13.so
7f52bb5d9000-7f52bb5da000 rw-p 00083000 08:01 34865433                   /lib/x86_64-linux-gnu/libm-2.13.so
7f52bb5da000-7f52bb76f000 r-xp 00000000 08:01 34865413                   /lib/x86_64-linux-gnu/libc-2.13.so
7f52bb76f000-7f52bb96e000 ---p 00195000 08:01 34865413                   /lib/x86_64-linux-gnu/libc-2.13.so
7f52bb96e000-7f52bb972000 r--p 00194000 08:01 34865413                   /lib/x86_64-linux-gnu/libc-2.13.so
7f52bb972000-7f52bb973000 rw-p 00198000 08:01 34865413                   /lib/x86_64-linux-gnu/libc-2.13.so
7f52bb973000-7f52bb979000 rw-p 00000000 00:00 0 
7f52bb979000-7f52bb98e000 r-xp 00000000 08:01 34869204                   /lib/x86_64-linux-gnu/libgcc_s.so.1
7f52bb98e000-7f52bbb8d000 ---p 00015000 08:01 34869204                   /lib/x86_64-linux-gnu/libgcc_s.so.1
7f52bbb8d000-7f52bbb8e000 r--p 00014000 08:01 34869204                   /lib/x86_64-linux-gnu/libgcc_s.so.1
7f52bbb8e000-7f52bbb8f000 rw-p 00015000 08:01 34869204                   /lib/x86_64-linux-gnu/libgcc_s.so.1
7f52bbb8f000-7f52bbbd1000 r-xp 00000000 08:01 34868847                   /lib/x86_64-linux-gnu/libdbus-1.so.3.5.7
7f52bbbd1000-7f52bbdd0000 ---p 00042000 08:01 34868847                   /lib/x86_64-linux-gnu/libdbus-1.so.3.5.7
7f52bbdd0000-7f52bbdd1000 r--p 00041000 08:01 34868847                   /lib/x86_64-linux-gnu/libdbus-1.so.3.5.7
7f52bbdd1000-7f52bbdd2000 rw-p 00042000 08:01 34868847                   /lib/x86_64-linux-gnu/libdbus-1.so.3.5.7
7f52bbdd2000-7f52bbe50000 r-xp 00000000 08:01 57942323                   /usr/lib/x86_64-linux-gnu/libjackserver.so.0.1.0
7f52bbe50000-7f52bc050000 ---p 0007e000 08:01 57942323                   /usr/lib/x86_64-linux-gnu/libjackserver.so.0.1.0
7f52bc050000-7f52bc054000 r--p 0007e000 08:01 57942323                   /usr/lib/x86_64-linux-gnu/libjackserver.so.0.1.0
7f52bc054000-7f52bc056000 rw-p 00082000 08:01 57942323                   /usr/lib/x86_64-linux-gnu/libjackserver.so.0.1.0
7f52bc056000-7f52bc13e000 r-xp 00000000 08:01 57934308                   /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.16
7f52bc13e000-7f52bc33e000 ---p 000e8000 08:01 57934308                   /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.16
7f52bc33e000-7f52bc346000 r--p 000e8000 08:01 57934308                   /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.16
7f52bc346000-7f52bc348000 rw-p 000f0000 08:01 57934308                   /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.16
7f52bc348000-7f52bc35d000 rw-p 00000000 00:00 0 
7f52bc35d000-7f52bc37e000 r-xp 00000000 08:01 34865427                   /lib/x86_64-linux-gnu/ld-2.13.so
7f52bc552000-7f52bc559000 rw-p 00000000 00:00 0 
7f52bc57a000-7f52bc57d000 rw-p 00000000 00:00 0 
7f52bc57d000-7f52bc57e000 r--p 00020000 08:01 34865427                   /lib/x86_64-linux-gnu/ld-2.13.so
7f52bc57e000-7f52bc580000 rw-p 00021000 08:01 34865427                   /lib/x86_64-linux-gnu/ld-2.13.so
7fffea21b000-7fffea23c000 rw-p 00000000 00:00 0                          [stack]
7fffea31e000-7fffea31f000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
Aborted (core dumped)

So, any ideas?

---

### Post by techMOTION on 2011-10-07
I installed csound, as recommended in the middle of the message.  Now I am given this when I start jackd in the terminal.

jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2011 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Cannot create thread 1 Operation not permitted
Cleaning up leftover debug module: DeviceManager
*** glibc detected *** jackd: free(): invalid pointer: 0x00007f6b3c30ab20 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x78a96)[0x7f6b3ce3ba96]
/lib/x86_64-linux-gnu/libc.so.6(cfree+0x6c)[0x7f6b3ce3fd7c]
/usr/lib/libffado.so.2(_ZN18DebugModuleManagerD2Ev+0x86)[0x7f6b3c1dc5d6]
/usr/lib/libffado.so.2(+0xb2396)[0x7f6b3c1da396]
/lib64/ld-linux-x86-64.so.2(+0x13bd8)[0x7f6b3db59bd8]
/lib64/ld-linux-x86-64.so.2(+0x1469e)[0x7f6b3db5a69e]
/lib64/ld-linux-x86-64.so.2(+0xe996)[0x7f6b3db54996]
/lib/x86_64-linux-gnu/libdl.so.2(+0x152f)[0x7f6b3c51752f]
/lib/x86_64-linux-gnu/libdl.so.2(dlclose+0x1f)[0x7f6b3c51700f]
/usr/lib/x86_64-linux-gnu/libjackserver.so.0(+0x4c333)[0x7f6b3d607333]
/usr/lib/x86_64-linux-gnu/libjackserver.so.0(+0x4d39e)[0x7f6b3d60839e]
/usr/lib/x86_64-linux-gnu/libjackserver.so.0(jackctl_server_create+0xf3d)[0x7f6b3d60c1dd]
jackd[0x40258b]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed)[0x7f6b3cde430d]
jackd[0x402ed1]
======= Memory map: ========
00400000-00406000 r-xp 00000000 08:01 57942310                           /usr/bin/jackd
00605000-00606000 r--p 00005000 08:01 57942310                           /usr/bin/jackd
00606000-00607000 rw-p 00006000 08:01 57942310                           /usr/bin/jackd
01224000-01245000 rw-p 00000000 00:00 0                                  [heap]
7f6b34000000-7f6b34021000 rw-p 00000000 00:00 0 
7f6b34021000-7f6b38000000 ---p 00000000 00:00 0 
7f6b39761000-7f6b39762000 ---p 00000000 00:00 0 
7f6b39762000-7f6b3a163000 rw-p 00000000 00:00 0 
7f6b3a163000-7f6b3a19e000 r-xp 00000000 08:01 34868921                   /lib/x86_64-linux-gnu/libpcre.so.3.12.1
7f6b3a19e000-7f6b3a39d000 ---p 0003b000 08:01 34868921                   /lib/x86_64-linux-gnu/libpcre.so.3.12.1
7f6b3a39d000-7f6b3a39e000 r--p 0003a000 08:01 34868921                   /lib/x86_64-linux-gnu/libpcre.so.3.12.1
7f6b3a39e000-7f6b3a39f000 rw-p 0003b000 08:01 34868921                   /lib/x86_64-linux-gnu/libpcre.so.3.12.1
7f6b3a39f000-7f6b3a3a6000 r-xp 00000000 08:01 57936809                   /usr/lib/x86_64-linux-gnu/libffi.so.6.0.0
7f6b3a3a6000-7f6b3a5a5000 ---p 00007000 08:01 57936809                   /usr/lib/x86_64-linux-gnu/libffi.so.6.0.0
7f6b3a5a5000-7f6b3a5a6000 r--p 00006000 08:01 57936809                   /usr/lib/x86_64-linux-gnu/libffi.so.6.0.0
7f6b3a5a6000-7f6b3a5a7000 rw-p 00007000 08:01 57936809                   /usr/lib/x86_64-linux-gnu/libffi.so.6.0.0
7f6b3a5a7000-7f6b3a5ab000 r-xp 00000000 08:01 57934181                   /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0.3000.0
7f6b3a5ab000-7f6b3a7aa000 ---p 00004000 08:01 57934181                   /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0.3000.0
7f6b3a7aa000-7f6b3a7ab000 r--p 00003000 08:01 57934181                   /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0.3000.0
7f6b3a7ab000-7f6b3a7ac000 rw-p 00004000 08:01 57934181                   /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0.3000.0
7f6b3a7ac000-7f6b3a7c3000 r-xp 00000000 08:01 34868942                   /lib/x86_64-linux-gnu/libz.so.1.2.3.4
7f6b3a7c3000-7f6b3a9c2000 ---p 00017000 08:01 34868942                   /lib/x86_64-linux-gnu/libz.so.1.2.3.4
7f6b3a9c2000-7f6b3a9c3000 r--p 00016000 08:01 34868942                   /lib/x86_64-linux-gnu/libz.so.1.2.3.4
7f6b3a9c3000-7f6b3a9c4000 rw-p 00017000 08:01 34868942                   /lib/x86_64-linux-gnu/libz.so.1.2.3.4
7f6b3a9c4000-7f6b3aab8000 r-xp 00000000 08:01 34865243                   /lib/x86_64-linux-gnu/libglib-2.0.so.0.3000.0
7f6b3aab8000-7f6b3acb7000 ---p 000f4000 08:01 34865243                   /lib/x86_64-linux-gnu/libglib-2.0.so.0.3000.0
7f6b3acb7000-7f6b3acb8000 r--p 000f3000 08:01 34865243                   /lib/x86_64-linux-gnu/libglib-2.0.so.0.3000.0
7f6b3acb8000-7f6b3acb9000 rw-p 000f4000 08:01 34865243                   /lib/x86_64-linux-gnu/libglib-2.0.so.0.3000.0
7f6b3acb9000-7f6b3acba000 rw-p 00000000 00:00 0 
7f6b3acba000-7f6b3acbd000 r-xp 00000000 08:01 57934183                   /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.3000.0
7f6b3acbd000-7f6b3aebc000 ---p 00003000 08:01 57934183                   /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.3000.0
7f6b3aebc000-7f6b3aebd000 r--p 00002000 08:01 57934183                   /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.3000.0
7f6b3aebd000-7f6b3aebe000 rw-p 00003000 08:01 57934183                   /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.3000.0
7f6b3aebe000-7f6b3af0c000 r-xp 00000000 08:01 57934180                   /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.3000.0
7f6b3af0c000-7f6b3b10c000 ---p 0004e000 08:01 57934180                   /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.3000.0
7f6b3b10c000-7f6b3b10d000 r--p 0004e000 08:01 57934180                   /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.3000.0
7f6b3b10d000-7f6b3b10e000 rw-p 0004f000 08:01 57934180                   /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.3000.0
7f6b3b10e000-7f6b3b10f000 rw-p 00000000 00:00 0 
7f6b3b10f000-7f6b3b113000 r-xp 00000000 08:01 57937445                   /usr/lib/libsigc-2.0.so.0.0.0
7f6b3b113000-7f6b3b312000 ---p 00004000 08:01 57937445                   /usr/lib/libsigc-2.0.so.0.0.0
7f6b3b312000-7f6b3b313000 r--p 00003000 08:01 57937445                   /usr/lib/libsigc-2.0.so.0.0.0
7f6b3b313000-7f6b3b314000 rw-p 00004000 08:01 57937445                   /usr/lib/libsigc-2.0.so.0.0.0
7f6b3b314000-7f6b3b465000 r-xp 00000000 08:01 57938682                   /usr/lib/libxml2.so.2.7.8
7f6b3b465000-7f6b3b664000 ---p 00151000 08:01 57938682                   /usr/lib/libxml2.so.2.7.8
7f6b3b664000-7f6b3b66c000 r--p 00150000 08:01 57938682                   /usr/lib/libxml2.so.2.7.8
7f6b3b66c000-7f6b3b66e000 rw-p 00158000 08:01 57938682                   /usr/lib/libxml2.so.2.7.8
7f6b3b66e000-7f6b3b66f000 rw-p 00000000 00:00 0 
7f6b3b66f000-7f6b3b6d1000 r-xp 00000000 08:01 57939868                   /usr/lib/libglibmm-2.4.so.1.3.0
7f6b3b6d1000-7f6b3b8d1000 ---p 00062000 08:01 57939868                   /usr/lib/libglibmm-2.4.so.1.3.0
7f6b3b8d1000-7f6b3b8d3000 r--p 00062000 08:01 57939868                   /usr/lib/libglibmm-2.4.so.1.3.0
7f6b3b8d3000-7f6b3b8d5000 rw-p 00064000 08:01 57939868                   /usr/lib/libglibmm-2.4.so.1.3.0
7f6b3b8d5000-7f6b3b8f5000 r-xp 00000000 08:01 57942332                   /usr/lib/libxml++-2.6.so.2.0.7
7f6b3b8f5000-7f6b3baf4000 ---p 00020000 08:01 57942332                   /usr/lib/libxml++-2.6.so.2.0.7
7f6b3baf4000-7f6b3baf6000 r--p 0001f000 08:01 57942332                   /usr/lib/libxml++-2.6.so.2.0.7
7f6b3baf6000-7f6b3baf7000 rw-p 00021000 08:01 57942332                   /usr/lib/libxml++-2.6.so.2.0.7
7f6b3baf7000-7f6b3bb0a000 r-xp 00000000 08:01 57942327                   /usr/lib/libconfig++.so.8.0.0Aborted (core dumped)

Any idea as to what should be done?  Thanks,

---

### Post by pablomme on 2011-10-08
This just hit me too. Everything worked fine in oneiric a couple of weeks ago, so this is recent breakage.

The crash seems to be from libffado, which is a firewire library. I just did
```

sudo apt-get --purge remove jackd2-firewire

```
and then JACK starts normally. Should work for you too, unless you are using a firewire device, in which case you're stuck with the crash. File a bug report if so.

---

### Post by techMOTION on 2011-10-08
Great detective work!

It seems as though JACK worked again, after I removed its Firewire module you listed.

---

