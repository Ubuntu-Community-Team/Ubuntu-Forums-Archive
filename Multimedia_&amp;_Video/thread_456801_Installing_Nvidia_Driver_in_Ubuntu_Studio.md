---
title: "Installing Nvidia Driver in Ubuntu Studio"
date: 2007-05-28
forum: Multimedia &amp; Video
---

### Post by txdmb on 2007-05-28
Hey, all I'm a bit of a Linux Noob. I've used envy to install the Nvidia driver in 7.04, but when I use it to install in Envy it just crashes my Xserver on reboot. What do I need to do to install the Nvidia driver in Studio? I have onboard Geforce 6100. Thanks for any help.

E

---

### Post by tseliot on 2007-05-28
can you post your /var/log/envy-installer.log ?

---

### Post by txdmb on 2007-05-28
Hmm, I'll try..

---

### Post by txdmb on 2007-05-28
Ok, I just reinstalled Studio, updated, and ran envy. I haven't restarted yet, because I don't really know how to do anything once the Xserver crashes. But here is the log, thanks for any help.


python pulse.py nvidia 
root@Esemp:/usr/share/envy# python pulse.py nvidia
Ubuntu Feisty 32bit
Your graphic card has been detected as a GeForce 6100
Your graphic card is supported by the latest driver
rm: cannot remove `/lib/linux-restricted-modules/.nvidia*': No such file or directory
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.20-15-generic linux-headers-2.6.20-15
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  linux-headers-2.6.20-16-lowlatency
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 841kB of archives.
After unpacking 7229kB of additional disk space will be used.
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main linux-headers-2.6.20-16-lowlatency 2.6.20-16.28 [841kB]
Fetched 841kB in 2s (410kB/s)                              
Selecting previously deselected package linux-headers-2.6.20-16-lowlatency.
(Reading database ... 132131 files and directories currently installed.)
Unpacking linux-headers-2.6.20-16-lowlatency (from .../linux-headers-2.6.20-16-lowlatency_2.6.20-16.28_i386.deb) ...
Setting up linux-headers-2.6.20-16-lowlatency (2.6.20-16.28) ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx is not installed, so not removed
E: Couldn't find package nvidia-kernel-2.6.20-16-lowlatency
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-new is not installed, so not removed
E: Couldn't find package nvidia-new-kernel-2.6.20-16-lowlatency
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-legacy is not installed, so not removed
Package nvidia-legacy-kernel-source is not installed, so not removed
Package nvidia-settings is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.20-15-generic linux-headers-2.6.20-15
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rm: cannot remove `/usr/src/nvidia*.deb': No such file or directory
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package fglrx-control is not installed, so not removed
E: Couldn't find package fglrx-kernel-2.6.20-16-lowlatency
rm: cannot remove `/usr/src/fglrx*.deb': No such file or directory
rm: cannot remove `/usr/src/*.deb': No such file or directory
rm: cannot remove `/usr/src/modules/nvidia-kernel': No such file or directory
rm: cannot remove `/usr/src/modules/fglrx-kernel': No such file or directory
An installer has been detected
md5new: d41d8cd98f00b204e9800998ecf8427e
md5sumold: 6e51f092653c4a67037e9893c1c4a71f
ENVY ERROR: md5 Error! Trying to fetch the driver from the website
No installer detected
Download of the driver in progress, please wait
--16:53:26--  [http://us.download.nvidia.com/XFree86/Linux-x86/100.14.03/NVIDIA-Linux-x86-100.14.03-pkg0.run](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.03/NVIDIA-Linux-x86-100.14.03-pkg0.run)
           => `NVIDIA-Linux-x86-100.14.03-pkg0.run'
Resolving us.download.nvidia.com... 72.247.30.209, 72.247.30.168
Connecting to us.download.nvidia.com|72.247.30.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7,840,057 (7.5M) [application/octet-stream]
100%[====================================>] 7,840,057    587.53K/s    ETA 00:00

16:53:43 (463.10 KB/s) - `NVIDIA-Linux-x86-100.14.03-pkg0.run' saved [7840057/7840057]

md5new: 6e51f092653c4a67037e9893c1c4a71f
md5sumold: 6e51f092653c4a67037e9893c1c4a71f
dpkg-buildpackage: source package is nvidia-graphics-drivers
dpkg-buildpackage: source version is 1:100.14.05
dpkg-buildpackage: source changed by Alberto Milone (tseliot) <albertomilone@alice.it>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 100.14.05
debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp build-kernel-stamp configure-stamp
dh_clean
rm -fr NVIDIA-Linux-x86-100.14.03-pkg0  nvidia-kernel-source.tar.gz
 debian/rules build
rm -f debian/nvidia-kernel-source.README.Debian debian/control debian/copyright debian/nvidia-glx.links debian/nvidia-glx-dev.links debian/nvidia-glx.override debian/nvidia-glx.docs debian/nvidia-glx.examples debian/nvidia-glx.postrm debian/nvidia-glx.init debian/nvidia-glx-ia32.override debian/nvidia-glx-ia32.links debian/nvidia-kernel-source.docs debian/nvidia-glx-dev.preinst || true
perl -p \
        -e 's{#BASE_VERSION#}{}g;' \
        -e 's{#RELEASE#}{100.14.03}g;' \
        -e 's{#VERSION#}{100.14.03}g;' \
        -e 's{#NEXTVER#}{100.14.05}g;' \
        -e 's{#UPSTREAMVERSION#}{100.14.03}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-100.14.03-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-100.14.03-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/100.14.03/NVIDIA-Linux-x86-100.14.03-pkg0.run}g' \
        < debian/nvidia-kernel-source.README.Debian.in > debian/nvidia-kernel-source.README.Debian
perl -p \
        -e 's{#BASE_VERSION#}{}g;' \
        -e 's{#RELEASE#}{100.14.03}g;' \
        -e 's{#VERSION#}{100.14.03}g;' \
        -e 's{#NEXTVER#}{100.14.05}g;' \
        -e 's{#UPSTREAMVERSION#}{100.14.03}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-100.14.03-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-100.14.03-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/100.14.03/NVIDIA-Linux-x86-100.14.03-pkg0.run}g' \
        < debian/control.in > debian/control
perl -p \
        -e 's{#BASE_VERSION#}{}g;' \
        -e 's{#RELEASE#}{100.14.03}g;' \
        -e 's{#VERSION#}{100.14.03}g;' \
        -e 's{#NEXTVER#}{100.14.05}g;' \
        -e 's{#UPSTREAMVERSION#}{100.14.03}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-100.14.03-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-100.14.03-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/100.14.03/NVIDIA-Linux-x86-100.14.03-pkg0.run}g' \
        < debian/copyright.in > debian/copyright
perl -p \
        -e 's{#BASE_VERSION#}{}g;' \
        -e 's{#RELEASE#}{100.14.03}g;' \
        -e 's{#VERSION#}{100.14.03}g;' \
        -e 's{#NEXTVER#}{100.14.05}g;' \
        -e 's{#UPSTREAMVERSION#}{100.14.03}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-100.14.03-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-100.14.03-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/100.14.03/NVIDIA-Linux-x86-100.14.03-pkg0.run}g' \
        < debian/nvidia-glx.links.in > debian/nvidia-glx.links
perl -p \
        -e 's{#BASE_VERSION#}{}g;' \
        -e 's{#RELEASE#}{100.14.03}g;' \
        -e 's{#VERSION#}{100.14.03}g;' \
        -e 's{#NEXTVER#}{100.14.05}g;' \
        -e 's{#UPSTREAMVERSION#}{100.14.03}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-100.14.03-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-100.14.03-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/100.14.03/NVIDIA-Linux-x86-100.14.03-pkg0.run}g' \
        < debian/nvidia-glx-dev.links.in > debian/nvidia-glx-dev.links
perl -p \
        -e 's{#BASE_VERSION#}{}g;' \
        -e 's{#RELEASE#}{100.14.03}g;' \
        -e 's{#VERSION#}{100.14.03}g;' \
        -e 's{#NEXTVER#}{100.14.05}g;' \
        -e 's{#UPSTREAMVERSION#}{100.14.03}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-100.14.03-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-100.14.03-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/100.14.03/NVIDIA-Linux-x86-100.14.03-pkg0.run}g' \
        < debian/nvidia-glx.override.in > debian/nvidia-glx.override
perl -p \
        -e 's{#BASE_VERSION#}{}g;' \
        -e 's{#RELEASE#}{100.14.03}g;' \
        -e 's{#VERSION#}{100.14.03}g;' \
        -e 's{#NEXTVER#}{100.14.05}g;' \
        -e 's{#UPSTREAMVERSION#}{100.14.03}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-100.14.03-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-100.14.03-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/100.14.03/NVIDIA-Linux-x86-100.14.03-pkg0.run}g' \
        < debian/nvidia-glx.docs.in > debian/nvidia-glx.docs
perl -p \
        -e 's{#BASE_VERSION#}{}g;' \
        -e 's{#RELEASE#}{100.14.03}g;' \
        -e 's{#VERSION#}{100.14.03}g;' \
        -e 's{#NEXTVER#}{100.14.05}g;' \
        -e 's{#UPSTREAMVERSION#}{100.14.03}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-100.14.03-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-100.14.03-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/100.14.03/NVIDIA-Linux-x86-100.14.03-pkg0.run}g' \
        < debian/nvidia-glx.examples.in > debian/nvidia-glx.examples
perl -p \
        -e 's{#BASE_VERSION#}{}g;' \
        -e 's{#RELEASE#}{100.14.03}g;' \
        -e 's{#VERSION#}{100.14.03}g;' \
        -e 's{#NEXTVER#}{100.14.05}g;' \
        -e 's{#UPSTREAMVERSION#}{100.14.03}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-100.14.03-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-100.14.03-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/100.14.03/NVIDIA-Linux-x86-100.14.03-pkg0.run}g' \
        < debian/nvidia-glx.postrm.in > debian/nvidia-glx.postrm
perl -p \
        -e 's{#BASE_VERSION#}{}g;' \
        -e 's{#RELEASE#}{100.14.03}g;' \
        -e 's{#VERSION#}{100.14.03}g;' \
        -e 's{#NEXTVER#}{100.14.05}g;' \
        -e 's{#UPSTREAMVERSION#}{100.14.03}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-100.14.03-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-100.14.03-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/100.14.03/NVIDIA-Linux-x86-100.14.03-pkg0.run}g' \
        < debian/nvidia-glx.init.in > debian/nvidia-glx.init
perl -p \
        -e 's{#BASE_VERSION#}{}g;' \
        -e 's{#RELEASE#}{100.14.03}g;' \
        -e 's{#VERSION#}{100.14.03}g;' \
        -e 's{#NEXTVER#}{100.14.05}g;' \
        -e 's{#UPSTREAMVERSION#}{100.14.03}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-100.14.03-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-100.14.03-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/100.14.03/NVIDIA-Linux-x86-100.14.03-pkg0.run}g' \
        < debian/nvidia-glx-ia32.override.in > debian/nvidia-glx-ia32.override
perl -p \
        -e 's{#BASE_VERSION#}{}g;' \
        -e 's{#RELEASE#}{100.14.03}g;' \
        -e 's{#VERSION#}{100.14.03}g;' \
        -e 's{#NEXTVER#}{100.14.05}g;' \
        -e 's{#UPSTREAMVERSION#}{100.14.03}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-100.14.03-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-100.14.03-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/100.14.03/NVIDIA-Linux-x86-100.14.03-pkg0.run}g' \
        < debian/nvidia-glx-ia32.links.in > debian/nvidia-glx-ia32.links
perl -p \
        -e 's{#BASE_VERSION#}{}g;' \
        -e 's{#RELEASE#}{100.14.03}g;' \
        -e 's{#VERSION#}{100.14.03}g;' \
        -e 's{#NEXTVER#}{100.14.05}g;' \
        -e 's{#UPSTREAMVERSION#}{100.14.03}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-100.14.03-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-100.14.03-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/100.14.03/NVIDIA-Linux-x86-100.14.03-pkg0.run}g' \
        < debian/nvidia-kernel-source.docs.in > debian/nvidia-kernel-source.docs
perl -p \
        -e 's{#BASE_VERSION#}{}g;' \
        -e 's{#RELEASE#}{100.14.03}g;' \
        -e 's{#VERSION#}{100.14.03}g;' \
        -e 's{#NEXTVER#}{100.14.05}g;' \
        -e 's{#UPSTREAMVERSION#}{100.14.03}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-100.14.03-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-100.14.03-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/100.14.03/NVIDIA-Linux-x86-100.14.03-pkg0.run}g' \
        < debian/nvidia-glx-dev.preinst.in > debian/nvidia-glx-dev.preinst
dh_testdir
./NVIDIA-Linux-x86-100.14.03-pkg0.run --extract-only
Creating directory NVIDIA-Linux-x86-100.14.03-pkg0
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86 100.14.03........
................................................................................
.....................................
if test -d /usr/share/envy/nvidia-graphics-drivers/patches; \
        then \
                pwd; \
                ls -al; \
                cd NVIDIA-Linux-x86-100.14.03-pkg0/usr/src/nv; \
                for i in /usr/share/envy/nvidia-graphics-drivers/patches/*; \
                        do patch -p3 <$i; \
                done; \
        fi
sed 's/^nvidia-graphics-drivers/nvidia-kernel/g'  debian/changelog > debian.binary/changelog
touch configure-stamp
touch build-stamp
 debian/rules binary
touch build-stamp
dh_testroot
dh_testdir
# build kernel module source tarball
mkdir -p /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/debian
mkdir -p /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/nv
cp -r /usr/share/envy/nvidia-graphics-drivers/debian.binary/* /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/debian
for f in `ls /usr/share/envy/nvidia-graphics-drivers/debian.binary` ; do \
                perl -p \
                -e 's{#BASE_VERSION#}{}g;' \
                -e 's{#RELEASE#}{100.14.03}g;' \
                -e 's{#VERSION#}{100.14.03}g;' \
                -e 's{#UPSTREAMVERSION#}{100.14.03}g;' \
                -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/100.14.03/NVIDIA-Linux-x86-100.14.03-pkg0.run}g' \
                < /usr/share/envy/nvidia-graphics-drivers/debian.binary/$f >   /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/debian/$f ; \
                chmod 0644 /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/debian/$f ; \
            done
/bin/sh: cannot create /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/debian/patches: Is a directory
chmod 755 /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/debian/patches          
cp /usr/share/envy/nvidia-graphics-drivers/NVIDIA-Linux-x86-100.14.03-pkg0/usr/src/nv/* /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/nv || true
chmod 755 /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/debian/rules
chown -R root:src /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules
tar -zcvf /usr/share/envy/nvidia-graphics-drivers/nvidia-kernel-source.tar.gz -C /usr/share/envy/nvidia-graphics-drivers/debian/temp modules
modules/
modules/nvidia-kernel/
modules/nvidia-kernel/debian/
modules/nvidia-kernel/debian/dirs.template
modules/nvidia-kernel/debian/changelog
modules/nvidia-kernel/debian/control.template
modules/nvidia-kernel/debian/README.Debian
modules/nvidia-kernel/debian/postinst
modules/nvidia-kernel/debian/copyright
modules/nvidia-kernel/debian/postrm
modules/nvidia-kernel/debian/patches/
modules/nvidia-kernel/debian/patches/04_minion
modules/nvidia-kernel/debian/patches/03_pci_get_class
modules/nvidia-kernel/debian/patches/01_sysfs
modules/nvidia-kernel/debian/patches/00list
modules/nvidia-kernel/debian/patches/02_pcialias
modules/nvidia-kernel/debian/override.template
modules/nvidia-kernel/debian/rules
modules/nvidia-kernel/debian/devfs.devices
modules/nvidia-kernel/nv/
modules/nvidia-kernel/nv/nvacpi.c
modules/nvidia-kernel/nv/Makefile.nvidia
modules/nvidia-kernel/nv/nv-kernel.o
modules/nvidia-kernel/nv/Makefile.kbuild
modules/nvidia-kernel/nv/README
modules/nvidia-kernel/nv/os-interface.h
modules/nvidia-kernel/nv/os-interface.c
modules/nvidia-kernel/nv/nvtypes.h
modules/nvidia-kernel/nv/conftest.sh
modules/nvidia-kernel/nv/nv-i2c.c
modules/nvidia-kernel/nv/makefile
modules/nvidia-kernel/nv/os-agp.c
modules/nvidia-kernel/nv/rmretval.h
modules/nvidia-kernel/nv/nv-vm.h
modules/nvidia-kernel/nv/pat.h
modules/nvidia-kernel/nv/nv.h
modules/nvidia-kernel/nv/nvreadme.h
modules/nvidia-kernel/nv/cpuopsys.h
modules/nvidia-kernel/nv/nv-memdbg.h
modules/nvidia-kernel/nv/nv-misc.h
modules/nvidia-kernel/nv/os-registry.c
modules/nvidia-kernel/nv/os-agp.h
modules/nvidia-kernel/nv/nv.c
modules/nvidia-kernel/nv/gcc-version-check.c
modules/nvidia-kernel/nv/nv-vm.c
modules/nvidia-kernel/nv/nv-linux.h
rm -rf debian/temp 
touch build-kernel-stamp
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs
install -m 644 /usr/share/envy/nvidia-graphics-drivers/nvidia-kernel-source.tar.gz /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-kernel-source/usr/src
install -m 0644 NVIDIA-Linux-x86-100.14.03-pkg0/usr/X11R6/lib/modules/drivers/nvidia_drv.so \
                /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/xorg/modules/drivers
install NVIDIA-Linux-x86-100.14.03-pkg0/usr/X11R6/lib/libXvMCNVIDIA.a /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-dev/usr/lib/libXvMCNVIDIA.a;
install NVIDIA-Linux-x86-100.14.03-pkg0/usr/X11R6/lib/libXvMCNVIDIA.so.100.14.03 /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/libXvMCNVIDIA.so.100.14.03;
install -m 0644 NVIDIA-Linux-x86-100.14.03-pkg0/usr/include/GL/gl.h \
                /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-dev/usr/include/GL
install -m 0644 NVIDIA-Linux-x86-100.14.03-pkg0/usr/include/GL/glext.h \
                /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-dev/usr/include/GL
install -m 0644 NVIDIA-Linux-x86-100.14.03-pkg0/usr/include/GL/glx.h \
                /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-dev/usr/include/GL
install -m 0644 NVIDIA-Linux-x86-100.14.03-pkg0/usr/include/GL/glxext.h \
                /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-dev/usr/include/GL
install -m 0644 NVIDIA-Linux-x86-100.14.03-pkg0/usr/lib/libGL.so.100.14.03 \
                        /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib
install -m 0644 NVIDIA-Linux-x86-100.14.03-pkg0/usr/lib/libGLcore.so.100.14.03 \
                /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib
sed "s/__GENERATED_BY__/Debian nvidia-graphics-drivers/" NVIDIA-Linux-x86-100.14.03-pkg0/usr/lib/libGL.la | sed "s/__LIBGL_PATH__/\/usr\/lib/" > /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-dev/usr/lib/libGL.la
# install -m 0644 NVIDIA-Linux-x86-100.14.03-pkg0/usr/lib/libGL.la /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/libGL.la
# TLS (nvidia-tls new for 6106)
install NVIDIA-Linux-x86-100.14.03-pkg0/usr/lib/libnvidia-tls.so.100.14.03 /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/
install NVIDIA-Linux-x86-100.14.03-pkg0/usr/lib/tls/libnvidia-tls.so.100.14.03 /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/nvidia
#sed "s/__GENERATED_BY__/Debian nvidia-graphics-drivers/" NVIDIA-Linux-x86-100.14.03-pkg0/usr/lib/tls/libGL.la | sed "s/__LIBGL_PATH__/\/usr\/lib\/tls/" > /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-dev/usr/lib/nvidia/libGL.la
# install -m 0644 NVIDIA-Linux-x86-100.14.03-pkg0/usr/lib/tls/libGL.la /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/nvidia/libGL.la
install -m 0644 NVIDIA-Linux-x86-100.14.03-pkg0/usr/lib/libnvidia-cfg.so.100.14.03 /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/nvidia/
install NVIDIA-Linux-x86-100.14.03-pkg0/usr/X11R6/lib/modules/extensions/libglx.so.100.14.03 /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/xorg/modules/extensions/
install NVIDIA-Linux-x86-100.14.03-pkg0/usr/X11R6/lib/modules/libnvidia-wfb.so.100.14.03 /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/xorg/modules/
install NVIDIA-Linux-x86-100.14.03-pkg0/usr/bin/tls_test /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/nvidia
install NVIDIA-Linux-x86-100.14.03-pkg0/usr/bin/tls_test_dso.so /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/nvidia
install -d /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/lintian/overrides
install -m 0644 debian/nvidia-glx.override \
                /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/lintian/overrides/nvidia-glx
if [ "i386" == "amd64" ] ; then \
                install NVIDIA-Linux-x86-100.14.03-pkg0/usr/lib32/libGLcore.so.100.14.03 \
                        /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-ia32/emul/ia32-linux/usr/lib ; \
                install NVIDIA-Linux-x86-100.14.03-pkg0/usr/lib32/libGL.so.100.14.03 \
                        /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-ia32/emul/ia32-linux/usr/lib ; \
                install NVIDIA-Linux-x86-100.14.03-pkg0/usr/lib32/libnvidia-tls.so.100.14.03 \
                        /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-ia32/emul/ia32-linux/usr/lib ; \
                install NVIDIA-Linux-x86-100.14.03-pkg0/usr/lib32/tls/libnvidia-tls.so.100.14.03 \
                        /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-ia32/emul/ia32-linux/usr/lib/tls ; \
        fi
[: 10: ==: unexpected operator
install -m 755 NVIDIA-Linux-x86-100.14.03-pkg0/usr/bin/nvidia-bug-report.sh /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/bin/
# use separate package
install -m 755 NVIDIA-Linux-x86-100.14.03-pkg0/usr/bin/nvidia-xconfig /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/bin/
# use separate source package instead
install -m 755 NVIDIA-Linux-x86-100.14.03-pkg0/usr/bin/nvidia-settings /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/bin/
install -m 644 NVIDIA-Linux-x86-100.14.03-pkg0/usr/share/doc/nvidia-settings-user-guide.txt /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/man/man1/
install -m 644 NVIDIA-Linux-x86-100.14.03-pkg0/usr/share/man/man1/nvidia-settings.1.gz /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/man/man1/
install -m 644 NVIDIA-Linux-x86-100.14.03-pkg0/usr/share/man/man1/nvidia-xconfig.1.gz /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/man/man1/
install /usr/share/envy/nvidia-graphics-drivers/script /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/bug/nvidia-glx
dh_install
/usr/bin/make -f debian/rules binary-common
make[1]: Entering directory `/usr/share/envy/nvidia-graphics-drivers'
dh_testdir
dh_testroot
dh_installchangelogs
dh_installdocs -s
dh_installexamples
dh_installdebconf
dh_installinit
dh_installman
dh_link
dh_compress -X.h -X README.Debian
dh_fixperms
dh_makeshlibs
dh_installdeb
dh_shlibdeps  -Xia32 -Xtls -l/usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib
# quickhack! remove me :-/
perl -pi.bak -e 's/,\s+nvidia-glx-ia32//;' /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx.substvars
dh_gencontrol -s
dh_md5sums
dh_builddeb -s
dpkg-deb: building package `nvidia-glx' in `../nvidia-glx_100.14.05_i386.deb'.
dpkg-deb: building package `nvidia-glx-dev' in `../nvidia-glx-dev_100.14.05_i386.deb'.
dpkg-deb: building package `nvidia-kernel-source' in `../nvidia-kernel-source_100.14.05_i386.deb'.
make[1]: Leaving directory `/usr/share/envy/nvidia-graphics-drivers'
 dpkg-genchanges -b
dpkg-genchanges: binary-only upload - not including any source code
dpkg-buildpackage: binary only upload (no source included)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.20-15-generic linux-headers-2.6.20-15
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-kernel-common is already the newest version.
nvidia-kernel-common set to manual installed.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.20-15-generic linux-headers-2.6.20-15
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Selecting previously deselected package nvidia-kernel-source.
(Reading database ... 136695 files and directories currently installed.)
Unpacking nvidia-kernel-source (from nvidia-kernel-source_100.14.05_i386.deb) ...
Setting up nvidia-kernel-source (100.14.05) ...
rm: cannot remove `/usr/src/nvidia-kernel*.deb': No such file or directory
rm: cannot remove `/usr/src/nvidia-legacy-kernel*.deb': No such file or directory
rm: cannot remove `/usr/src/nvidia-new-kernel*.deb': No such file or directory
Getting source for kernel version: 2.6.20-16-lowlatency
Kernel headers available in /lib/modules/2.6.20-16-lowlatency/build
Creating symlink...
apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manual installed.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.20-15-generic linux-headers-2.6.20-15
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Done!

tls.so.100.14.03 \
                        /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-ia32/emul/ia32-linux/usr/lib/tls ; \
        fi
[: 10: ==: unexpected operator
install -m 755 NVIDIA-Linux-x86-100.14.03-pkg0/usr/bin/nvidia-bug-report.sh /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/bin/
# use separate package
install -m 755 NVIDIA-Linux-x86-100.14.03-pkg0/usr/bin/nvidia-xconfig /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/bin/
# use separate source package instead
install -m 755 NVIDIA-Linux-x86-100.14.03-pkg0/usr/bin/nvidia-settings /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/bin/
install -m 644 NVIDIA-Linux-x86-100.14.03-pkg0/usr/share/doc/nvidia-settings-user-guide.txt /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/man/man1/
install -m 644 NVIDIA-Linux-x86-100.14.03-pkg0/usr/share/man/man1/nvidia-settings.1.gz /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/man/man1/
install -m 644 NVIDIA-Linux-x86-100.14.03-pkg0/usr/share/man/man1/nvidia-xconfig.1.gz /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/man/man1/
install /usr/share/envy/nvidia-graphics-drivers/script /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/bug/nvidia-glx
dh_install 
/usr/bin/make -f debian/rules binary-common
make[1]: Entering directory `/usr/share/envy/nvidia-graphics-drivers'
dh_testdir
dh_testroot
dh_installchangelogs 
dh_installdocs -s 
dh_installexamples
dh_installdebconf
dh_installinit
dh_installman
dh_link
dh_compress -X.h -X README.Debian 
dh_fixperms
dh_makeshlibs
dh_installdeb
dh_shlibdeps  -Xia32 -Xtls -l/usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib
# quickhack! remove me :-/
perl -pi.bak -e 's/,\s+nvidia-glx-ia32//;' /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx.substvars
dh_gencontrol -s
dh_md5sums
dh_builddeb -s
dpkg-deb: building package `nvidia-glx' in `../nvidia-glx_100.14.05_i386.deb'.
dpkg-deb: building package `nvidia-glx-dev' in `../nvidia-glx-dev_100.14.05_i386.deb'.
dpkg-deb: building package `nvidia-kernel-source' in `../nvidia-kernel-source_100.14.05_i386.deb'.
make[1]: Leaving directory `/usr/share/envy/nvidia-graphics-drivers'
 dpkg-genchanges -b
dpkg-genchanges: binary-only upload - not including any source code
dpkg-buildpackage: binary only upload (no source included)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.20-15-generic linux-headers-2.6.20-15
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-kernel-common is already the newest version.
nvidia-kernel-common set to manual installed.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.20-15-generic linux-headers-2.6.20-15
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Selecting previously deselected package nvidia-kernel-source.
(Reading database ... 136695 files and directories currently installed.)
Unpacking nvidia-kernel-source (from nvidia-kernel-source_100.14.05_i386.deb) ...
Setting up nvidia-kernel-source (100.14.05) ...
rm: cannot remove `/usr/src/nvidia-kernel*.deb': No such file or directory
rm: cannot remove `/usr/src/nvidia-legacy-kernel*.deb': No such file or directory
rm: cannot remove `/usr/src/nvidia-new-kernel*.deb': No such file or directory
Getting source for kernel version: 2.6.20-16-lowlatency
Kernel headers available in /lib/modules/2.6.20-16-lowlatency/build
Creating symlink...
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manual installed.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.20-15-generic linux-headers-2.6.20-15
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Done!

Updated infos about 85 packages
Extracting the package tarball, /usr/src/nvidia-kernel-source.tar.gz, please wait...

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Building nvidia-kernel-source, step 2, please wait... &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;   
  &#9474;                                                                         &#9474;   
  &#9474;                                                                         &#9474;   
  &#9474;                                                                         &#9474;   
  &#9474;                                                                         &#9474;   
  &#9474;                                                                         &#9474;   
  &#9474;                                                                         &#9474;   
  &#9474;                                                                         &#9474;   
  &#9474;                                                                         &#9474;   
  &#9474;                                                                         &#9474;   
  &#9474;                                                                         &#9474;   
  &#9474;                                                                         &#9474;
install -m 755 NVIDIA-Linux-x86-100.14.03-pkg0/usr/bin/nvidia-bug-report.sh /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/bin/
# use separate package
install -m 755 NVIDIA-Linux-x86-100.14.03-pkg0/usr/bin/nvidia-xconfig /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/bin/
# use separate source package instead
install -m 755 NVIDIA-Linux-x86-100.14.03-pkg0/usr/bin/nvidia-settings /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/bin/
install -m 644 NVIDIA-Linux-x86-100.14.03-pkg0/usr/share/doc/nvidia-settings-user-guide.txt /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/man/man1/
install -m 644 NVIDIA-Linux-x86-100.14.03-pkg0/usr/share/man/man1/nvidia-settings.1.gz /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/man/man1/
install -m 644 NVIDIA-Linux-x86-100.14.03-pkg0/usr/share/man/man1/nvidia-xconfig.1.gz /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/man/man1/
install /usr/share/envy/nvidia-graphics-drivers/script /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/bug/nvidia-glx
dh_install 
/usr/bin/make -f debian/rules binary-common
make[1]: Entering directory `/usr/share/envy/nvidia-graphics-drivers'
dh_testdir
dh_testroot
dh_installchangelogs 
dh_installdocs -s 
dh_installexamples
dh_installdebconf
dh_installinit
dh_installman
dh_link
dh_compress -X.h -X README.Debian 
dh_fixperms
dh_makeshlibs
dh_installdeb
dh_shlibdeps  -Xia32 -Xtls -l/usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib
# quickhack! remove me :-/
perl -pi.bak -e 's/,\s+nvidia-glx-ia32//;' /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx.substvars
dh_gencontrol -s
dh_md5sums
dh_builddeb -s
dpkg-deb: building package `nvidia-glx' in `../nvidia-glx_100.14.05_i386.deb'.
dpkg-deb: building package `nvidia-glx-dev' in `../nvidia-glx-dev_100.14.05_i386.deb'.
dpkg-deb: building package `nvidia-kernel-source' in `../nvidia-kernel-source_100.14.05_i386.deb'.
make[1]: Leaving directory `/usr/share/envy/nvidia-graphics-drivers'
 dpkg-genchanges -b
dpkg-genchanges: binary-only upload - not including any source code
dpkg-buildpackage: binary only upload (no source included)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.20-15-generic linux-headers-2.6.20-15
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-kernel-common is already the newest version.
nvidia-kernel-common set to manual installed.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.20-15-generic linux-headers-2.6.20-15
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Selecting previously deselected package nvidia-kernel-source.
(Reading database ... 136695 files and directories currently installed.)
Unpacking nvidia-kernel-source (from nvidia-kernel-source_100.14.05_i386.deb) ...
Setting up nvidia-kernel-source (100.14.05) ...
rm: cannot remove `/usr/src/nvidia-kernel*.deb': No such file or directory
rm: cannot remove `/usr/src/nvidia-legacy-kernel*.deb': No such file or directory
rm: cannot remove `/usr/src/nvidia-new-kernel*.deb': No such file or directory
Getting source for kernel version: 2.6.20-16-lowlatency
Kernel headers available in /lib/modules/2.6.20-16-lowlatency/build
Creating symlink...
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manual installed.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.20-15-generic linux-headers-2.6.20-15
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Done!

Updated infos about 85 packages
Extracting the package tarball, /usr/src/nvidia-kernel-source.tar.gz, please wait...
Done with /usr/src/nvidia-kernel-2.6.20-16-lowlatency_100.14.05+2.6.20-16.28_i386.deb .
Selecting previously deselected package nvidia-kernel-2.6.20-16-lowlatency.
(Reading database ... 136703 files and directories currently installed.)
Unpacking nvidia-kernel-2.6.20-16-lowlatency (from .../nvidia-kernel-2.6.20-16-lowlatency_100.14.05+2.6.20-16.28_i386.deb) ...
Setting up nvidia-kernel-2.6.20-16-lowlatency (100.14.05+2.6.20-16.28) ...

rm: cannot remove `/usr/lib/nvidia/libGL.so.1*': No such file or directory
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-new is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.20-15-generic linux-headers-2.6.20-15
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.20-15-generic linux-headers-2.6.20-15
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Selecting previously deselected package nvidia-glx.
(Reading database ... 136710 files and directories currently installed.)
Unpacking nvidia-glx (from nvidia-glx_100.14.05_i386.deb) ...
Setting up nvidia-glx (100.14.05) ...
Creating NVIDIA TLS links... done.

rm: cannot remove `*.asc': No such file or directory
rm: cannot remove `/usr/share/envy/*.deb': No such file or directory
rm: cannot remove `/usr/share/envy/*.asc': No such file or directory
rm: cannot remove `/usr/share/envy/*.changes': No such file or directory
ENVY: Operation Completed

---

