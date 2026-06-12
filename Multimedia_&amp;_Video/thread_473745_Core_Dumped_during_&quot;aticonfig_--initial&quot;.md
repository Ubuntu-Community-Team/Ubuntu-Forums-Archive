---
title: "Core Dumped during &quot;aticonfig --initial&quot;"
date: 2007-06-14
forum: Multimedia &amp; Video
---

### Post by av011 on 2007-06-14
I have installed an ATI FireGL V7300 board on a workstation. running Ubuntu 7.04, Xorg 7.2.0.
Hardware: 2 x Opteron 2220, MOBO Supermicro H8DAE-2 with nvidia MCP55 PCI-E bridge, 16GB RAM.

From the ATI support website, I downloaded the ATI driver 8.37.6, which seems to be the only driver supporting Xorg 7.2.  I followed the express install and the installation seemed to go OK.  The log file is at the and of this message.  I then tried to run the initilal configuration "aticonfig --initial" and ended up with a core dump.  Please see below.  Any help would be greatly appreciated.

Many thanks in advance.
Achilles

------------------------------Output from "aticonfig --initial"----------------------------------------------------
$ sudo aticonfig --initial
Password:
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-1
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0x00007fffda692a3c ***
======= Backtrace: =========
/lib/libc.so.6(cfree+0x1b6)[0x2b70d1257396]
aticonfig[0x4148ed]
aticonfig[0x414849]
aticonfig[0x40c6e5]
aticonfig(XOpenDisplay+0x2bd)[0x402485]
aticonfig(XOpenDisplay+0x141)[0x402309]
/lib/libc.so.6(__libc_start_main+0xf4)[0x2b70d12018e4]
aticonfig(XOpenDisplay+0x62)[0x40222a]
======= Memory map: ========
00400000-00420000 r-xp 00000000 08:13 1441287                            /usr/bin/aticonfig
00520000-00526000 rw-p 00020000 08:13 1441287                            /usr/bin/aticonfig
00526000-00547000 rw-p 00526000 00:00 0                                  [heap]
2b70d0416000-2b70d0432000 r-xp 00000000 08:12 393231                     /lib/ld-2.5.so
2b70d0432000-2b70d0436000 rw-p 2b70d0432000 00:00 0 
2b70d0631000-2b70d0633000 rw-p 0001b000 08:12 393231                     /lib/ld-2.5.so
2b70d0633000-2b70d0639000 r-xp 00000000 08:13 557539                     /usr/lib/libXrandr.so.2.1.0
2b70d0639000-2b70d0839000 ---p 00006000 08:13 557539                     /usr/lib/libXrandr.so.2.1.0
2b70d0839000-2b70d083a000 rw-p 00006000 08:13 557539                     /usr/lib/libXrandr.so.2.1.0
2b70d083a000-2b70d0843000 r-xp 00000000 08:13 557491                     /usr/lib/libXrender.so.1.3.0
2b70d0843000-2b70d0a42000 ---p 00009000 08:13 557491                     /usr/lib/libXrender.so.1.3.0
2b70d0a42000-2b70d0a43000 rw-p 00008000 08:13 557491                     /usr/lib/libXrender.so.1.3.0
2b70d0a43000-2b70d0a53000 r-xp 00000000 08:13 557476                     /usr/lib/libXext.so.6.4.0
2b70d0a53000-2b70d0c53000 ---p 00010000 08:13 557476                     /usr/lib/libXext.so.6.4.0
2b70d0c53000-2b70d0c54000 rw-p 00010000 08:13 557476                     /usr/lib/libXext.so.6.4.0
2b70d0c54000-2b70d0d5a000 r-xp 00000000 08:13 557474                     /usr/lib/libX11.so.6.2.0
2b70d0d5a000-2b70d0f5a000 ---p 00106000 08:13 557474                     /usr/lib/libX11.so.6.2.0
2b70d0f5a000-2b70d0f61000 rw-p 00106000 08:13 557474                     /usr/lib/libX11.so.6.2.0
2b70d0f61000-2b70d0f62000 rw-p 2b70d0f61000 00:00 0 
2b70d0f62000-2b70d0fe3000 r-xp 00000000 08:12 393241                     /lib/libm-2.5.so
2b70d0fe3000-2b70d11e2000 ---p 00081000 08:12 393241                     /lib/libm-2.5.so
2b70d11e2000-2b70d11e4000 rw-p 00080000 08:12 393241                     /lib/libm-2.5.so
2b70d11e4000-2b70d132b000 r-xp 00000000 08:12 393237                     /lib/libc-2.5.so
2b70d132b000-2b70d152b000 ---p 00147000 08:12 393237                     /lib/libc-2.5.so
2b70d152b000-2b70d152e000 r--p 00147000 08:12 393237                     /lib/libc-2.5.so
2b70d152e000-2b70d1530000 rw-p 0014a000 08:12 393237                     /lib/libc-2.5.so
2b70d1530000-2b70d1535000 rw-p 2b70d1530000 00:00 0 
2b70d1535000-2b70d1537000 r-xp 00000000 08:13 557470                     /usr/lib/libXau.so.6.0.0
2b70d1537000-2b70d1736000 ---p 00002000 08:13 557470                     /usr/lib/libXau.so.6.0.0
2b70d1736000-2b70d1737000 rw-p 00001000 08:13 557470                     /usr/lib/libXau.so.6.0.0
2b70d1737000-2b70d1738000 rw-p 2b70d1737000 00:00 0 
2b70d1738000-2b70d173d000 r-xp 00000000 08:13 557472                     /usr/lib/libXdmcp.so.6.0.0
2b70d173d000-2b70d193c000 ---p 00005000 08:13 557472                     /usr/lib/libXdmcp.so.6.0.0
2b70d193c000-2b70d193d000 rw-p 00004000 08:13 557472                     /usr/lib/libXdmcp.so.6.0.0
2b70d193d000-2b70d193f000 r-xp 00000000 08:12 393240                     /lib/libdl-2.5.so
2b70d193f000-2b70d1b3f000 ---p 00002000 08:12 393240                     /lib/libdl-2.5.so
2b70d1b3f000-2b70d1b41000 rw-p 00002000 08:12 393240                     /lib/libdl-2.5.so
2b70d1b41000-2b70d1b43000 rw-p 2b70d1b41000 00:00 0 
2b70d1b43000-2b70d1b50000 r-xp 00000000 08:12 393230                     /lib/libgcc_s.so.1
2b70d1b50000-2b70d1d50000 ---p 0000d000 08:12 393230                     /lib/libgcc_s.so.1
2b70d1d50000-2b70d1d51000 rw-p 0000d000 08:12 393230   Aborted (core dumped)
--------------------------------------------------------------------------------------------------------------------

