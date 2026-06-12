---
title: "rt2750 driver installation problem- aircrack"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by Tozarian on 2009-01-27
I have a nintendo wifi usb connector which is just a re-branded buffalo adapter but with a different usb id. I am trying to install the drivers using this guide 

[http://www.aircrack-ng.org/doku.php?id=rt2570](http://www.aircrack-ng.org/doku.php?id=rt2570)

I get a "no device present error"
and when i just try skipping a couple steps to the installation it tell me i cannot create a directory

PC:~/rt2570-k2wrlz-1.6.3/Module$ make && make install
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
2.6 module install
make -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/home/michael/rt2570-k2wrlz-1.6.3/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
mkdir: cannot create directory `/lib/modules/2.6.27-9-generic/extra': Permission denied
make[1]: *** [_emodinst_] Error 1
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [modules_install] Error 2
michael@Ubuntu-PC:~/rt2570-k2wrlz-1.6.3/Module$ 

what am I doing wrong here? Is this impossible to get aircrack working with this adapter?

---

### Post by denbeigh2000 on 2009-05-23
I'm having a similar problem.

When I use the make command:

denbeigh@denbeigh-laptop:~/aircrack2/aircrack-ng-1.0-rc3$ make
make -C src all
make[1]: Entering directory `/home/denbeigh/aircrack2/aircrack-ng-1.0-rc3/src'
make -C osdep
make[2]: Entering directory `/home/denbeigh/aircrack2/aircrack-ng-1.0-rc3/src/osdep'
Building for Linux
make[3]: Entering directory `/home/denbeigh/aircrack2/aircrack-ng-1.0-rc3/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o osdep.o osdep.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o network.o network.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o linux.o linux.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o linux_tap.o linux_tap.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o radiotap-parser.o radiotap-parser.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o common.o common.c
ar cru libosdep.a  osdep.o network.o linux.o linux_tap.o radiotap-parser.o common.o
ranlib libosdep.a 
touch .os.Linux
make[3]: Leaving directory `/home/denbeigh/aircrack2/aircrack-ng-1.0-rc3/src/osdep'
make[2]: Leaving directory `/home/denbeigh/aircrack2/aircrack-ng-1.0-rc3/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -Iinclude   -c -o aircrack-ng.o aircrack-ng.c
In file included from aircrack-ng.c:65:
crypto.h:12:26: error: openssl/hmac.h: No such file or directory
crypto.h:13:25: error: openssl/sha.h: No such file or directory
crypto.h:15:25: error: openssl/rc4.h: No such file or directory
crypto.h:16:25: error: openssl/aes.h: No such file or directory
cc1: warnings being treated as errors
In file included from aircrack-ng.c:69:
sha1-sse2.h: In function ‘calc_4pmk’:
sha1-sse2.h:143: error: implicit declaration of function ‘HMAC’
sha1-sse2.h:143: error: implicit declaration of function ‘EVP_sha1’
aircrack-ng.c: In function ‘crack_wpa_thread’:
aircrack-ng.c:3876: error: implicit declaration of function ‘EVP_md5’
make[1]: *** [aircrack-ng.o] Error 1
make[1]: Leaving directory `/home/denbeigh/aircrack2/aircrack-ng-1.0-rc3/src'
make: *** [all] Error 2


Anything I'm doing wrong??

---

