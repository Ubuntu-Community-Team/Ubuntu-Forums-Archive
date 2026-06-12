---
title: "Trouble installing Catalyst 12.11 on Ubuntu 12.10 32bit"
date: 2012-12-30
forum: Multimedia Software
---

### Post by Gaaargh on 2012-12-30
Hello all,
I've been having a problem installing ATI's Catalyst 12.11 beta driver on Ubuntu 12.10. My GPU is a Radeon HD 7850. I'm following the instructions here: [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

I get as far as this instruction: 
```
sudo sh ./amd-driver-installer-catalyst-12.10-x86.x86_64.run --buildpkg Ubuntu/quantal
```And I get the following output for my troubles
```
Generating package: Ubuntu/quantal
Package build failed!
Package build utility output:
./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: debclean: not found
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:9.010-0ubuntu1
dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.aKvS2r
dpkg-buildpackage: host architecture i386
 debian/rules build
#Create important strings
for i in 10fglrx \
             dkms.conf \
             fglrx.install \
             fglrx-dev.install \
             fglrx-dev.links \
             fglrx-amdcccle.install \
             fglrx.grub-gfxpayload \
             fglrx.dirs \
             fglrx.links \
             fglrx.postinst \
             fglrx.postrm \
             fglrx.preinst \
             fglrx.prerm \
             overrides/fglrx; do \
        sed -e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \
            -e "s|#LIBDIR#|usr/lib|g" \
            -e "s|#LIBDIR32#|usr/lib32|g" \
            -e "s|#BINDIR#|usr/bin|g" \
            -e "s|#SYSCONFDIR#|etc|g" \
            -e "s|#MANDIR#|usr/share/man/man1|g" \
            -e "s|#LDSOCONF#|usr/lib/fglrx/ld.so.conf|g" \
            -e "s|#ALTLDSOCONF#|usr/lib/fglrx/alt_ld.so.conf|g" \
            -e "s|#ALTPRIORITY#|1000|g" \
            -e "s|#PXALTPRIORITY#|900|g" \
            -e "s|#AUTOSTARTDIR#|etc/xdg/autostart|g" \
            -e "s|#DATADIR#|usr/share|g" \
            -e "s|#PKGDESKDIR#|usr/share/fglrx|g" \
            -e "s|#PKGDATADIR#|usr/share/fglrx|g" \
            -e "s|#PKGCONFIGDIR#|usr/lib/fglrx|g" \
            -e "s|#PKGBINDIR#|usr/lib/fglrx/bin|g" \
            -e "s|#PKGLIBDIR#|usr/lib/fglrx|g" \
            -e "s|#PKGLIBDIR32#|usr/lib32/fglrx|g" \
            -e "s|#PKGDRIVERSDIR#|usr/lib/fglrx/xorg|g" \
            -e "s|#XORGEXTRA#|usr/lib/i386-linux-gnu/xorg/extra-modules|g" \
            -e "s|#PKGEXTENSIONDIR#|usr/lib/fglrx/xorg|g" \
            -e "s|#XORGEXTENSIONSDIR#|usr/lib/xorg/modules/extensions|g" \
            -e "s|#DRIVERNAME#|fglrx|g" \
            -e "s|#DRIVERDEVNAME#|fglrx-dev|g" \
            -e "s|#DRIVERSRCNAME#||g" \
            -e "s|#INCLUDEDIR#|usr/include|g" \
            -e "s|#PKGLIBCONFDIR#|lib/fglrx|g" \
            -e "s|#GRUBBLKLISTDIR#|usr/share/grub-gfxpayload-lists/blacklist|g" \
            -e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \
            -e "s|#PXDIR#|usr/lib/pxpress|g" \
            -e "s|#PXDIR32#|usr/lib32/pxpress|g" \
            -e "s|#PXXMODDIR#|usr/lib/pxpress/xorg/modules|g" \
            -e "s|#PXDIRNAME#|pxpress|g" \
            -e "s|#PXLIBDIR#|usr/lib/pxpress/lib|g" \
            -e "s|#PXLIBDIR32#|usr/lib32/pxpress/lib|g" \
            -e "s|#PXLDSOCONF#|usr/lib/pxpress/ld.so.conf|g" \
            -e "s|#ALTPXLDSOCONF#|usr/lib/pxpress/alt_ld.so.conf|g" \
            -e "s|#CVERSION#|9.010|g" \
            -e "s|#SRCXARCH#|xpic|g" \
            -e "s|#SRCARCH#|x86|g" \
            -e "s|#SRCOTHERARCH#|x86_64|g" \
            -e "s|#SRCLIBDIR#|lib|g" \
            -e "s|#DEB_HOST_MULTIARCH#|i386-linux-gnu|g" \
            -e "s|#OTHER_ARCH#|x86_64-linux-gnu|g" \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        xpic     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
        arch/x86/usr/X11R6/bin \
        usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# set the permissions on the pxpress scripts
chmod 744 debian/pxpress/switch*
dh build
   dh_testdir
   dh_auto_configure
   dh_auto_build
   dh_auto_test
dh build
 debian/rules binary
# refresh copyright file
cat debian/copyright_stub_0 > debian/copyright
cat usr/share/doc/fglrx/LICENSE.TXT >> debian/copyright
cat debian/copyright_stub_1 >> debian/copyright
#Steps that we can't easily represent in debhelper files or .in files yet
# Remove any libraries that may be caught by shell expansion
find . -name libGLE* | xargs rm -f
find . -name libEGL* | xargs rm -f
dh_installdirs -pfglrx
# Install the QT libraries
dh_install -pfglrx "arch/x86_64/usr/share/ati/lib" "usr/share/ati"
cp: cannot stat `debian/tmp/arch/x86_64/usr/share/ati/lib': No such file or directory
dh_install: cp -a debian/tmp/arch/x86_64/usr/share/ati/lib debian/fglrx/usr/share/ati/ returned exit code 1
make: *** [binary-arch] Error 2
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.XPx6MP
```From my limited understanding of this output, I think the installer is looking in the wrong place for "debian/tmp/arch/x86_64/usr/share/ati/lib", but I'm not sure if I'm right, and if I am, I'm not sure how to fix this. 

Could anyone here read through the output above and make more sense of it for me?

---

### Post by MrKrinkin on 2013-01-01
I don't see why an error comes up but try these things

sudo apt-get install linux-headers-generic
sudo apt-get install dh-make dh-modaliases execstack

Then try building the package again.

I had on issues doing this on 64bit though.

---

### Post by bosyber on 2013-01-14
> **Gaaargh said:**
> Hello all,
I've been having a problem installing ATI's Catalyst 12.11 beta driver on Ubuntu 12.10. My GPU is a Radeon HD 7850. I'm following the instructions here: [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

I get as far as this instruction: 
```
sudo sh ./amd-driver-installer-catalyst-12.10-x86.x86_64.run --buildpkg Ubuntu/quantal
```
... <snip> ...

From my limited understanding of this output, I think the installer is looking in the wrong place for "debian/tmp/arch/x86_64/usr/share/ati/lib", but I'm not sure if I'm right, and if I am, I'm not sure how to fix this. 

Could anyone here read through the output above and make more sense of it for me?
I had the same problem, and you are right, it is looking in/for the wrong place when copying some bits. 
Short version:
0) save the below to a file rules.patch (or use the attached file):
```
 