-------------------------Driver installation LOG file "fglrx-install.log"---------------------------------------
[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
 Assuming default VMAP API
 Assuming default munmap API
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
In file included from /lib/modules/fglrx/build_mod/2.6.x/drm_proc.h:41,
                 from /lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:334:
/lib/modules/fglrx/build_mod/2.6.x/drmP.h:126:1: warning: "DRM_DEBUG_CODE" redefined
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:178:1: warning: this is the location of the previous definition
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:452: warning: initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function ‘firegl_stub_open’:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:575: warning: assignment discards qualifiers from pointer target type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function ‘firegl_put_user_ptr’:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1388: warning: cast from pointer to integer of different size
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1388: warning: cast from pointer to integer of different size
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1388: warning: cast from pointer to integer of different size
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1388: warning: cast from pointer to integer of different size
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function ‘__ke_do_mmap’:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1885: warning: assignment makes pointer from integer without a cast
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function ‘__ke_request_irq’:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2638: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function ‘__ke_unregister_ioctl32_conversion’:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2661: warning: ‘return’ with a value, in function returning void
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: At top level:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:4897: warning: ‘kmem_cache_t’ is deprecated
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function ‘KAS_SlabCache_Initialize’:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:4938: warning: cast from pointer to integer of different size
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function ‘KAS_ExecuteAtLevel’:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:4756: warning: ‘flags’ may be used uninitialized in this function
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC4.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC4
  CC      /lib/modules/fglrx/build_mod/2.6.x/fglrx.mod.o
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
build succeeded with return value 0
duplicating results into driver repository...
done.
==============================
- recreating module dependency list
- trying a sample load of the kernel modules
done
-----------------------------------------------------------------------------------------------------------------------

---

### Post by IanW on 2007-06-14
I got this too. It seems this version of aticonfig is royally b0rked.

How I got the drivers working was to use Alberto Milone's "envy" program.
Find it [here.]("http://albertomilone.com/nvidia_scripts1.html")

If you still have the ati driver blob, ensure it is in your home directory, then download the envy.deb there too.
Install the deb, and run envy from your Applications/System Tools menu.

Envy should then see the driver blob, and start unpacking it instead of downloading another copy.

---

### Post by av011 on 2007-06-14
I followed this procedure but In my case, envy failed.  It maybe that something else is not configured correctly in my system.  Below is the log of the installation.  Something is strange because envy is trying to find lis /usr/x86_64-linux-gnu/lib64/, but that directory does not exist in my system.  It should be /usr/lib64, for r example.

Please take a look and let me know if you spot something obvious.

Thanks
Achilles

=============================================================
       +-----------------------------------------------------------+
       |    Envy Menu ver.0.9.5                                    |
       |                                                           |
       |    1 - Install the NVIDIA driver                          |
       |                                                           |
       |    2 - Uninstall the NVIDIA driver                        |
       |                                                           |
       |    3 - Install the ATI driver                             |
       |                                                           |
       |    4 - Uninstall the ATI driver                           |
       |                                                           |
       |    5 - Install the ATI/NVIDIA driver Manually             |
       |                                                           |
       |    6 - Clean the Installation of any Nvidia driver        |
       |                                                           |
       |    7 - Restart the Xserver                                |
       |                                                           |
       |    8 - Exit                                               |
       |                                                           |
       |    NOTE: IF THE SCREEN TURNS BLACK, PLEASE TYPE ALT+F1    |
       +-----------------------------------------------------------+
Please select one of the activities displayed above and press ENTER:

3
rm: cannot remove `*.deb': No such file or directory
Ubuntu Feisty 64bit
rm: cannot remove `/lib/linux-restricted-modules/.nvidia*': No such file or directory
Your graphic card has been detected as a ATI FireGL V7300
Your graphic card is supported by the latest driver
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.20-16-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx is not installed, so not removed
E: Couldn't find package nvidia-kernel-2.6.20-16-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-new is not installed, so not removed
E: Couldn't find package nvidia-new-kernel-2.6.20-16-generic
E: Invalid operation nvidia-new-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-legacy is not installed, so not removed
E: Couldn't find package nvidia-legacy-kernel-source
rm: cannot remove `/usr/src/nvidia*.deb': No such file or directory
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package fglrx-control
rm: cannot remove `/usr/src/fglrx*.deb': No such file or directory
rm: cannot remove `/usr/src/*.deb': No such file or directory
rm: cannot remove `/usr/src/modules/nvidia-kernel': No such file or directory
rm: cannot remove `/usr/src/modules/fglrx-kernel': No such file or directory
An installer has been detected
md5new: ebad4685199a9b3704237bc165de00d4
md5sumold: ebad4685199a9b3704237bc165de00d4
rm: cannot remove `/usr/src/fglrx-kernel*.deb': No such file or directory
Created directory fglrx-install.Bj8126
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.37.6..................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/feisty
Package build failed!
Package build utility output:
dpkg-buildpackage: source package is fglrx-installer
dpkg-buildpackage: source version is 8.37.6-1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
dpkg-buildpackage: host architecture amd64
dpkg-buildpackage: source version without epoch 8.37.6-1
 debian/rules build
make: Entering directory `/tmp/fglrx.dU8209'
echo "Using architecture: amd64"
Using architecture: amd64
if [ -f /tmp/fglrx.dU8209/debian/control.template ]; then \
                cat /tmp/fglrx.dU8209/debian/control.template > /tmp/fglrx.dU8209/debian/control; \
        fi
for i in preinst postinst postrm shlibs atieventsd.init ; do \
          if [ -f /tmp/fglrx.dU8209/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/feisty/" /tmp/fglrx.dU8209/debian/driver.$i > \
              /tmp/fglrx.dU8209/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx.dU8209/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
            /tmp/fglrx.dU8209/debian/10fglrx.template > /tmp/fglrx.dU8209/debian/10fglrx; \
        fi
if [ -f /tmp/fglrx.dU8209/debian/fglrx.default ]; then \
          mv /tmp/fglrx.dU8209/debian/fglrx.default /tmp/fglrx.dU8209/debian/fglrx; \
        fi
dh_testdir
dh_testdir
make: Leaving directory `/tmp/fglrx.dU8209'
 debian/rules binary
make: Entering directory `/tmp/fglrx.dU8209'
echo "Using architecture: amd64"
Using architecture: amd64
if [ -f /tmp/fglrx.dU8209/debian/control.template ]; then \
                cat /tmp/fglrx.dU8209/debian/control.template > /tmp/fglrx.dU8209/debian/control; \
        fi
for i in preinst postinst postrm shlibs atieventsd.init ; do \
          if [ -f /tmp/fglrx.dU8209/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/feisty/" /tmp/fglrx.dU8209/debian/driver.$i > \
              /tmp/fglrx.dU8209/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx.dU8209/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
            /tmp/fglrx.dU8209/debian/10fglrx.template > /tmp/fglrx.dU8209/debian/10fglrx; \
        fi
if [ -f /tmp/fglrx.dU8209/debian/fglrx.default ]; then \
          mv /tmp/fglrx.dU8209/debian/fglrx.default /tmp/fglrx.dU8209/debian/fglrx; \
        fi
dh_testdir
dh_testdir
dh_testdir
dh_testroot
dh_clean -k
rm -f /tmp/fglrx.dU8209/debian/control
sed -e 's/#XSERVER#/xorg/g' debian/control.template > /tmp/fglrx.dU8209/debian/control
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
                etc/X11/Xsession.d
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
                usr/src/modules/fglrx \
                usr/src/modules/fglrx/debian
dh_install
# Driver package
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/fgl*"      "usr/bin"
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/aticonfig" "usr/bin"
dh_install -pxorg-driver-fglrx "usr/sbin/atieventsd"     "usr/sbin"
dh_installman -pxorg-driver-fglrx "usr/share/man/man8/atieventsd.8.gz"
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
# Kernel source package
dh_install -pfglrx-kernel-source \
                lib/modules/fglrx/build_mod/*.c            \
                lib/modules/fglrx/build_mod/*.h            \
                lib/modules/fglrx/build_mod/*.sh           \
                lib/modules/fglrx/build_mod/lib*           \
                lib/modules/fglrx/build_mod/2.6.x/Makefile \
                usr/src/modules/fglrx
dh_install -pfglrx-kernel-source "debian/changelog" "usr/src/modules/fglrx/debian"
dh_install -pfglrx-kernel-source  \
                debian/copyright        \
                debian/compat           \
                module/rules            \
                module/control.template \
                module/dirs.template    \
                module/postinst         \
                usr/src/modules/fglrx/debian
(cd debian/fglrx-kernel-source/usr/src \
         && chown -R root:src modules \
         && tar -jcf fglrx.tar.bz2 modules \
         && rm -rf modules)
# control panel package
dh_install -A -pfglrx-amdcccle "usr/X11R6/bin/amdcccle"                         "usr/bin"
dh_install -A -pfglrx-amdcccle "usr/share/icons/*.xpm"                          "usr/share/icons"
dh_install -A -pfglrx-amdcccle "usr/share/icons/*.xpm"                          "usr/share/pixmaps"
dh_install -A -pfglrx-amdcccle "debian/amdcccle.desktop"                                "usr/share/applications"
dh_install -A -pfglrx-amdcccle "debian/amdcccle.kdelnk"                                 "usr/share/applnk"
dh_install -A -pfglrx-amdcccle "usr/share/ati"                                                  "usr/share"
dh_desktop    -pfglrx-amdcccle
# start the install
dh_installdocs
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/*
#dh_installchangelogs
dh_link
dh_strip
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/lib/libfglrx_tvout.so.1.0
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/lib/libfglrx_gamma.so.1.0
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/lib/libfglrx_pp.so.1.0
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/lib/dri/fglrx_dri.so
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/lib/xorg/modules/glesx.so
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/lib/xorg/modules/linux/libfglrxdrm.so
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/lib/xorg/modules/drivers/fglrx_drv.so
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/lib32/libGL.so.1.2
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/lib32/dri/fglrx_dri.so
+ /usr/bin/strip --remove-section=.comment --remove-section=.note debian/xorg-driver-fglrx/usr/sbin/atieventsd
+ /usr/bin/strip --remove-section=.comment --remove-section=.note debian/xorg-driver-fglrx/usr/bin/fglrxinfo
+ /usr/bin/strip --remove-section=.comment --remove-section=.note debian/xorg-driver-fglrx/usr/bin/fglrx_xgamma
+ /usr/bin/strip --remove-section=.comment --remove-section=.note debian/xorg-driver-fglrx/usr/bin/fgl_glxgears
+ /usr/bin/strip --remove-section=.comment --remove-section=.note debian/xorg-driver-fglrx/usr/bin/aticonfig
+ /usr/bin/strip --strip-debug debian/xorg-driver-fglrx-dev/usr/lib/libfglrx_gamma.a
+ /usr/bin/strip --strip-debug debian/xorg-driver-fglrx-dev/usr/lib/libfglrx_dm.a
+ /usr/bin/strip --strip-debug debian/xorg-driver-fglrx-dev/usr/lib/libfglrx_tvout.a
+ /usr/bin/strip --strip-debug debian/xorg-driver-fglrx-dev/usr/lib/libfglrx_pp.a
+ /usr/bin/strip --remove-section=.comment --remove-section=.note debian/fglrx-amdcccle/usr/bin/amdcccle
dh_compress
dh_makeshlibs
dh_installdeb
LD_PRELOAD= dh_shlibdeps
dpkg: /usr/x86_64-linux-gnu/lib64/libc.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libm.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libstdc++.so.5 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libpthread.so.0 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/librt.so.1 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libGL.so.1 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libdl.so.2 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libX11.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libXext.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libgcc_s.so.1 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libXrandr.so.2 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libXrender.so.1 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libm.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libstdc++.so.5 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libpthread.so.0 not found.
dpkg: /usr/x86_64-linux-gnu/lib/librt.so.1 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libGL.so.1 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libdl.so.2 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libX11.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libXext.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libc.so.6 not found.[/COLOR]
dpkg: /usr/x86_64-linux-gnu/lib64/libfglrx_gamma.so.1 not found.
dpkg-shlibdeps: failure: dpkg --search gave error exit status 1
dh_shlibdeps: command returned error code 256
make: *** [binary] Error 1
make: Leaving directory `/tmp/fglrx.dU8209'
Removing temporary directory: fglrx-install.Bj8126
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb
Getting source for kernel version: 2.6.20-16-generic
Kernel headers available in /lib/modules/2.6.20-16-generic/build
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Done!

Updated infos about 85 packages
The source tarball could not be found!
Package fglrx-kernel-src not installed?
Running "m-a -f get fglrx-kernel-src" may help.
find: /usr/src/modules: No such file or directory
rm: cannot remove `*.deb': No such file or directory
rm: cannot remove `*.changes': No such file or directory
Do you want to restart your computer now (Recommended)? (y/n) \ "y" is the default answer

======================================================================

---

