---
title: "can't compile vpnc with openssl from source in karmic"
date: 2009-12-19
forum: Networking &amp; Wireless
---

### Post by jmarks on 2009-12-19
I am trying to compile vpnc 0.5.3 from source with openssl under karmic. There is a fair amount of straightforward documentation in the forums on how to do this, but it is not working.
I downloaded and unpacked vpnc 0.5.3 from [www.unix-ag.uni-kl.de/~massar/vpnc/]("http://www.unix-ag.uni-kl.de/%7Emassar/vpnc/")
I installed openssl and openssl-dev.
I made sure I had all the dependencies with ```
 sudo apt-get build-dep vpnc 
```I uncommented the two lines in the Makefile in the vpnc directory that allows compilation with openssl
(there is no ./configure file in the vpnc source directory)
the problem comes with running ```
 dpkg-buildpackage 
``` I must be missing critical files, because I get the following error text:
```

dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
tail: cannot open `debian/changelog' for reading: No such file or directory
dpkg-buildpackage: error: tail of debian/changelog gave error exit status 1

```I have never compiled code from source before so I can't figure out what to do next. The tar archive I downloaded does have a changelog file but does not have a debian/changelog.gz file.
Thanks for any help!

---

