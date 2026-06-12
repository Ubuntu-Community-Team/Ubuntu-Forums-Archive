---
title: "Problem with catalyst 8.4 and Ubuntu 8.04"
date: 2008-05-07
forum: Multimedia Software
---

### Post by SledgeHammer_999 on 2008-05-07
OS:Ubuntu 8.04 64-bit
GPU: x1800xl 256MB
command:```
sudo sh ati-driver-installer-8-4-x86.x86_64.run --buildpkg Ubuntu/hardy
```

error: ```
Generating package: Ubuntu
Automatically detected hardy
Package build failed!
Package build utility output:
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.476-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture amd64
echo "Using architecture: amd64"
Using architecture: amd64
for i in preinst postinst postrm shlibs atieventsd.init ; do \
	  if [ -f /tmp/fglrx.N16779/debian/driver.$i ]; then \
	    sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
	        -e "s/#DISTRO#/hardy/" /tmp/fglrx.N16779/debian/driver.$i > \
	      /tmp/fglrx.N16779/debian/xorg-driver-fglrx.$i; \
	  fi; \
	done
if [ -f /tmp/fglrx.N16779/debian/10fglrx.template ]; then \
	  sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
	    /tmp/fglrx.N16779/debian/10fglrx.template > /tmp/fglrx.N16779/debian/10fglrx; \
	fi
if [ -f /tmp/fglrx.N16779/debian/fglrx.default ]; then \
	  mv /tmp/fglrx.N16779/debian/fglrx.default /tmp/fglrx.N16779/debian/fglrx; \
	fi
dh_testdir
dh_testdir
# move licenses away from binary dir
if [ ! -d usr/share/doc/fglrx ]; then \
		mkdir -p usr/share/doc/fglrx; \
		mv usr/X11R6/bin/LICENSE.* usr/share/doc/fglrx; \
	fi
# set executable on user apps
find usr/X11R6/bin -type f | xargs chmod a+x
# remove exec bit from files that don't deserve it
find usr/X11R6/include \
		usr/X11R6/lib \
		usr/X11R6/lib64 \
		usr/share usr/src     -type f | xargs chmod -x
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
# remove exec bit from 64-bit libs too
find usr/X11R6/lib64       -type f | xargs chmod -x
dh_testdir
 debian/rules binary
echo "Using architecture: amd64"
Using architecture: amd64
for i in preinst postinst postrm shlibs atieventsd.init ; do \
	  if [ -f /tmp/fglrx.N16779/debian/driver.$i ]; then \
	    sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
	        -e "s/#DISTRO#/hardy/" /tmp/fglrx.N16779/debian/driver.$i > \
	      /tmp/fglrx.N16779/debian/xorg-driver-fglrx.$i; \
	  fi; \
	done
if [ -f /tmp/fglrx.N16779/debian/10fglrx.template ]; then \
	  sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
	    /tmp/fglrx.N16779/debian/10fglrx.template > /tmp/fglrx.N16779/debian/10fglrx; \
	fi
if [ -f /tmp/fglrx.N16779/debian/fglrx.default ]; then \
	  mv /tmp/fglrx.N16779/debian/fglrx.default /tmp/fglrx.N16779/debian/fglrx; \
	fi
dh_testdir
dh_testdir
# move licenses away from binary dir
if [ ! -d usr/share/doc/fglrx ]; then \
		mkdir -p usr/share/doc/fglrx; \
		mv usr/X11R6/bin/LICENSE.* usr/share/doc/fglrx; \
	fi
# set executable on user apps
find usr/X11R6/bin -type f | xargs chmod a+x
# remove exec bit from files that don't deserve it
find usr/X11R6/include \
		usr/X11R6/lib \
		usr/X11R6/lib64 \
		usr/share usr/src     -type f | xargs chmod -x
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
# remove exec bit from 64-bit libs too
find usr/X11R6/lib64       -type f | xargs chmod -x
dh_testdir
dh_testdir
dh_testroot
dh_clean -k
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs
# Create the directories to install into
dh_installdirs -pxorg-driver-fglrx \
		usr/lib \
		usr/sbin \
		usr/lib \
		usr/lib/xorg/modules \
		usr/lib/xorg/modules/drivers \
		usr/lib/xorg/modules/linux \
		etc/acpi \
		etc/acpi/events \
		etc/default \
		etc/X11/Xsession.d \

# the amd64 package includes 32bit compatibility libraries
dh_installdirs -pxorg-driver-fglrx \
		usr/lib32 \
		usr/lib32
dh_installdirs -A -pxorg-driver-fglrx \
		usr/bin \
		usr/sbin \
		usr/share \
		usr/share/applnk \
		usr/share/gnome \
		usr/share/gnome/apps \
		usr/share/icons \
		usr/share/pixmaps
dh_installdirs -pxorg-driver-fglrx-dev \
		usr/include \
		usr/lib
dh_installdirs -pfglrx-kernel-source \
		usr/src/fglrx-8.476
dh_install
# Driver package
/sbin/ldconfig -n usr/X11R6/lib/
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/fgl*"      "usr/bin"
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/aticonfig" "usr/bin"
dh_install -pxorg-driver-fglrx "usr/sbin/atieventsd"     "usr/sbin"
dh_installman -pxorg-driver-fglrx "usr/share/man/man8/atieventsd.8"
# amd64 needs some library redirection
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/*.so*"           "usr/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/dri"     "usr/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/linux"   "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/drivers" "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/*.so"    "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/*.a"     "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/*.so*"           "usr/lib32"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/modules/dri"     "usr/lib32"
dh_install -pxorg-driver-fglrx "etc/ati"                   "etc"
dh_install -pxorg-driver-fglrx "debian/10fglrx"            "etc/X11/Xsession.d"
dh_install -pxorg-driver-fglrx "debian/fglrx-powermode.sh" "etc/acpi"
dh_install -pxorg-driver-fglrx "debian/fglrx-*-aticonfig"  "etc/acpi/events"
dh_install -pxorg-driver-fglrx "debian/fglrx"              "etc/default"
dh_installinit -pxorg-driver-fglrx --name="atieventsd"
# Driver dev package
dh_install -pxorg-driver-fglrx-dev "usr/X11R6/lib64/*.a" "usr/lib"
dh_install -pxorg-driver-fglrx-dev "usr/X11R6/include/*" "usr/include"
dh_install -pxorg-driver-fglrx-dev "usr/include/*"       "usr/include"
#Create dkms.conf
echo "PACKAGE_NAME=\"fglrx\"" > debian/dkms.conf
echo "PACKAGE_VERSION=\"8.476\"" >> debian/dkms.conf
echo "CLEAN=\"rm -f *.*o\"" >> debian/dkms.conf
echo "BUILT_MODULE_NAME[0]=\"fglrx\"" >> debian/dkms.conf
echo "MAKE[0]=\"pushd \${dkms_tree}/fglrx/8.476/build; sh make.sh --nohints; popd\"" >> debian/dkms.conf
echo "DEST_MODULE_LOCATION[0]=\"/kernel/drivers/char/drm\"" >> debian/dkms.conf
echo "AUTOINSTALL=\"yes\"" >> debian/dkms.conf
# Kernel source package
dh_install -pfglrx-kernel-source \
		lib/modules/fglrx/build_mod/*.c            \
		lib/modules/fglrx/build_mod/*.h            \
		lib/modules/fglrx/build_mod/*.sh           \
		lib/modules/fglrx/build_mod/lib*           \
		lib/modules/fglrx/build_mod/2.6.x/Makefile \
		debian/dkms.conf			   \
		usr/src/fglrx-8.476
# control panel package
dh_install -A -pfglrx-amdcccle "usr/X11R6/bin/amdcccle"				"usr/bin"
dh_install -A -pfglrx-amdcccle "usr/share/icons/*.xpm"				"usr/share/icons"
dh_install -A -pfglrx-amdcccle "usr/share/icons/*.xpm"				"usr/share/pixmaps"
dh_install -A -pfglrx-amdcccle "debian/amdcccle.desktop"			"usr/share/applications"
dh_install -A -pfglrx-amdcccle "debian/amdcccle.kdelnk"				"usr/share/applnk"
dh_install -A -pfglrx-amdcccle "usr/share/ati"					"usr/share"
dh_desktop    -pfglrx-amdcccle
# start the install
dh_installdocs
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/*
#dh_installchangelogs
dh_link
dh_strip
dh_compress
dh_installdeb
dh_makeshlibs
dh_shlibdeps
dpkg-shlibdeps: warning: symbol XauFileName used by debian/xorg-driver-fglrx/usr/sbin/atieventsd found in none of the libraries.
dpkg-shlibdeps: warning: debian/xorg-driver-fglrx/usr/sbin/atieventsd shouldn't be linked with libXrender.so.1 (it uses none of its symbols).
dpkg-shlibdeps: failure: couldn't find library libfglrx_gamma.so.1 needed by debian/xorg-driver-fglrx/usr/bin/fglrx_xgamma (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: command returned error code 512
make: *** [binary] Error 1
dpkg-buildpackage: failure: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.M16692
```


