---
title: "NDISWRAPPER Compile Error for WUSB54G - Help!!!"
date: 2005-12-17
forum: Networking &amp; Wireless
---

### Post by tirofiban on 2005-12-17
Hello,

I'm new to Linux and have not had much success getting the Linksys WUSB54G to work with my Linux system.:confused: 

I tried the default NDISWRAPPER (1.1) and it says driver loaded, hardware present, but IWCONFIG says there is no WLAN0. 

So I figured, it would be best to compile the latest NDISWRAPPER version. This is where I'm really getting stuck and could use your help. I've tried 2 different installation methods I found on the net. I keep getting errors. Enclosed are copies of the terminal text. I appreciate any help. Thank you.

P.S. What's a compatibility level?

ATTEMPT #1:

marc@Dell:~$ sudo -s
Password:
root@Dell:~# apt-get install debhelper build-essential fakeroot linux-headers-$( uname -r)
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  binutils debconf-utils dpkg-dev g++ g++-4.0 gcc gcc-4.0 gettext html2text
  intltool-debian libc6-dev libstdc++6-4.0-dev linux-headers-2.6.12-9
  linux-kernel-headers make po-debconf
Suggested packages:
  binutils-doc dh-make debian-keyring gcc-4.0-doc lib64stdc++6 manpages-dev
  autoconf automake1.9 libtool flex bison gcc-doc gcc-4.0-locales
  libc6-dev-amd64 lib64gcc1 cvs gettext-doc glibc-doc libstdc++6-4.0-doc
  stl-manual
Recommended packages:
  libmudflap0-dev curl libmail-sendmail-perl libcompress-zlib-perl
The following NEW packages will be installed:
  binutils build-essential debconf-utils debhelper dpkg-dev fakeroot g++
  g++-4.0 gcc gcc-4.0 gettext html2text intltool-debian libc6-dev
  libstdc++6-4.0-dev linux-headers-2.6.12-9 linux-headers-2.6.12-9-386
  linux-kernel-headers make po-debconf
0 upgraded, 20 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/19.4MB of archives.
After unpacking 120MB of additional disk space will be used.
Do you want to continue [Y/n]? Y

