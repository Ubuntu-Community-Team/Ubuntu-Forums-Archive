---
title: "Video Card upgrade - driver issues"
date: 2010-04-24
forum: Multimedia Software
---

### Post by taurolyon on 2010-04-24
I recently upgraded my ATI HD4670 to an HD5870. I then attempted to  reinstall my ATI fglrx drivers to accommodate for my new device. 

Every time I try to activate the driver using the Hardware Drivers GUI -  I get "SystemError: installArchives() failed"

I checked Synapic and it informed me I had a broken package: **flgrx-amdcccle**

Attempting to reinstall this package: **E:  /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu3_amd64.deb: subprocess  new pre-installation script returned error exit status 1**

```

(Reading database ... 189870 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.723.1-0ubuntu3_amd64.deb) ...

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run /usr/share/ati/fglrx-uninstall.sh (this  is not recommended).

dpkg: error processing  /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu3_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not installed.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fglrx-amdcccle

```I think something in my old driver installation is causing issues  here. Any ideas?

---

### Post by taurolyon on 2010-04-25
**Sigh**

2 hours and still no luck...

I even tried to build DEB packages and getting errors... I think it's going to be a new Ubuntu install on Thursday for me... 

Here's my --buildpkg output:

```
jay@jay-desktop:~$ sudo ./ati-driver-installer-10-3-x86.x86_64.run --buildpkg Ubuntu/lucid
Created directory fglrx-install.GDmMzn
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.712..........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/lucid
Package build failed!
Package build utility output:
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.712-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture amd64
#Create important strings
for i in 10fglrx \
             dkms.conf \
             fglrx.install \
             fglrx-dev.install \
             fglrx-amdcccle.install \
             overrides/fglrx; do \
        sed -e "s|#XMODDIR#|usr/lib/fglrx/xorg/modules|"     \
            -e "s|#XMODDIR32#||" \
            -e "s|#DRIDIR32#|usr/lib32/fglrx|"   \
            -e "s|#LIBDIR#|lib64|"       \
            -e "s|#DRIDIR#|usr/lib/fglrx|"       \
            -e "s|#CVERSION#|8.712|"   \
            -e "s|#XARCH#|x740_64a|"   \
            -e "s|#ARCH#|x86_64|"   \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        x740_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
        usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
        x740_64a/usr/X11R6/lib64/modules/drivers/fglrx_drv.so > \
        debian/modaliases/fglrx-modules.alias.override
dh build
   dh_testdir
   dh_auto_configure
   dh_auto_build
   dh_auto_test
 debian/rules binary
#Steps that we can't easily represent in debhelper files or .in files yet
dh_install -pfglrx    "arch/x86/usr/X11R6/lib/libAMD*.so*"           "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/*.so*"           "usr/lib32/fglrx"
dh_installdirs -pfglrx "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/modules/dri"     "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/lib/*"                     "usr/lib32/fglrx"
for i in \
            debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so \
            debian/fglrx/usr/lib32/fglrx/libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
- debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so
- debian/fglrx/usr/lib32/fglrx/libGL.so.1.2
#they don't provide the symlink for us (starting at 8.699)
dh_link -pfglrx usr/lib32/fglrx/libatiuki.so.1.0 usr/lib32/fglrx/libatiuki.so.1
dh_installdocs -pfglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pfglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
Duplicate specification "O=s" for option "O"
#remove executable bits from stack
dh_install -pfglrx-amdcccle
execstack -c debian/fglrx-amdcccle/usr/lib/fglrx/bin/amdcccle
dh_install -pfglrx
for i in \
            debian/fglrx/usr/lib/fglrx/bin/atiode \
            debian/fglrx/usr/lib/fglrx/bin/amdnotifyui \
            debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so \
            debian/fglrx/usr/lib/fglrx/libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
- debian/fglrx/usr/lib/fglrx/bin/atiode
- debian/fglrx/usr/lib/fglrx/bin/amdnotifyui
- debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so
- debian/fglrx/usr/lib/fglrx/libGL.so.1
- debian/fglrx/usr/lib/fglrx/libGL.so.1.2
# Blacklist any other driver that udev may want to load instead of fglrx
printf "blacklist radeon\n" > /tmp/fglrx.Sa4Dod/debian/fglrx/usr/lib/fglrx/modprobe.conf
#ld.so.conf
echo "usr/lib/fglrx" >    "/tmp/fglrx.Sa4Dod/debian/fglrx/usr/lib/fglrx/ld.so.conf"
echo "usr/lib32/fglrx" >>    "/tmp/fglrx.Sa4Dod/debian/fglrx/usr/lib/fglrx/ld.so.conf"
#Run the normal stuff
dh binary
   dh_testroot -Nfglrx -Nfglrx-amdcccle
   dh_prep -Nfglrx -Nfglrx-amdcccle
   dh_installdirs -Nfglrx -Nfglrx-amdcccle
   dh_auto_install -Nfglrx -Nfglrx-amdcccle
   dh_install -Nfglrx -Nfglrx-amdcccle
   dh_installdocs -Nfglrx
   dh_installchangelogs
   dh_installexamples
   dh_installman
   dh_installcatalogs
   dh_installcron
   dh_installdebconf
   dh_installemacsen
   dh_installifupdown
   dh_installinfo
   dh_pysupport
   dh_installinit -Nfglrx
Duplicate specification "O=s" for option "O"
   dh_installmenu
   dh_installmime
   dh_installmodules
   dh_installlogcheck
   dh_installlogrotate
   dh_installpam
   dh_installppp
   dh_installudev
   dh_installwm
   dh_installxfonts
   dh_bugfiles
   dh_lintian
   dh_gconf
   dh_icons
   dh_perl
   dh_usrlocal
   dh_link -Nfglrx
   dh_compress
   dh_fixperms
   dh_strip
   dh_makeshlibs
objdump: debian/fglrx/usr/lib/fglrx/ld.so.conf: File format not recognized
   debian/rules override_dh_shlibdeps
make[1]: Entering directory `/tmp/fglrx.Sa4Dod'
dh_shlibdeps -l`pwd`/debian/fglrx/usr/lib/fglrx
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/bin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.
dpkg-shlibdeps: warning: debian/fglrx/usr/lib32/fglrx/libXvBAW.so.1.0 contains an unresolvable reference to symbol dlopen: it's probably a plugin.
dpkg-shlibdeps: warning: 2 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libGL.so.1.2 contains an unresolvable reference to symbol XGetGeometry: it's probably a plugin.
dpkg-shlibdeps: warning: 31 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: debian/fglrx/usr/lib32/fglrx/libAMDXvBA.so.1.0 contains an unresolvable reference to symbol dlsym: it's probably a plugin.
dpkg-shlibdeps: warning: 21 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: debian/fglrx/usr/lib32/fglrx/libfglrx_gamma.so.1.0 contains an unresolvable reference to symbol XextCreateExtension: it's probably a plugin.
dpkg-shlibdeps: warning: 5 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: debian/fglrx/usr/lib32/fglrx/libfglrx_dm.so.1.0 contains an unresolvable reference to symbol XextCreateExtension: it's probably a plugin.
dpkg-shlibdeps: warning: 6 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 contains an unresolvable reference to symbol dlsym: it's probably a plugin.
dpkg-shlibdeps: warning: 21 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: error: no dependency information found for /usr/share/ati/lib64/libQtCore.so.4 (used by debian/fglrx/usr/lib/fglrx/bin/amdnotifyui).
dh_shlibdeps: dpkg-shlibdeps -Tdebian/fglrx.substvars debian/fglrx/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so debian/fglrx/usr/lib/fglrx/xorg/modules/linux/libfglrxdrm.so debian/fglrx/usr/lib/fglrx/xorg/modules/amdxmm.so debian/fglrx/usr/lib/fglrx/xorg/modules/glesx.so debian/fglrx/usr/lib/fglrx/xorg/modules/extensions/libglx.so debian/fglrx/usr/lib/fglrx/libXvBAW.so.1.0 debian/fglrx/usr/lib/fglrx/libGL.so.1.2 debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so debian/fglrx/usr/lib/fglrx/libfglrx_gamma.so.1.0 debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 debian/fglrx/usr/lib/fglrx/libaticalrt.so debian/fglrx/usr/lib/fglrx/libfglrx_dm.so.1.0 debian/fglrx/usr/lib/fglrx/libatiuki.so.1.0 debian/fglrx/usr/lib/fglrx/bin/amdnotifyui debian/fglrx/usr/lib/fglrx/bin/fglrxinfo debian/fglrx/usr/lib/fglrx/bin/atieventsd debian/fglrx/usr/lib/fglrx/bin/fgl_glxgears debian/fglrx/usr/lib/fglrx/bin/atiode debian/fglrx/usr/lib/fglrx/bin/fglrx_xgamma debian/fglrx/usr/lib/fglrx/bin/atiodcli debian/fglrx/usr/lib/fglrx/bin/aticonfig debian/fglrx/usr/lib/fglrx/libaticalcl.so debian/fglrx/usr/lib/fglrx/libatiadlxx.so debian/fglrx/usr/lib/fglrx/libaticaldd.so debian/fglrx/usr/lib32/fglrx/libXvBAW.so.1.0 debian/fglrx/usr/lib32/fglrx/libGL.so.1.2 debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so debian/fglrx/usr/lib32/fglrx/libfglrx_gamma.so.1.0 debian/fglrx/usr/lib32/fglrx/libAMDXvBA.so.1.0 debian/fglrx/usr/lib32/fglrx/libaticalrt.so debian/fglrx/usr/lib32/fglrx/libfglrx_dm.so.1.0 debian/fglrx/usr/lib32/fglrx/libatiuki.so.1.0 debian/fglrx/usr/lib32/fglrx/libaticalcl.so debian/fglrx/usr/lib32/fglrx/libatiadlxx.so debian/fglrx/usr/lib32/fglrx/libaticaldd.so returned exit code 2
make[1]: *** [override_dh_shlibdeps] Error 9
make[1]: Leaving directory `/tmp/fglrx.Sa4Dod'
make: *** [binary] Error 2
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.GDmMzn

```

---

### Post by taurolyon on 2010-04-25
:confused:

---

### Post by taurolyon on 2010-04-25
no replies, so BUMP!

I'm completely stumped here. Barring a full re-install of Ubuntu, I have no clue how to fix it...

---

### Post by commandergc on 2010-04-25
You need to remove the driver and then re-install it.

---

### Post by jupraman on 2011-04-23
I'm having the exact same error for the radeon hd 4200.
Did a reinstall as suggested but to no avail.
Has anyone found a workaround?

---

### Post by chkneater on 2011-05-03
check wiki.cchtml.com/index/php and find your distro, and follow the instructions exactly.  Worked for my ATi 4850HD on AMD 64.

---

### Post by bobdotexe on 2011-12-21
> **chkneater said:**
> check wiki.cchtml.com/index/php and find your distro, and follow the instructions exactly.  Worked for my ATi 4850HD on AMD 64.

very helpful, but it's wiki.cchtml.com/index.php

and the ubuntu page is:
[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

Assuming your using 11.10:
[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide)

---

