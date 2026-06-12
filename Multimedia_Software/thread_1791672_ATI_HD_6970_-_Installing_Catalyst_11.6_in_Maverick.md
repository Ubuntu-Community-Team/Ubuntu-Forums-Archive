---
title: "ATI HD 6970 - Installing Catalyst 11.6 in Maverick"
date: 2011-06-27
forum: Multimedia Software
---

### Post by BrightEyesDavid on 2011-06-27
Ubuntu is displaying the desktop okay (though limited to 1600x1200) after my having installed my new HD 6970 card, so I'm now trying to install the proprietary driver (I understand the open source one requires a more recent kernel than that in Maverick).

The proprietary driver under 'Additional Drivers' resulted in a black screen on boot, so I deactivated and am trying to follow the manual install instructions at the [cchtml Ubuntu Maverick Installation Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually").

When I try to create the .deb packages with:
```
sh ati-driver-installer-11-6-x86.x86_64.run --buildpkg Ubuntu/maverick
```I get:

```
david@skipper:~/catalyst11.6$ sh ati-driver-installer-11-6-x86.x86_64.run --buildpkg Ubuntu/maverick
Created directory fglrx-install.oLN3ux
Verifying archive integrity... All good.
Uncompressing ATI Catalyst(TM) Proprietary Driver-8.861.........................
=====================================================================
 ATI Technologies Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Generating package: Ubuntu/maverick
Package build failed!
Package build utility output:
./packages/Ubuntu/ati-packager.sh: 396: debclean: not found
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.861-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.64Vzxk
dpkg-buildpackage: host architecture amd64
 debian/rules build
Can't exec "debian/rules": Permission denied at /usr/bin/dpkg-buildpackage line 507.
dpkg-buildpackage: error: debian/rules build failed with unknown exit code -1
Cleaning in directory .
/usr/bin/fakeroot: line 176: debian/rules: Permission denied
debuild: fatal error at line 1319:
couldn't exec fakeroot debian/rules: 
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.861-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.QEmIld
dpkg-buildpackage: host architecture amd64
 debian/rules build
Can't exec "debian/rules": Permission denied at /usr/bin/dpkg-buildpackage line 507.
dpkg-buildpackage: error: debian/rules build failed with unknown exit code -1
Cleaning in directory .
Can't exec "debian/rules": Permission denied at /usr/bin/debuild line 1314.
debuild: fatal error at line 1313:
couldn't exec debian/rules: Permission denied
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.861-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.xtY6vC
dpkg-buildpackage: host architecture amd64
 debian/rules build
Can't exec "debian/rules": Permission denied at /usr/bin/dpkg-buildpackage line 507.
dpkg-buildpackage: error: debian/rules build failed with unknown exit code -1
Cleaning in directory .
/usr/bin/fakeroot: line 176: debian/rules: Permission denied
debuild: fatal error at line 1319:
couldn't exec fakeroot debian/rules: 
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.861-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.oYWICI
dpkg-buildpackage: host architecture amd64
 debian/rules build
Can't exec "debian/rules": Permission denied at /usr/bin/dpkg-buildpackage line 507.
dpkg-buildpackage: error: debian/rules build failed with unknown exit code -1
Removing temporary directory: fglrx-install.oLN3ux
```I've installed devscripts which has debclean in it.

I don't know what to do next...

Many thanks.

---

### Post by mogliii on 2011-08-01
do you have a ssd?

I had the same error and the problem was due to "noexec" mount of /tmp. I mounted my tmp in ram as tmpfs.

This workaround helped me
[http://serialized.net/2010/03/getting-around-tmpfs-noexec-problems/](http://serialized.net/2010/03/getting-around-tmpfs-noexec-problems/)

And here a bug report which is related:
[http://www.mail-archive.com/debian-dpkg-bugs@lists.debian.org/msg07771.html](http://www.mail-archive.com/debian-dpkg-bugs@lists.debian.org/msg07771.html)

---

### Post by BrightEyesDavid on 2011-08-01
I do indeed, and also have tmp mounted in RAM with noexec - thanks!

I previously got round the issue by [having the installer run directly without making a .deb package]("http://askubuntu.com/questions/50771/installing-catalyst-11-6-for-an-ati-hd-6970").

---

