---
title: "Error unpacking latest ATI Driver :("
date: 2007-03-10
forum: Multimedia &amp; Video
---

### Post by jmattos on 2007-03-10
Hi all.

I'm followingthe directions here...[https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=(Driver)%7C(ATI)#head-99489608eb537a1a0346cdd3ad34209d7887714a](https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=(Driver)%7C(ATI)#head-99489608eb537a1a0346cdd3ad34209d7887714a)

and when I try to execute the following
bash ./ati-driver-installer-8.34.8-x86.x86_64.run --buildpkg Ubuntu/edgy

_I get the following:_
jsmith@jsmith-desktop:~/Desktop/ATI Install$ **bash ./ati-driver-installer-8.34.8-x86.x86_64.run --buildpkg Ubuntu/edg**y
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.34.8..........................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/edgy
cp: cannot stat `Install/fglrx-install/x710/*': No such file or directory
cp: cannot stat `Install/fglrx-install/arch/x86/*': No such file or directory
cp: cannot stat `Install/fglrx-install/common/*': No such file or directory
cp: target `/tmp/fglrx.v30935/usr/X11R6/' is not a directory: No such file or directory
chmod: cannot access `Install/fglrx-install/packages/Ubuntu': No such file or directory
cp: target `/tmp/fglrx.v30935/debian' is not a directory
cp: cannot stat `Install/fglrx-install/packages/Ubuntu/module': No such file or directory
./packages/Ubuntu/ati-packager.sh: line 34: /tmp/fglrx.v30935/debian/changelog: No such file or directory
./packages/Ubuntu/ati-packager.sh: line 36: /tmp/fglrx.v30935/debian/changelog: No such file or directory
./packages/Ubuntu/ati-packager.sh: line 38: /tmp/fglrx.v30935/debian/changelog: No such file or directory
Package build failed!
Package build utility output:
dpkg-parsechangelog: error: cannot open debian/changelog to find format: No such file or directory
dpkg-buildpackage: unable to determine source package is
Removing temporary directory: fglrx-install
jsmith@smith-desktop:~/Desktop/ATI Install$

---

### Post by jmattos on 2007-03-10
[SOLVED]

I downloaded the ATI driver "run" file to a directory called "ATI Install" on my desktop, then created a terminal, CD'd into it, and ran the commands. This is apparently bad.

I moved the file to ATI then reran and it seems to have gotten through that step.

weird?

---------------
jmattos@jmattos-desktop:~/Desktop/ATI$ sudo ln -sf bash /bin/shjmattos@jmattos-desktop:~/Desktop/ATI$ bash ./ati-driver-installer-8.34.8-x86.x86_64.run --buildpkg Ubuntu/edgy
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.34.8..................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/edgy
Package /home/jmattos/Desktop/ATI/xorg-driver-fglrx_8.34.8-1_i386.deb has been successfully generated
Package /home/jmattos/Desktop/ATI/xorg-driver-fglrx-dev_8.34.8-1_i386.deb has been successfully generated
Package /home/jmattos/Desktop/ATI/fglrx-kernel-source_8.34.8-1_i386.deb has been successfully generated
Package /home/jmattos/Desktop/ATI/fglrx-control_8.34.8-1_i386.deb has been successfully generated
Package /home/jmattos/Desktop/ATI/fglrx-sources_8.34.8-1_i386.deb has been successfully generated
Removing temporary directory: fglrx-install
jmattos@jmattos-desktop:~/Desktop/ATI$ ls
ati-driver-installer-8.34.8-x86.x86_64.run  fglrx-sources_8.34.8-1_i386.deb
fglrx-control_8.34.8-1_i386.deb             xorg-driver-fglrx_8.34.8-1_i386.deb
fglrx-installer_8.34.8-1_i386.changes       xorg-driver-fglrx-dev_8.34.8-1_i386.deb
fglrx-kernel-source_8.34.8-1_i386.deb
jmattos@jmattos-desktop:~/Desktop/ATI$ 
jmattos@jmattos-desktop:~/Desktop/ATI$ bash ./ati-driver-installer-8.34.8-x86.x86_64.run --buildpkg Ubuntu/edgy

---