*** rules.bak   2013-01-14 16:26:04.454851290 +0100
--- rules       2013-01-14 16:40:05.958872145 +0100
*************** else
*** 241,243 ****
        # Install the QT libraries
!       dh_install -p$(PKG_driver) "arch/x86_64/usr/share/ati/lib" "$(datadir)/ati"
  endif
--- 241,243 ----
        # Install the QT libraries
!       dh_install -p$(PKG_driver) "arch/x86/usr/share/ati/lib" "$(datadir)/ati"
  endif
```

1) extract the files from the amd*.run file, in my case like this:
```
 $sh ./amd-driver-installer-catalyst-12.11-beta11-x86.x86_64.run --extract ~/build/amd-v12.11
```

2) Change the wrong path in the rules file:
```
$ cd  ~/build/amd-v12.11
$ cd packages/Ubuntu/dists/quantal
$ cp rules rules.bak
$ patch rules < ~/build/rules.patch
```
 
3) Build the packages (this will place the packages in the parent directory):
[/CODE]$ ./ati-installer.sh 9.000 --buildpkg Ubuntu/quantal[/CODE]

A few notes:

I am running an x86_64 kernel with x86 userland, if you are not you may have to make different changes in the "rules" file. I started by comparing with the version from the v12.10 driver. In both versions, there is some hackery in there intended to overwrite the right path if your computer is detected to be either x86 or x86_64, though that clearly isn't working entirely right. But the main difference between those versions is that from v12.11 beta it also seems to install QT stuff, so there is more copying, and more libraries added to the build. That is also were the change I made takes effect, look for
the string "*QT libraries*" in the rules file.

Note that all this applies equally to any version of ubuntu at least, not just quantal, and possibly debian too.

**kernel 3.7 (and up?)**:
Since I was not running the normal 3.5 kernel but instead a 3.7.1 kernel, I in addition followed the advice from [http://ubuntuforums.org/showthread.php?t=1988444](http://ubuntuforums.org/showthread.php?t=1988444): 

2a) Download and apply the patch [http://catalyst.apocalypsus.net/files/arch-fglrx-3.7.patch](http://catalyst.apocalypsus.net/files/arch-fglrx-3.7.patch):
```
$ cd ~/build/amd-v12.11
$ patch -p1 < ./3.7.patch 
```

and I had to in addition follow the advice from [http://ubuntuforums.org/showthread.php?t=2075495](http://ubuntuforums.org/showthread.php?t=2075495) to
2b) add a symbolic link for version.h in the linux kernel headers from the new location in uapi:
```
$ sudo ln -s /lib/modules/3.7.1-030701-generic/build/include/{generated/uapi/,}linux/version.h  

