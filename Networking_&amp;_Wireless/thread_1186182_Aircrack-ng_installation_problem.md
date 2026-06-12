---
title: "Aircrack-ng installation problem"
date: 2009-06-13
forum: Networking &amp; Wireless
---

### Post by exus69 on 2009-06-13
Hello everybody,

Am facing a problem installing the latest version of Aircrack-ng (1.0-rc3) on Ubuntu 9.04 which has the updated repositories :

```

root@ubuntu:~# cd /root/Desktop/aircrack-ng-1.0-rc3/src
root@ubuntu:~/Desktop/aircrack-ng-1.0-rc3/src# make
make -C osdep
make[1]: Entering directory `/root/Desktop/aircrack-ng-1.0-rc3/src/osdep'
Building for Linux
make[2]: Entering directory `/root/Desktop/aircrack-ng-1.0-rc3/src/osdep'
make[2]: `.os.Linux' is up to date.
make[2]: Leaving directory `/root/Desktop/aircrack-ng-1.0-rc3/src/osdep'
make[1]: Leaving directory `/root/Desktop/aircrack-ng-1.0-rc3/src/osdep'
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
make: *** [aircrack-ng.o] Error 1

```

I found a possible solution after googling which dint help unfortunately. Heres the link [http://forum.aircrack-ng.org/index.php?topic=5456.0](http://forum.aircrack-ng.org/index.php?topic=5456.0)

Am using the default drivers of my Edimax EW-7318USg USB adapter

Please help

Note: I've posted this same problem in the Absolute Beginners thread by   mistake but since I could'nt delete the same I reposted it over here

Sunny

---

### Post by kevdog on 2009-06-13
Ive compiled aircrack before without a problem, however it seems like you are missing a dependency.

---

### Post by munky99999 on 2009-06-13
Well make sure you have the package "build-essential"

OR do the SVN method.

---

