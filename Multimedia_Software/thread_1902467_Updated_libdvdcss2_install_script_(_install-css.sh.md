---
title: "Updated libdvdcss2 install script ( install-css.sh )"
date: 2011-12-30
forum: Multimedia Software
---

### Post by dbbolton on 2011-12-30
I read this article: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
and had trouble finding the **install-css.sh** script. When I finally found a copy online, it did not work because the mirror no longer exists. I found the source on debian.org and modified the script to use it, along with some other miscellaneous improvements.

The new version of the script can be found here: [https://github.com/dbb/debian-scripts/blob/master/install-css.sh](https://github.com/dbb/debian-scripts/blob/master/install-css.sh)

If this method is no longer advisable, please let me know and I urge you to edit the help page as well.

---

### Post by mc4man on 2011-12-30
The script is in libdvdread4 & still works fine.
Ex.
```
:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
[sudo] password for doug: 
--2011-12-30 21:42:22--  http://packages.medibuntu.org/dists/oneiric/free/binary-i386/Packages
Resolving packages.medibuntu.org... 88.191.127.22
Connecting to packages.medibuntu.org|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7889 (7.7K) [text/plain]
Saving to: `/tmp/dvdcss-m9j2Nk/Packages'

100%[==============================================================================>] 7,889       --.-K/s   in 0.09s   

2011-12-30 21:42:22 (84.8 KB/s) - `/tmp/dvdcss-m9j2Nk/Packages' saved [7889/7889]

--2011-12-30 21:42:22--  http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb
Resolving packages.medibuntu.org... 88.191.127.22
Connecting to packages.medibuntu.org|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 38036 (37K) [application/x-debian-package]
Saving to: `/tmp/dvdcss-m9j2Nk/libdvdcss.deb'

100%[==============================================================================>] 38,036       134K/s   in 0.3s    

2011-12-30 21:42:23 (134 KB/s) - `/tmp/dvdcss-m9j2Nk/libdvdcss.deb' saved [38036/38036]

Selecting previously deselected package libdvdcss2.
(Reading database ... 234256 files and directories currently installed.)
Unpacking libdvdcss2 (from .../dvdcss-m9j2Nk/libdvdcss.deb) ...
Setting up libdvdcss2 (1.2.10-0.3medibuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

---

