---
title: "libpciaccess0 patch Catalyst"
date: 2012-10-17
forum: Multimedia Software
---

### Post by snoopy1024 on 2012-10-17
OK, here goes.

[LEFT] Am a fairly new user so please, bare with me.
I have to patch libpciaccess0 for proper Catalyst 12.6 function. Running  64-bit 12.04 with ATI HD3200 graphic card and proprietary 12.6 drivers  are the only  drivers 
for my hardware compatible with xorg-server 1.12. Open source drivers  lack smoothness in video playback and fglrx from the repository just  give crappy performance overall.

I have found a solution in another thread, but am unable to follow accordingly...
It is marked solved, so posting there won't get enough attention.
Please help me understand and learn for future reference...

[http://ubuntuforums.org/showthread.php?t=2031533](http://ubuntuforums.org/showthread.php?t=2031533)


I have a working build environment and after

```
$ apt-get source libpciaccess0
```i get

```
Picking 'libpciaccess' as source package instead of 'libpciaccess0'
```Alright, now I have **libpciaccess-0.12.902** folder in my home directory.
With **build-dep libciaccess** I get neccessary dependencies and after **debcheckout libpciaccess0** a **libpciaccess0** folder emerges.

cd to **libpciaccess0 **and apply patch with [B]patch -p1
[/B]terminal responds:

```
patching file src/common_interface.c
patching file src/common_io.c
```Great, but when I try to build with [B]dpkg-buildpackage -us -uc -B

[/B]```
dpkg-buildpackage: source package libpciaccess
dpkg-buildpackage: source version 0.13.1-2
dpkg-buildpackage: source changed by Julien Cristau <jcristau@debian.org>
dpkg-buildpackage: host architecture amd64
 dpkg-source --before-build libpciaccess0
dpkg-checkbuilddeps: Unmet build dependencies: quilt (>= 0.46-7)
dpkg-buildpackage: warning: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: warning: (Use -d flag to override.)
```Not working with -d flag either:

```
dpkg-buildpackage: source package libpciaccess
dpkg-buildpackage: source version 0.13.1-2
dpkg-buildpackage: source changed by Julien Cristau <jcristau@debian.org>
dpkg-buildpackage: host architecture amd64
 dpkg-source --before-build libpciaccess0
 fakeroot debian/rules clean
dh clean --with autoreconf,quilt --builddirectory=build/ --parallel
dh: unable to load addon quilt: Can't locate Debian/Debhelper/Sequence/quilt.pm in
 @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2
 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14 
/usr/local/lib/site_perl .) at (eval 18) line 2.
BEGIN failed--compilation aborted at (eval 18) line 2.

make: *** [clean] Error 2
dpkg-buildpackage: error: fakeroot debian/rules clean gave error exit  status 2
```Since libpciaccess0 is part of libpciaccess package I  tried applying patch to **libpciaccess-0.12.902 **- it was successful 
```
patching file src/common_interface.c
patching file src/common_io.c
Hunk #1 succeeded at 31 with fuzz 2 (offset 3 lines).
Hunk #2 succeeded at 96 (offset 26 lines).
Hunk #3 succeeded at 139 (offset 26 lines).
Hunk #4 succeeded at 159 (offset 26 lines).
```so i also ran

```
dpkg-buildpackage -us -uc -B
```and was able to build patched deb package **libpciaccess0_0.12.902-1_amd64.deb**
Unfortuantely, after installation and reboot xorg is broken and have to revert to previous version.

How can I patch it properly?




[/LEFT]

---

### Post by snoopy1024 on 2012-10-22
Didn't have a chance to experiment more, but no replies yet  :(.
I'll give it a try with 12.10 in the next few days, if someone knows the solution, please post it or send me a message. Thank you.

---

