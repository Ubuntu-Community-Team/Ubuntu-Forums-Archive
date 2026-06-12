---
title: "Installing proprietary ati drivers"
date: 2011-05-15
forum: Multimedia Software
---

### Post by johncoss on 2011-05-15
Hi, I know that this question is asked many times (and many guides exists), but I simply can't do it.
When I installed Ubuntu it used freeware drivers then I used Additional Drivers program to install proprietary ATI drivers and it worked without any problems. I could run fancy UI effects for Gnome so it worked and glxgears worked good.
However, I wanted to test something (issues with playing videos) and I downloaded drivers from ATI site for my card and run ```
./ati-driver-installer-11-5-x86.x86_64.run
```
It seemed that some error occurred and after reboot GNOME was WAY TOOOOOOOOOOO SLOOOOW. I uninstalled using package manager and deactivated drivers using Additional Drivers program. Also I followed guide [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch) to fully purge ATI driver and install back xorg as default.
It works now and effects are back for UI, but they are not quick as with proprietary drivers, so I wanted to use Additional Drivers program to reactivate driver (it worked in first place), but it gived me installArchives failed error. I used apt-get to install fglrx but it fails too.
```
nomadsoulx@reborn:~$ sudo apt-get install fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libxt-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  fglrx-amdcccle
The following NEW packages will be installed:
  fglrx fglrx-amdcccle
0 upgraded, 2 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/25.1MB of archives.
After this operation, 75.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 163032 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.780-0ubuntu2_i386.deb) ...
/usr/share/ati/fglrx-uninstall.sh: 32: cannot create /etc/ati/fglrx-uninstall.log: Directory nonexistent

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the force option
 re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

dpkg: error processing /var/cache/apt/archives/fglrx_2%3a8.780-0ubuntu2_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.780-0ubuntu2_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx_2%3a8.780-0ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
I also tried to generate platform specific drivers for ATI using its installer but that fails also
```

Package build failed!
Package build utility output:
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.850-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.pw0a9K
dpkg-buildpackage: host architecture i386
 debian/rules build
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 fglrx.install \
			 fglrx-dev.install \
			 fglrx-amdcccle.install \
			 overrides/fglrx; do \
		sed -e "s|#XMODDIR#|usr/lib/fglrx/xorg/modules|"     \
			-e "s|#XMODDIR32#||" \
			-e "s|#PXPRESSXMODDIR#|usr/lib/pxpress/xorg/modules|" \
			-e "s|#DRIDIR32#|usr/lib32/fglrx|"   \
			-e "s|#LIBDIR#|lib|"       \
			-e "s|#DRIDIR#|usr/lib/fglrx|"       \
			-e "s|#PXPRESSDIR#|usr/lib/pxpress|" \
			-e "s|#PXPRESSLIBDIR#|usr/lib/pxpress/lib|" \
			-e "s|#PXPRESSLIBDIR32#|usr/lib32/pxpress/lib|" \
			-e "s|#CVERSION#|8.850|"   \
			-e "s|#XARCH#|xpic|"   \
			-e "s|#ARCH#|x86|"   \
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
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
		lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
		debian/modaliases/fglrx-modules.alias.override
# set the permissions on the pxpress scripts
chmod 744 debian/pxpress/switch*
dh build
   dh_testdir
   dh_auto_configure
   dh_auto_build
   dh_auto_test
 debian/rules binary