```

With that it all seemed to produce working fglrx stuff.

---

### Post by Gaaargh on 2013-02-16
Hi bosyber, thanks a million for that detailed reply! I used your patch but unfortunately I'm still getting the exact same error :confused:. Now I'm **really **confused, as I can see that the line in my rules file is:
```
dh_install -p$(PKG_driver) "arch/x86/usr/share/ati/lib" "$(datadir)/ati"
``` 
but when I execute
```
$ ./ati-installer.sh 9.012 --buildpkg Ubuntu/quantal
```
(btw I've moved onto driver version 13.1, hence the 9.012), I still get 
```
# Install the QT libraries
dh_install -pfglrx "arch/x86_64/usr/share/ati/lib" "usr/share/ati"
cp: cannot stat `debian/tmp/arch/x86_64/usr/share/ati/lib': No such file or directory

```
So maybe the rules file in Ubuntu/quantal isn't being called somehow? Is there some edit I could apply to see if this is true?

---

### Post by Gaaargh on 2013-02-16
Welp, apparently I'm just a massive idiot :oops: I wasn't rebuilding with admin privileges. 
```
sudo ./ati-installer.sh 9.012 --buildpkg Ubuntu/quantal
```
seems to have done the trick. Will reboot and check now.

---

### Post by Gaaargh on 2013-02-16
> **Gaaargh said:**
> Welp, apparently I'm just a massive idiot :oops: I wasn't rebuilding with admin privileges. 
```
sudo ./ati-installer.sh 9.012 --buildpkg Ubuntu/quantal
```seems to have done the trick. Will reboot and check now.
EDIT: Yep I'm a confirmed idiot. Driver seems to be installed ok. Say a prayer this finally makes TF2 playable on this install for me! :D

---

### Post by Yellow Pasque on 2013-02-16
Hmm, the last time I checked, you didn't need root permissions just to build the packages, as long as your user owned the .run file and you were in a non-root directory (also assuming fakeroot was installed).

---

