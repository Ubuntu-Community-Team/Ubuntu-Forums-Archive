---
title: "please help me install monkey's audio"
date: 2008-08-28
forum: Multimedia Software
---

### Post by logos34 on 2008-08-28
Trying to compile/install mac-3.99 on x64 (using checkinstall). It fails at the very end.  Any monkey's audio afficionados out there that can tell me what is going wrong and how to fix? 

> 
This package will be built according to these values: 

0 -  Maintainer: [ root@ubuntu ]
1 -  Summary: [ Monkey's Audio - a fast and powerful lossless audio compressor ]
2 -  Name:    [ mac-3.99-u4 ]
3 -  Version: [ b5-s4 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ mac-3.99-u4-b5 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
Making install in src
make[1]: Entering directory `/home/user1/downloads/mac-3.99-u4-b5/src'
Making install in Shared
make[2]: Entering directory `/home/user1/downloads/mac-3.99-u4-b5/src/Shared'
make[3]: Entering directory `/home/user1/downloads/mac-3.99-u4-b5/src/Shared'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/include/mac" || mkdir -p -- "/usr/include/mac"
 /usr/bin/install -c -m 644 'config.h' '/usr/include/mac/config.h'
 /usr/bin/install -c -m 644 'All.h' '/usr/include/mac/All.h'
 /usr/bin/install -c -m 644 'GlobalFunctions.h' '/usr/include/mac/GlobalFunctions.h'
 /usr/bin/install -c -m 644 'ID3Genres.h' '/usr/include/mac/ID3Genres.h'
 /usr/bin/install -c -m 644 'IO.h' '/usr/include/mac/IO.h'
 /usr/bin/install -c -m 644 'SmartPtr.h' '/usr/include/mac/SmartPtr.h'
 /usr/bin/install -c -m 644 'StdLibFileIO.h' '/usr/include/mac/StdLibFileIO.h'
 /usr/bin/install -c -m 644 'NoWindows.h' '/usr/include/mac/NoWindows.h'
 /usr/bin/install -c -m 644 'CharacterHelper.h' '/usr/include/mac/CharacterHelper.h'
 /usr/bin/install -c -m 644 'CircleBuffer.h' '/usr/include/mac/CircleBuffer.h'
 /usr/bin/install -c -m 644 'MACUtils.h' '/usr/include/mac/MACUtils.h'
make[3]: Leaving directory `/home/user1/downloads/mac-3.99-u4-b5/src/Shared'
make[2]: Leaving directory `/home/user1/downloads/mac-3.99-u4-b5/src/Shared'
Making install in MACLib
make[2]: Entering directory `/home/user1/downloads/mac-3.99-u4-b5/src/MACLib'
Making install in Assembly
make[3]: Entering directory `/home/user1/downloads/mac-3.99-u4-b5/src/MACLib/Assembly'
make[4]: Entering directory `/home/user1/downloads/mac-3.99-u4-b5/src/MACLib/Assembly'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/user1/downloads/mac-3.99-u4-b5/src/MACLib/Assembly'
make[3]: Leaving directory `/home/user1/downloads/mac-3.99-u4-b5/src/MACLib/Assembly'
make[3]: Entering directory `/home/user1/downloads/mac-3.99-u4-b5/src/MACLib'
make[4]: Entering directory `/home/user1/downloads/mac-3.99-u4-b5/src/MACLib'
test -z "/usr/lib" || mkdir -p -- "/usr/lib"
 /bin/bash ../../libtool --mode=install /usr/bin/install -c  'libmac.la' '/usr/lib/libmac.la'
/usr/bin/install -c .libs/libmac.so.2.0.0 /usr/lib/libmac.so.2.0.0
(cd /usr/lib && rm -f libmac.so.2 && ln -s libmac.so.2.0.0 libmac.so.2)
(cd /usr/lib && rm -f libmac.so && ln -s libmac.so.2.0.0 libmac.so)
/usr/bin/install -c .libs/libmac.lai /usr/lib/libmac.la
/usr/bin/install -c .libs/libmac.a /usr/lib/libmac.a
ranlib /usr/lib/libmac.a
chmod 644 /usr/lib/libmac.a
[COLOR=Red]chmod: changing permissions of `/usr/lib/libmac.a': No such file or directory
make[4]: *** [install-libLTLIBRARIES] Error 1[/COLOR]
make[4]: Leaving directory `/home/user1/downloads/mac-3.99-u4-b5/src/MACLib'
make[3]: *** [install-am] Error 2
make[3]: Leaving directory `/home/user1/downloads/mac-3.99-u4-b5/src/MACLib'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/user1/downloads/mac-3.99-u4-b5/src/MACLib'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/user1/downloads/mac-3.99-u4-b5/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

---

### Post by tek1024 on 2008-11-05
I'm getting the exact same error on Xubuntu 8.10 Intrepid, but "sudo make install" works just fine.  Did you ever find a solution?

---