How do I fix it? (the same drivers compiled fine on gutsy)

thank you in advance

---

### Post by SledgeHammer_999 on 2008-05-07
bump

---

### Post by Gumper on 2008-05-15
I'm having the same problem. Have you been successful in resolving this?

---

### Post by SledgeHammer_999 on 2008-05-15
nope. I am just waiting for the new release this month(maybe this week). Hopefully it will be solved in the new release.

---

### Post by peakshysteria on 2008-05-23
Same issue in my end with the new 8.5 driver.

[http://ubuntuforums.org/showthread.php?t=789641&page=2](http://ubuntuforums.org/showthread.php?t=789641&page=2)
:confused:

---

### Post by SledgeHammer_999 on 2008-05-23
I don't know about you guys but I have the same problem with new drivers(8.5)

Is this specific to 64-bit?

---

### Post by SledgeHammer_999 on 2008-05-23
I found 2 solutions:

**Solution A:**

Instead of ```
sudo sh ati-driver-installer-8-5-x86.x86_64.run --buildpkg Ubuntu/hardy
```
Use ```
sudo sh ati-driver-installer-8-5-x86.x86_64.run --buildpkg Ubuntu/8.04
```

**Solution B:**

doing little googling and found a solution:

Extract the archive and navigate to the new folder:
```

sudo sh ati-driver-installer-8-5-x86.x86_64.run --extract driver
cd driver

```

Navigate to where the libs are for 64 bit and make a symlink
```

cd arch/x86_64/usr/X11R6/lib64
ln -s libfglrx_gamma.so.1.0 libfglrx_gamma.so.1

```

Build the package(the command doesn't contain errors the script just behaves wrongly):
```

cd ../
sudo sh ati-installer.sh -- --buildpkg Ubuntu/hardy

```

It built the packages and they installed. But after reboot the monitor goes black. I switch to a console, login and do a "dmesg|grep fglrx". 5-10 lines come up and they that the driver is loaded and working!!!

I found the solution for that too. But for me is a bit strange:

```

sudo modprobe -r radeon
sudo modprobe fglrx

```

I restarted X and it worked!!! And I only had to do it once(why?!?!?)
But I have another problem:
It displayed everything in 1920*1080. My monitor's manual says that it can go only up to 1024*768. Even the Catalyst for Windows recognize it up to 1024*768. Even older versions of Linux catalyst.

What lines should I put to my xorg.conf file to limit the available resolutions to 1024*768?

---

### Post by peakshysteria on 2008-05-23
```
gksudo displayconfig-gtk
``` and set the proper resolution. I had the same problem after a clean install.

And thanks for a possible solution to the error. I'll check it out. Not sure i dare go there since I'm a bit on tin ice when it comes to the terminal.

Edit: couldn't keep away. Had to try but didn't make it this time either.

> Extract the archive and navigate to the new folder:
Code:

```
sudo sh ati-driver-installer-8-5-x86.x86_64.run --extract driver
cd driver

```
Navigate to where the libs are for 64 bit and make a symlink
Code:
```

cd arch/x86_64/usr/X11R6/lib64
ln -s libfglrx_gamma.so.1.0 libfglrx_gamma.so.1

```
Build the package(the command doesn't contain errors the script just behaves wrongly):
Code:
```

cd ../
sudo sh ati-installer -- --buildpkg Ubuntu/hardy 

```


It fails on this last command saying: sh: Can't open ati-installer

---

### Post by SledgeHammer_999 on 2008-05-23
sorry my bad.

```

sudo sh ati-installer.sh -- --buildpkg Ubuntu/hardy

```

---

### Post by peakshysteria on 2008-05-23
I get the same problem with both sudo sh ati-installer.sh -- --buildpkg Ubuntu/hardy and sudo sh ati-installer -- --buildpkg Ubuntu/hardy:

sh: Can't open ati-installer.sh

---

### Post by SledgeHammer_999 on 2008-05-23
I know where the problem is now, another mistake by me-> you are not in the correct folder:

```

cd /home/<username>/driver
sudo sh ati-installer.sh -- --buildpkg Ubuntu/hardy

```

replace <username> with your username

---

### Post by Jiskefet on 2008-05-23
Before you enter and execute the command, you need to make sure you are in the correct directory. Type cd ../ and Enter until yo are back in the .../driver dir.

---

### Post by peakshysteria on 2008-05-24
Thanks a lot everybody. With this last post (ehich I haven't tried yet) i think it's there actually. But I'll give it a rest for now. Used the best part of yesterday to figure this thing out. Spent the night getting my resolution back (which is the downside every time I try this and fail). As soon as I make it I'll post back here. Thanks again guys.

---

### Post by SledgeHammer_999 on 2008-05-24
I found an easier solution. See my updated post.

---

