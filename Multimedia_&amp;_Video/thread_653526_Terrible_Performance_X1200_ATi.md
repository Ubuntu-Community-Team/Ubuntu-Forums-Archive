---
title: "Terrible Performance X1200 ATi"
date: 2007-12-30
forum: Multimedia &amp; Video
---

### Post by nsegative on 2007-12-30
Hey guys. My friend has a toshiba A215 laptop with an amd x2 (1.6 ghz), 1 gig of ram and ati X1200. The thing is after installing the needed drivers (xorg fglrx drivers) from admin section and rebooting it's abysmally slow (compiz fusion is enabled). Like changing work places seems lagish, firefox scrolling lags and many affects completely freeze up for a second (like minimize beam up). I tried installing 7.12 ati drivers on his laptop (followed the guide completely, installed needed build packages, uninstalled proprietary drivers) but I get this:
```
Created directory fglrx-install.Wm5781
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.443.1.......................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/gutsy
Package build failed!
Package build utility output:
dpkg-buildpackage: source package is fglrx-installer
dpkg-buildpackage: source version is 8.443.1-1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 8.443.1-1
 debian/rules build
echo "Using architecture: i386"
Using architecture: i386
if [ -f /tmp/fglrx.OF5862/debian/control.template ]; then \
                cat /tmp/fglrx.OF5862/debian/control.template > /tmp/fglrx.OF5862/debian/control; \
        fi
for i in preinst postinst postrm shlibs atieventsd.init ; do \
          if [ -f /tmp/fglrx.OF5862/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/gutsy/" /tmp/fglrx.OF5862/debian/driver.$i > \
              /tmp/fglrx.OF5862/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx.OF5862/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
            /tmp/fglrx.OF5862/debian/10fglrx.template > /tmp/fglrx.OF5862/debian/10fglrx; \
        fi
if [ -f /tmp/fglrx.OF5862/debian/fglrx.default ]; then \
          mv /tmp/fglrx.OF5862/debian/fglrx.default /tmp/fglrx.OF5862/debian/fglrx; \
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
find: usr/X11R6/lib64: No such file or directory
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
dh_testdir
 debian/rules binary
echo "Using architecture: i386"
Using architecture: i386
if [ -f /tmp/fglrx.OF5862/debian/control.template ]; then \
                cat /tmp/fglrx.OF5862/debian/control.template > /tmp/fglrx.OF5862/debian/control; \
        fi
for i in preinst postinst postrm shlibs atieventsd.init ; do \
          if [ -f /tmp/fglrx.OF5862/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/gutsy/" /tmp/fglrx.OF5862/debian/driver.$i > \
              /tmp/fglrx.OF5862/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx.OF5862/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
            /tmp/fglrx.OF5862/debian/10fglrx.template > /tmp/fglrx.OF5862/debian/10fglrx; \
        fi
if [ -f /tmp/fglrx.OF5862/debian/fglrx.default ]; then \
          mv /tmp/fglrx.OF5862/debian/fglrx.default /tmp/fglrx.OF5862/debian/fglrx; \
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
find: usr/X11R6/lib64: No such file or directory
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
dh_testdir
dh_testdir
dh_testroot
dh_clean -k
rm -f /tmp/fglrx.OF5862/debian/control
sed -e 's/#XSERVER#/xorg/g' debian/control.template > /tmp/fglrx.OF5862/debian/control
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs
cd: 15: can't cd to ieee80211
cp: target `/lib/modules/2.6.22-14-generic/madwifi/wlan_scan_ap.ko' is not a directory
cd: 15: can't cd to rtl8187
cp: target `/lib/modules/2.6.22-14-generic/madwifi/wlan_scan_ap.ko' is not a directory
cd: 15: can't cd to ieee80211
cp: target `/lib/modules/2.6.22-14-generic/madwifi/wlan_scan_ap.ko' is not a directory
cd: 15: can't cd to rtl8187
cp: target `/lib/modules/2.6.22-14-generic/madwifi/wlan_scan_ap.ko' is not a directory
cd: 15: can't cd to ieee80211
cp: target `/lib/modules/2.6.22-14-generic/madwifi/wlan_scan_ap.ko' is not a directory
cd: 15: can't cd to rtl8187
cp: target `/lib/modules/2.6.22-14-generic/madwifi/wlan_scan_ap.ko' is not a directory
cd: 15: can't cd to ieee80211
cp: target `/lib/modules/2.6.22-14-generic/madwifi/wlan_scan_ap.ko' is not a directory
cd: 15: can't cd to rtl8187
cp: target `/lib/modules/2.6.22-14-generic/madwifi/wlan_scan_ap.ko' is not a directory
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
                etc/xdg/compiz
cd: 15: can't cd to ieee80211
cp: target `/lib/modules/2.6.22-14-generic/madwifi/wlan_scan_ap.ko' is not a directory
cd: 15: can't cd to rtl8187
cp: target `/lib/modules/2.6.22-14-generic/madwifi/wlan_scan_ap.ko' is not a directory
cd: 15: can't cd to ieee80211
cp: target `/lib/modules/2.6.22-14-generic/madwifi/wlan_scan_ap.ko' is not a directory
cd: 15: can't cd to rtl8187
cp: target `/lib/modules/2.6.22-14-generic/madwifi/wlan_scan_ap.ko' is not a directory
dh_installdirs -A -pxorg-driver-fglrx \
                usr/bin \
                usr/sbin \
                usr/share \
                usr/share/applnk \
                usr/share/gnome \
                usr/share/gnome/apps \
                usr/share/icons \
                usr/share/pixmaps
cd: 15: can't cd to ieee80211
cp: target `/lib/modules/2.6.22-14-generic/madwifi/wlan_scan_ap.ko' is not a directory
cd: 15: can't cd to rtl8187
cp: target `/lib/modules/2.6.22-14-generic/madwifi/wlan_scan_ap.ko' is not a directory
cd: 15: can't cd to ieee80211
cp: target `/lib/modules/2.6.22-14-generic/madwifi/wlan_scan_ap.ko' is not a directory
cd: 15: can't cd to rtl8187
cp: target `/lib/modules/2.6.22-14-generic/madwifi/wlan_scan_ap.ko' is not a directory
dh_installdirs -pxorg-driver-fglrx-dev \
                usr/include \
                usr/lib
cd: 15: can't cd to ieee80211
cp: target `/lib/modules/2.6.22-14-generic/madwifi/wlan_scan_ap.ko' is not a directory
cd: 15: can't cd to rtl8187
cp: target `/lib/modules/2.6.22-14-generic/madwifi/wlan_scan_ap.ko' is not a directory
cd: 15: can't cd to ieee80211
cp: target `/lib/modules/2.6.22-14-generic/madwifi/wlan_scan_ap.ko' is not a directory
cd: 15: can't cd to rtl8187
cp: target `/lib/modules/2.6.22-14-generic/madwifi/wlan_scan_ap.ko' is not a directory
dh_installdirs -pfglrx-kernel-source \
                usr/src/fglrx-8.443.1 
cd: 15: can't cd to ieee80211
cp: target `/lib/modules/2.6.22-14-generic/madwifi/wlan_scan_ap.ko' is not a directory
cd: 15: can't cd to rtl8187
cp: target `/lib/modules/2.6.22-14-generic/madwifi/wlan_scan_ap.ko' is not a directory
cd: 15: can't cd to ieee80211
cp: target `/lib/modules/2.6.22-14-generic/madwifi/wlan_scan_ap.ko' is not a directory
cd: 15: can't cd to rtl8187
cp: target `/lib/modules/2.6.22-14-generic/madwifi/wlan_scan_ap.ko' is not a directory
dh_install
# Driver package
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/fgl*"      "usr/bin"
cd: 15: can't cd to ieee80211
cp: target `/lib/modules/2.6.22-14-generic/madwifi/wlan_scan_ap.ko' is not a directory
cd: 15: can't cd to rtl8187
cp: target `/lib/modules/2.6.22-14-generic/madwifi/wlan_scan_ap.ko' is not a directory
cp: target `debian/xorg-driver-fglrx/usr/bin/' is not a directory: No such file or directory
dh_install: command returned error code 256
make: *** [binary] Error 1
Removing temporary directory: fglrx-install.Wm5781


```
and xorg.conf gives me this (direct rendering says no and there seems to be no way to enable it).
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection

```

Strangely my friends old laptop (1.6 ghz, intel 945GM card and 512 ram) runs completely smooth as butter. This is gutsy 7.10 Thanks for any help!

---

### Post by intel on 2008-01-02
unfortunately there are known issues with both compiz & fglrx,

your friend can post for install help here
[https://groups.google.com/group/x1250](https://groups.google.com/group/x1250)

How to install latest fglrx on ATI Radeon X1200 RS690
[https://groups.google.com/group/x1250/web/drivers4linux](https://groups.google.com/group/x1250/web/drivers4linux)

---

### Post by nsegative on 2008-01-03
Thanks! Will take a look.

---