Preconfiguring packages ...
Selecting previously deselected package binutils.
(Reading database ... 56661 files and directories currently installed.)
Unpacking binutils (from .../binutils_2.16.1-2ubuntu6_i386.deb) ...
Selecting previously deselected package linux-kernel-headers.
Unpacking linux-kernel-headers (from .../linux-kernel-headers_2.6.11.2-0ubuntu13 _i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.3.5-1ubuntu12_i386.deb) ...
Selecting previously deselected package gcc-4.0.
Unpacking gcc-4.0 (from .../gcc-4.0_4.0.1-4ubuntu9_i386.deb) ...
Selecting previously deselected package gcc.
Unpacking gcc (from .../gcc_4%3a4.0.1-3_i386.deb) ...
Selecting previously deselected package libstdc++6-4.0-dev.
Unpacking libstdc++6-4.0-dev (from .../libstdc++6-4.0-dev_4.0.1-4ubuntu9_i386.de b) ...
Selecting previously deselected package g++-4.0.
Unpacking g++-4.0 (from .../g++-4.0_4.0.1-4ubuntu9_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.0.1-3_i386.deb) ...
Selecting previously deselected package make.
Unpacking make (from .../archives/make_3.80-9_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.10ubuntu4_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.1_i386.deb) ...
Selecting previously deselected package debconf-utils.
Unpacking debconf-utils (from .../debconf-utils_1.4.56ubuntu2_all.deb) ...
Selecting previously deselected package html2text.
Unpacking html2text (from .../html2text_1.3.2a-2build1_i386.deb) ...
Selecting previously deselected package gettext.
Unpacking gettext (from .../gettext_0.14.5-2ubuntu2_i386.deb) ...
Selecting previously deselected package intltool-debian.
Unpacking intltool-debian (from .../intltool-debian_0.30+20040213_all.deb) ...
Selecting previously deselected package po-debconf.
Unpacking po-debconf (from .../po-debconf_0.8.23_all.deb) ...
Selecting previously deselected package debhelper.
Unpacking debhelper (from .../debhelper_4.9.5ubuntu1_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.5.1ubuntu2_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.12-9.
Unpacking linux-headers-2.6.12-9 (from .../linux-headers-2.6.12-9_2.6.12-9.23_i3 86.deb) ...
Selecting previously deselected package linux-headers-2.6.12-9-386.
Unpacking linux-headers-2.6.12-9-386 (from .../linux-headers-2.6.12-9-386_2.6.12 -9.23_i386.deb) ...
Setting up binutils (2.16.1-2ubuntu6) ...

Setting up linux-kernel-headers (2.6.11.2-0ubuntu13) ...
Setting up libc6-dev (2.3.5-1ubuntu12) ...
Setting up gcc-4.0 (4.0.1-4ubuntu9) ...
Setting up gcc (4.0.1-3) ...

Setting up make (3.80-9) ...

Setting up dpkg-dev (1.13.10ubuntu4) ...
Setting up debconf-utils (1.4.56ubuntu2) ...

Setting up html2text (1.3.2a-2build1) ...

Setting up gettext (0.14.5-2ubuntu2) ...

Setting up intltool-debian (0.30+20040213) ...
Setting up po-debconf (0.8.23) ...
Setting up debhelper (4.9.5ubuntu1) ...
Setting up fakeroot (1.5.1ubuntu2) ...

Setting up linux-headers-2.6.12-9 (2.6.12-9.23) ...

Setting up linux-headers-2.6.12-9-386 (2.6.12-9.23) ...
Setting up libstdc++6-4.0-dev (4.0.1-4ubuntu9) ...
Setting up g++-4.0 (4.0.1-4ubuntu9) ...
Setting up g++ (4.0.1-3) ...

Setting up build-essential (11.1) ...
root@Dell:~# dir
Desktop  ndiswrapper-17targz.tar  windows_drivers
root@Dell:~# pwd
/home/marc
root@Dell:~# cd /usr/src
root@Dell:/usr/src# tar xvzf /home/marc/ndiswrapper-17targz.tar
ndiswrapper-1.7/
ndiswrapper-1.7/AUTHORS
ndiswrapper-1.7/ChangeLog
ndiswrapper-1.7/INSTALL
ndiswrapper-1.7/Makefile
ndiswrapper-1.7/README
ndiswrapper-1.7/ndiswrapper.spec
ndiswrapper-1.7/version
ndiswrapper-1.7/ndiswrapper.8
ndiswrapper-1.7/utils/
ndiswrapper-1.7/utils/Makefile
ndiswrapper-1.7/utils/ndiswrapper
ndiswrapper-1.7/utils/loadndisdriver.c
ndiswrapper-1.7/utils/ndiswrapper-buginfo
ndiswrapper-1.7/driver/
ndiswrapper-1.7/driver/divdi3.c
ndiswrapper-1.7/driver/hal.c
ndiswrapper-1.7/driver/iw_ndis.c
ndiswrapper-1.7/driver/iw_ndis.h
ndiswrapper-1.7/driver/loader.c
ndiswrapper-1.7/driver/loader.h
ndiswrapper-1.7/driver/longlong.h
ndiswrapper-1.7/driver/Makefile
ndiswrapper-1.7/driver/misc_funcs.c
ndiswrapper-1.7/driver/ndis.c
ndiswrapper-1.7/driver/ndis.h
ndiswrapper-1.7/driver/ndiswrapper.h
ndiswrapper-1.7/driver/ntoskernel.c
ndiswrapper-1.7/driver/ntoskernel.h
ndiswrapper-1.7/driver/ntoskernel_io.c
ndiswrapper-1.7/driver/pe_linker.c
ndiswrapper-1.7/driver/pe_linker.h
ndiswrapper-1.7/driver/pnp.c
ndiswrapper-1.7/driver/pnp.h
ndiswrapper-1.7/driver/proc.c
ndiswrapper-1.7/driver/usb.c
ndiswrapper-1.7/driver/usb.h
ndiswrapper-1.7/driver/winnt_types.h
ndiswrapper-1.7/driver/wrapper.c
ndiswrapper-1.7/driver/wrapndis.h
ndiswrapper-1.7/driver/wrapndis.c
ndiswrapper-1.7/driver/x86_64_stubs.S
ndiswrapper-1.7/debian/
ndiswrapper-1.7/debian/Makefile
ndiswrapper-1.7/debian/changelog.modules
ndiswrapper-1.7/debian/changelog.source
ndiswrapper-1.7/debian/changelog.utils
ndiswrapper-1.7/debian/control.modules
ndiswrapper-1.7/debian/control.source
ndiswrapper-1.7/debian/control.utils
ndiswrapper-1.7/debian/copyright
ndiswrapper-1.7/debian/dirs.utils
ndiswrapper-1.7/debian/docs
ndiswrapper-1.7/debian/postinst.modules
ndiswrapper-1.7/debian/README.Debian
ndiswrapper-1.7/debian/rules
root@Dell:/usr/src# pwd
/usr/src
root@Dell:/usr/src# dir
linux-headers-2.6.12-9  linux-headers-2.6.12-9-386  ndiswrapper-1.7
root@Dell:/usr/src# cd /usr/src/ndiswrapper-1.7
root@Dell:/usr/src/ndiswrapper-1.7# sed -e "s/misc/kernel\/drivers\/net\/ndiswra pper/g" debian/rules > debian/temp
root@Dell:/usr/src/ndiswrapper-1.7# mv debian/temp debian/rules
root@Dell:/usr/src/ndiswrapper-1.7# cd /usr/src/ndiswrapper-1.7
root@Dell:/usr/src/ndiswrapper-1.7# make deb
make[1]: Entering directory `/usr/src/ndiswrapper-1.7'
make -f debian/rules binary-utils
make[2]: Entering directory `/usr/src/ndiswrapper-1.7'
sed -e 's/-#KVERS#//g' \
-e 's/#DRIVER_VERSION#/1.7/g' \
-e 's/#UTILS_VERSION#/1.7/g' \
-e 's/#DATE#/'"`date --rfc-822`"'/g' \
        -e 's/#MAINT#/Giridhar Pemmasani <pgiri@users.sourceforge.net>/g' \
        debian/changelog.utils > debian/changelog
sed -e 's/#DRIVER_VERSION#/1.7/' \
-e 's/#UTILS_VERSION#/1.7/' \
-e 's/#MAINT#/Giridhar Pemmasani <pgiri@users.sourceforge.net>/g' \
debian/control.utils > debian/control
echo "utils/loadndisdriver /sbin" > debian/ndiswrapper-utils.install
echo "utils/ndiswrapper /usr/sbin" >> debian/ndiswrapper-utils.install
echo "utils/ndiswrapper-buginfo /usr/sbin" >> \
        debian/ndiswrapper-utils.install
cp debian/dirs.utils debian/dirs
dh_testdir
dh_testroot
dh_installchangelogs ChangeLog
dh_installchangelogs: Compatibility levels before 3 are deprecated.
dh_installdocs
dh_installdocs: Compatibility levels before 3 are deprecated.
dh_installexamples
dh_installexamples: Compatibility levels before 3 are deprecated.
dh_installdebconf
dh_installdebconf: Compatibility levels before 3 are deprecated.
export DH_OPTIONS='-i'
dh_installman ndiswrapper.8
dh_installman: Compatibility levels before 3 are deprecated.
make -C utils
make[3]: Entering directory `/usr/src/ndiswrapper-1.7/utils'
gcc -g -Wall -DUTILS_VERSION=\"1.7\"  -o loadndisdriver loadndisdriver.c
make[3]: Leaving directory `/usr/src/ndiswrapper-1.7/utils'
dh_install
dh_install: Compatibility levels before 3 are deprecated.
dh_link
dh_link: Compatibility levels before 3 are deprecated.
dh_strip
dh_strip: Compatibility levels before 3 are deprecated.
dh_compress
dh_compress: Compatibility levels before 3 are deprecated.
dh_fixperms
dh_fixperms: Compatibility levels before 3 are deprecated.
dh_perl
dh_perl: Compatibility levels before 3 are deprecated.
dh_makeshlibs
dh_makeshlibs: Compatibility levels before 3 are deprecated.
dh_installdeb
dh_installdeb: Compatibility levels before 3 are deprecated.
dh_shlibdeps
dh_shlibdeps: Compatibility levels before 3 are deprecated.
dh_gencontrol
dh_gencontrol: Compatibility levels before 3 are deprecated.
dpkg-gencontrol: warning: unknown substitution variable ${misc:Depends}
dh_md5sums
dh_md5sums: Compatibility levels before 3 are deprecated.
dh_builddeb --destdir=..
dh_builddeb: Compatibility levels before 3 are deprecated.
dpkg-deb: building package `ndiswrapper-utils' in `../ndiswrapper-utils_1.7-1_i3 86.deb'.
dh_clean
dh_clean: Compatibility levels before 3 are deprecated.
make[2]: Leaving directory `/usr/src/ndiswrapper-1.7'
make -f debian/rules binary-modules
make[2]: Entering directory `/usr/src/ndiswrapper-1.7'
sed -e 's/#KVERS#/2.6.12-9-386/g' \
-e 's/#DRIVER_VERSION#/1.7/g' \
-e 's/#UTILS_VERSION#/1.7/g' \
-e 's/#DATE#/'"`date --rfc-822`"'/g' \
        -e 's/#MAINT#/Giridhar Pemmasani <pgiri@users.sourceforge.net>/g' \
        debian/changelog.modules > debian/changelog
sed -e 's/#KVERS#/2.6.12-9-386/' \
-e 's/#DRIVER_VERSION#/1.7/' \
-e 's/#UTILS_VERSION#/1.7/' \
debian/control.modules > debian/control
sed -e 's/#KVERS#/2.6.12-9-386/' debian/postinst.modules > debian/postinst
if [ 6 == 4 ];then \
        module=ndiswrapper.o; \
else \
        module=ndiswrapper.ko; \
fi; \
echo "driver/$module /lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper" \
        > debian/ndiswrapper-modules-2.6.12-9-386.install
dh_testdir
dh_testroot
dh_installchangelogs ChangeLog
dh_installchangelogs: Compatibility levels before 3 are deprecated.
dh_installdocs
dh_installdocs: Compatibility levels before 3 are deprecated.
dh_installexamples
dh_installexamples: Compatibility levels before 3 are deprecated.
dh_installdebconf
dh_installdebconf: Compatibility levels before 3 are deprecated.
dh_installdirs lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper
dh_installdirs: Compatibility levels before 3 are deprecated.
make -C /usr/src/ndiswrapper-1.7/driver
make[3]: Entering directory `/usr/src/ndiswrapper-1.7/driver'
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/usr/src/ndiswrapper-1.7/driver \
        DRIVER_VERSION=1.7
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: co mmand not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: co mmand not found
make[4]: gcc-3.4: Command not found
make[4]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  LD      /usr/src/ndiswrapper-1.7/driver/built-in.o
  CC [M]  /usr/src/ndiswrapper-1.7/driver/hal.o
/bin/sh: gcc-3.4: command not found
make[5]: *** [/usr/src/ndiswrapper-1.7/driver/hal.o] Error 127
make[4]: *** [_module_/usr/src/ndiswrapper-1.7/driver] Error 2
make[4]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make[3]: *** [default] Error 2
make[3]: Leaving directory `/usr/src/ndiswrapper-1.7/driver'
make[2]: *** [build-modules] Error 2
make[2]: Leaving directory `/usr/src/ndiswrapper-1.7'
make[1]: *** [binary] Error 2
make[1]: Leaving directory `/usr/src/ndiswrapper-1.7'
make: *** [deb] Error 2
root@Dell:/usr/src/ndiswrapper-1.7#



ATTEMPT 2 (Different method?):
marc@Dell:~$ tar xvfz ndiswrapper-17tar.gz
ndiswrapper-1.7/
ndiswrapper-1.7/AUTHORS
ndiswrapper-1.7/ChangeLog
ndiswrapper-1.7/INSTALL
ndiswrapper-1.7/Makefile
ndiswrapper-1.7/README
ndiswrapper-1.7/ndiswrapper.spec
ndiswrapper-1.7/version
ndiswrapper-1.7/ndiswrapper.8
ndiswrapper-1.7/utils/
ndiswrapper-1.7/utils/Makefile
ndiswrapper-1.7/utils/ndiswrapper
ndiswrapper-1.7/utils/loadndisdriver.c
ndiswrapper-1.7/utils/ndiswrapper-buginfo
ndiswrapper-1.7/driver/
ndiswrapper-1.7/driver/divdi3.c
ndiswrapper-1.7/driver/hal.c
ndiswrapper-1.7/driver/iw_ndis.c
ndiswrapper-1.7/driver/iw_ndis.h
ndiswrapper-1.7/driver/loader.c
ndiswrapper-1.7/driver/loader.h
ndiswrapper-1.7/driver/longlong.h
ndiswrapper-1.7/driver/Makefile
ndiswrapper-1.7/driver/misc_funcs.c
ndiswrapper-1.7/driver/ndis.c
ndiswrapper-1.7/driver/ndis.h
ndiswrapper-1.7/driver/ndiswrapper.h
ndiswrapper-1.7/driver/ntoskernel.c
ndiswrapper-1.7/driver/ntoskernel.h
ndiswrapper-1.7/driver/ntoskernel_io.c
ndiswrapper-1.7/driver/pe_linker.c
ndiswrapper-1.7/driver/pe_linker.h
ndiswrapper-1.7/driver/pnp.c
ndiswrapper-1.7/driver/pnp.h
ndiswrapper-1.7/driver/proc.c
ndiswrapper-1.7/driver/usb.c
ndiswrapper-1.7/driver/usb.h
ndiswrapper-1.7/driver/winnt_types.h
ndiswrapper-1.7/driver/wrapper.c
ndiswrapper-1.7/driver/wrapndis.h
ndiswrapper-1.7/driver/wrapndis.c
ndiswrapper-1.7/driver/x86_64_stubs.S
ndiswrapper-1.7/debian/
ndiswrapper-1.7/debian/Makefile
ndiswrapper-1.7/debian/changelog.modules
ndiswrapper-1.7/debian/changelog.source
ndiswrapper-1.7/debian/changelog.utils
ndiswrapper-1.7/debian/control.modules
ndiswrapper-1.7/debian/control.source
ndiswrapper-1.7/debian/control.utils
ndiswrapper-1.7/debian/copyright
ndiswrapper-1.7/debian/dirs.utils
ndiswrapper-1.7/debian/docs
ndiswrapper-1.7/debian/postinst.modules
ndiswrapper-1.7/debian/README.Debian
ndiswrapper-1.7/debian/rules
marc@Dell:~$ cd ndiswrapper-1.7
marc@Dell:~/ndiswrapper-1.7$ fakeroot debian/rules binary-modules
sed -e 's/#KVERS#/2.6.12-9-386/g' \
-e 's/#DRIVER_VERSION#/1.7/g' \
-e 's/#UTILS_VERSION#/1.7/g' \
-e 's/#DATE#/'"`date --rfc-822`"'/g' \
        -e 's/#MAINT#/Giridhar Pemmasani <pgiri@users.sourceforge.net>/g' \
        debian/changelog.modules > debian/changelog
sed -e 's/#KVERS#/2.6.12-9-386/' \
-e 's/#DRIVER_VERSION#/1.7/' \
-e 's/#UTILS_VERSION#/1.7/' \
debian/control.modules > debian/control
sed -e 's/#KVERS#/2.6.12-9-386/' debian/postinst.modules > debian/postinst
if [ 6 == 4 ];then \
        module=ndiswrapper.o; \
else \
        module=ndiswrapper.ko; \
fi; \
echo "driver/$module /lib/modules/2.6.12-9-386/misc" \
        > debian/ndiswrapper-modules-2.6.12-9-386.install
dh_testdir
dh_testroot
dh_installchangelogs ChangeLog
dh_installchangelogs: Compatibility levels before 3 are deprecated.
dh_installdocs
dh_installdocs: Compatibility levels before 3 are deprecated.
dh_installexamples
dh_installexamples: Compatibility levels before 3 are deprecated.
dh_installdebconf
dh_installdebconf: Compatibility levels before 3 are deprecated.
dh_installdirs lib/modules/2.6.12-9-386/misc
dh_installdirs: Compatibility levels before 3 are deprecated.
/usr/bin/make -C /home/marc/ndiswrapper-1.7/driver
make[1]: Entering directory `/home/marc/ndiswrapper-1.7/driver'
/usr/bin/make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/marc/ndiswrapper- 1.7/driver \
        DRIVER_VERSION=1.7
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: co mmand not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: co mmand not found
make[2]: gcc-3.4: Command not found
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  LD      /home/marc/ndiswrapper-1.7/driver/built-in.o
  CC [M]  /home/marc/ndiswrapper-1.7/driver/hal.o
/bin/sh: gcc-3.4: command not found
make[3]: *** [/home/marc/ndiswrapper-1.7/driver/hal.o] Error 127
make[2]: *** [_module_/home/marc/ndiswrapper-1.7/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/marc/ndiswrapper-1.7/driver'
make: *** [build-modules] Error 2
marc@Dell:~/ndiswrapper-1.7$

---

### Post by Verbious on 2005-12-18
For what it is worth, I followed the instructions for using NDISWRAPPER in two of the how to's.  I was able to get my Netgear WG511 working.  This is a PCMCIA card that was made in China and has given people fits because it doesn't work sometimes.

I had to reload Ubuntu and started over.  Without access to the net, how was I going to download the latest and greatest Ndiswrapper?

Here is what I did:

With a fresh Breezy install I went to System > Administration> Synaptic Packet Manger.  I then searched for "ndiswrapper" and the selected it for application. Hit apply and let it install.

Make a folder called "windows_drivers" and copy the .inf, .cat, and .sys windows XP files into it.  

Now open a terminal and change directories until you are in the "windows_drivers" folder.  Once you can see your Windows drivers that you copied over, do:  sudo ndiswrapper -i yourdriver.INF  

check to see that your driver was installed correctly by doing:  sudo ndiswrapper -l

This will show that the driver is installed and the hardware present.

Next do:  sudo ndiswrapper -m  This should load ndiswrapper as a module.

Next do:  sudo gedit /etc/network/interfaces

You must add a few things to this file.  Here is mine. 
mapping hotplug
	script grep
	[COLOR="Red"]map wlan0

iface wlan0 inet dhcp
auto wlan0[/COLOR]

Add the stuff in red to your file, Save it and then restart your computer.

Once the computer restarts look for the lights to light up on the card.  hopefully they will.  Now open a terminal and do:  network-admin  

This will open the GUI for administering your network cards.  Click on wlan0 and then click Activate.  Then click properties.  in the properties box you will see a drop down menu under Wireless Settings for:  Network Name (ESSID)

Click the drop down menu and look for your wireless network, click on it then hit OK.  Deactivate your eth0 or wired LAN and then you should be able to get out on the web.

That is how I did my PCMCIA card with the ndiswrapper that comes with Ubuntu. 

I tried using the WiFiRadar but had big problems so I stopped using it.  

I hope that helps.  Look for my post called Netgear WG511 version 3 made in china working.  That was the first method that I followed, and then found out that I really didn't need to.  Live and learn!

---

### Post by greenway on 2005-12-18
Looking over your post, I noticed your gcc-3.4 package is missing and this is causing some compilation problems. You can solve this by typing "sudo apt-get install gcc-3.4" in a terminal.

Also, this is the sequence I always follow when compiling NDISWRAPPER and it has never failed on me:

make sure you have the following packages installed:

build-essential (sudo apt-get install build-essential)
kernel-package (sudo apt-get install kernel-package)
gcc-3.4  (sudo apt-get install gcc-3.4)
libncurses5 (sudo apt-get install libncurses5)
libncurses5-dev (sudo apt-get install libncurses5-dev)
libqt3-mt-dev (sudo apt-get install libqt3-mt-dev)

(Not quite sure if the last three are needed for module compilation but just be sure... )

Furthermore, make sure you have the correct kernel headers: sudo apt-get install linux-headers-<<version>> (for example "sudo apt-get install linux-headers-2.6.10-5-386")

Then create a symbolic link pointing to your kernel headers (assuming you're running the 2.6.10-5-386 kernel, if not replace with you kernel type).

type:

sudo ln -s /usr/src/linux-headers-2.6.10-5-386 /lib/modules/2.6.10-5-386/build

To be sure, check in /lib/modules/2.6.10-5-386/build if there's a link to your kernel headers.

Now, download the latest version of NDISWRAPPER and unpack it (I always put it in /usr/src/NDISWRAPPER-version), go to the directory where you unpacked it, run "sudo make clean", then "sudo make" and finally "sudo make install"

This should get you on your way, if you still experience any problems just post them here.

best of luck!

---