#Steps that we can't easily represent in debhelper files or .in files yet
# Remove any libraries that may be caught by shell expansion
find . -name libGLE* | xargs rm -f
find . -name libEGL* | xargs rm -f
dh_installdirs -pfglrx
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
			debian/fglrx/usr/lib/fglrx/*libGL.so.*.* \
			; do execstack -q $i; execstack -c $i; done
- debian/fglrx/usr/lib/fglrx/bin/atiode
- debian/fglrx/usr/lib/fglrx/bin/amdnotifyui
- debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so
- debian/fglrx/usr/lib/fglrx/fglrx-libGL.so.1.2
# Make some additional scripts executable
find debian/fglrx-amdcccle/usr/lib/fglrx/bin/ \
		-type f | xargs chmod a+x
# Rename libraries which are supposed to have fglrx-libGL as a prefix
for lib in `find debian/fglrx/ -name 'fglrx-libGL*'`; \
		do \
			file_name=`echo $lib | awk -F/ '{print $NF}'`; \
			path=`echo $lib | sed -e "s|\/$file_name|\/|"`; \
			# Remove fglrx prefix \
			new_name=`echo $file_name | sed -e "s|fglrx\-||"`; \
			full_path=`echo "$path$new_name"`; \
			mv -f $lib $full_path; \
	done
# Rename libraries which are supposed to have fglrx-libglx as a prefix
for lib in `find debian/fglrx/ -name 'fglrx-libglx*'`; \
		do \
			file_name=`echo $lib | awk -F/ '{print $NF}'`; \
			path=`echo $lib | sed -e "s|\/$file_name|\/|"`; \
			new_path=`echo $path | sed -e 's/fglrx\/$//'`; \
			# Remove fglrx prefix \
			new_name=`echo $file_name | sed -e "s|fglrx\-||"`; \
			full_path=`echo "$new_path$new_name"`; \
			mv -f $lib $full_path; \
	done
# Create links for PowerXpress X modules (except for extensions)
for i in \
		debian/fglrx/usr/lib/fglrx/xorg/modules/* \
		; do \
			orig_name=`echo $i  | sed -e "s|debian/fglrx/||"`; \
			if [ `echo $orig_name  | sed -e "s|usr/lib/fglrx/xorg/modules/||"` != "extensions" ]; then \
				link_name=$orig_name ; \
				link_name=`echo $orig_name  | sed -e "s|usr/lib/fglrx/xorg/modules|usr/lib/pxpress/xorg/modules|"`; \
				dh_link -pfglrx $orig_name $link_name ; \
			fi \
		done
# Create links for PowerXpress libs (except for libGL)
for i in \
		debian/fglrx/usr/lib/fglrx/* \
		; do \
			orig_name=`echo $i  | sed -e "s|debian/fglrx/||"`; \
			# Copy each file except for libGL* \
			if [ -f $i ]; then \
				if [ ! `echo $orig_name  | grep libGL` ]; then \
					link_name=$orig_name ; \
					link_name=`echo $orig_name  | sed -e "s|usr/lib/fglrx|usr/lib/pxpress/lib|"`; \
					dh_link -pfglrx $orig_name $link_name ; \
				fi \
			else \
				# Here we only accept the dri directory \
				dir_name=`echo $orig_name | awk -F/ '{print $NF}'`; \
				if [ "$dir_name" = "dri" ]; then \
					link_name=$orig_name ; \
					link_name=`echo $orig_name  | sed -e "s|usr/lib/fglrx|usr/lib/pxpress/lib|"`; \
					dh_link -pfglrx $orig_name $link_name ; \
				fi \
			fi \
		done
# Blacklist any other driver that udev may want to load instead of fglrx
printf "blacklist radeon\n" > /tmp/fglrx.pw0a9K/debian/fglrx/lib/fglrx/modprobe.conf
#ld.so.conf
echo "/usr/lib/fglrx" >	"/tmp/fglrx.pw0a9K/debian/fglrx/usr/lib/fglrx/ld.so.conf"
# ld.so.conf for PowerXpress
echo "/usr/lib/mesa" >		"/tmp/fglrx.pw0a9K/debian/fglrx/usr/lib/pxpress/ld.so.conf"
echo "/usr/lib/pxpress/lib" >>	"/tmp/fglrx.pw0a9K/debian/fglrx/usr/lib/pxpress/ld.so.conf"
#Run the normal stuff
dh binary-arch
   dh_testroot -a -Nfglrx -Nfglrx-amdcccle
   dh_prep -a -Nfglrx -Nfglrx-amdcccle
   dh_installdirs -a -Nfglrx -Nfglrx-amdcccle
   dh_auto_install -a -Nfglrx -Nfglrx-amdcccle
   dh_install -a -Nfglrx -Nfglrx-amdcccle
   dh_installdocs -a -Nfglrx
   dh_installchangelogs -a -Nfglrx
   dh_installexamples -a -Nfglrx
   dh_installman -a -Nfglrx
   dh_installcatalogs -a -Nfglrx
   dh_installcron -a -Nfglrx
   dh_installdebconf -a -Nfglrx
   dh_installemacsen -a -Nfglrx
   dh_installifupdown -a -Nfglrx
   dh_installinfo -a -Nfglrx
   dh_pysupport -a -Nfglrx
   dh_installinit -a -Nfglrx
Duplicate specification "O=s" for option "O"
   dh_installmenu -a -Nfglrx
   dh_installmime -a -Nfglrx
   dh_installmodules -a -Nfglrx
   dh_installlogcheck -a -Nfglrx
   dh_installlogrotate -a -Nfglrx
   dh_installpam -a -Nfglrx
   dh_installppp -a -Nfglrx
   dh_installudev -a -Nfglrx
   dh_installwm -a -Nfglrx
   dh_installxfonts -a -Nfglrx
   dh_bugfiles -a -Nfglrx
   dh_lintian -a -Nfglrx
   dh_gconf -a -Nfglrx
   dh_icons -a -Nfglrx
   dh_perl -a -Nfglrx
   dh_usrlocal -a -Nfglrx
   dh_link -a -Nfglrx
   dh_compress -a
   dh_fixperms -a
   dh_strip -a
   dh_makeshlibs -a
objdump: debian/fglrx/usr/lib/fglrx/ld.so.conf: File format not recognized
objdump: debian/fglrx/usr/lib/pxpress/ld.so.conf: File format not recognized
   debian/rules override_dh_shlibdeps
make[1]: Entering directory `/tmp/fglrx.pw0a9K'
dh_shlibdeps -l/tmp/fglrx.pw0a9K/debian/fglrx/usr/lib/fglrx
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 contains an unresolvable reference to symbol dlsym: it's probably a plugin.
dpkg-shlibdeps: warning: 23 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/bin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libGL.so.1.2 contains an unresolvable reference to symbol XOpenDisplay: it's probably a plugin.
dpkg-shlibdeps: warning: 30 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: error: no dependency information found for /usr/share/ati/lib/libQtGui.so.4 (used by debian/fglrx/usr/lib/fglrx/bin/amdnotifyui).
dh_shlibdeps: dpkg-shlibdeps -Tdebian/fglrx.substvars debian/fglrx/usr/lib/fglrx/libaticalcl.so debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so debian/fglrx/usr/lib/fglrx/libfglrx_dm.so.1.0 debian/fglrx/usr/lib/fglrx/libaticaldd.so debian/fglrx/usr/lib/fglrx/libaticalrt.so debian/fglrx/usr/lib/fglrx/libGL.so.1.2 debian/fglrx/usr/lib/fglrx/bin/atieventsd debian/fglrx/usr/lib/fglrx/bin/atiodcli debian/fglrx/usr/lib/fglrx/bin/fglrxinfo debian/fglrx/usr/lib/fglrx/bin/amdnotifyui debian/fglrx/usr/lib/fglrx/bin/atiode debian/fglrx/usr/lib/fglrx/bin/aticonfig debian/fglrx/usr/lib/fglrx/bin/fgl_glxgears debian/fglrx/usr/lib/fglrx/xorg/modules/linux/libfglrxdrm.so debian/fglrx/usr/lib/fglrx/xorg/modules/glesx.so debian/fglrx/usr/lib/fglrx/xorg/modules/amdxmm.so debian/fglrx/usr/lib/fglrx/xorg/modules/extensions/libglx.so debian/fglrx/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so debian/fglrx/usr/lib/fglrx/libXvBAW.so.1.0 debian/fglrx/usr/lib/fglrx/libatiuki.so.1.0 debian/fglrx/usr/lib/fglrx/libatiadlxx.so returned exit code 2
make[1]: *** [override_dh_shlibdeps] Error 9
make[1]: Leaving directory `/tmp/fglrx.pw0a9K'
make: *** [binary-arch] Error 2
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
[Error] Generate Package - error generating package : Ubuntu/maverick

```
Sorry for long post but I really want to get this fixed. If is possible I would like to restore driver that system installed for me when I used Additional Drivers dialog.
Thanks in advance!

---

### Post by slooksterpsv on 2011-05-15
I've ran into this issue before, with the fglrx do this:

sudo apt-get purge fglrx fglrx-amdcccle

Then I had to find where the drivers were and remove them:
sudo rm -R /lib/usr/fglrx
sudo rm -R /lib/fglrx
sudo rm -R /usr/share/doc/fglrx

Reboot then: 
sudo apt-get install fglrx && sudo aticonfig --initial -f

Reboot again.

That's when I installed the .run package by AMD. I keep thinking there was one other area...

---

### Post by johncoss on 2011-05-16
Hi slooksterpsv,

I managed to install proprietary drivers at last. I followed your instructions for removing fglrx. Fglrx packages were already removed so first apt-get was not needed for me.
Later I searched for fglrx in my system using
```
locate fglrx
```
I removed fglrx from certain directories (keep in mind that there is not /lib/usr folder :))
```
sudo rm -R /usr/lib/fglrx
sudo rm -R /usr/share/ati

```
After this I tried 
```
sudo apt-get install fglrx
```
It passed without problems (finally), but after reboot system was not using ati drivers. I tried aticonfig but simply there was no such application. I used then Additional Drivers program to activate proprietary drivers and it worked without any problems!! Driver is installed and I run
```
sudo aticonfig --initial
```
to finish installation.
Now it works :D
Thanks!!

---

