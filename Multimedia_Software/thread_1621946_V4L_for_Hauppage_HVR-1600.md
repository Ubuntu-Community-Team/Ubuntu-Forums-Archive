---
title: "V4L for Hauppage HVR-1600"
date: 2010-11-14
forum: Multimedia Software
---

### Post by Ayasugi on 2010-11-14
I'm having quite a bit of trouble getting my capture card to work. I've been following [this guide]("http://www.mythtv.org/wiki/Hauppauge_HVR-1600").
My overall goal is to stream a live tv signal to someone on a separate network, but this post is just about getting the card to work in linux. I'm not afraid of terminal, but I'm merely an enlightened newbie. I'm not exactly sure what to post, but here are some steps of the installation process that returned errors. Any help is very much appreciated. :P
I'm running Ubuntu 10.04, kernel version 2.6.32-21-generic.

Output from sudo make menuconfig
```
ayasugi@ayasugi-desktop:/lib/firmware/v4l-dvb$ sudo make menuconfig
make -C /lib/firmware/v4l-dvb/v4l menuconfig
make[1]: Entering directory `/lib/firmware/v4l-dvb/v4l'
No version yet, using 2.6.32-21-generic
make[1]: Leaving directory `/lib/firmware/v4l-dvb/v4l'
make[1]: Entering directory `/lib/firmware/v4l-dvb/v4l'
./scripts/make_kconfig.pl /lib/modules/2.6.32-21-generic/build /lib/modules/2.6.32-21-generic/build
Preparing to compile for kernel version 2.6.32

***WARNING:*** You do not have the full kernel sources installed.
This does not prevent you from building the v4l-dvb tree if you have the
kernel headers, but the full kernel source may be required in order to use
make menuconfig / xconfig / qconfig.

If you are experiencing problems building the v4l-dvb tree, please try
building against a vanilla kernel before reporting a bug.

Vanilla kernels are available at http://kernel.org.
On most distros, this will compile a newly downloaded kernel:

cp /boot/config-`uname -r` <your kernel dir>/.config
cd <your kernel dir>
make all modules_install install

Please see your distro's web site for instructions to build a new kernel.

WARNING: This is the V4L/DVB backport tree, with experimental drivers
     backported to run on legacy kernels from the development tree at:
        http://git.linuxtv.org/media-tree.git.
     It is generally safe to use it for testing a new driver or
     feature, but its usage on production environments is risky.
     Don't use it in production. You've been warned.
LIRC: Requires at least kernel 2.6.36
IR_LIRC_CODEC: Requires at least kernel 2.6.36
IR_IMON: Requires at least kernel 2.6.36
IR_MCEUSB: Requires at least kernel 2.6.36
V4L2_MEM2MEM_DEV: Requires at least kernel 2.6.33
VIDEO_TVP7002: Requires at least kernel 2.6.34
VIDEO_AK881X: Requires at least kernel 2.6.33
SOC_CAMERA: Requires at least kernel 2.6.33
SOC_CAMERA_MT9M001: Requires at least kernel 2.6.33
SOC_CAMERA_MT9M111: Requires at least kernel 2.6.33
SOC_CAMERA_MT9T031: Requires at least kernel 2.6.33
SOC_CAMERA_MT9V022: Requires at least kernel 2.6.33
SOC_CAMERA_TW9910: Requires at least kernel 2.6.33
SOC_CAMERA_PLATFORM: Requires at least kernel 2.6.33
SOC_CAMERA_OV772X: Requires at least kernel 2.6.33
RADIO_SAA7706H: Requires at least kernel 2.6.34
Created default (all yes) .config file
/lib/modules/2.6.32-21-generic/build/scripts/kconfig/mconf ./Kconfig
#
# configuration written to .config
#


*** End of Linux kernel configuration.
*** Execute 'make' to build the kernel or try 'make help'.

./scripts/fix_kconfig.pl
make[1]: Leaving directory `/lib/firmware/v4l-dvb/v4l'

```Output from make comand
```
ayasugi@ayasugi-desktop:/lib/firmware/v4l-dvb$ make -j5
make -C /lib/firmware/v4l-dvb/v4l 
make[1]: Entering directory `/lib/firmware/v4l-dvb/v4l'
scripts/make_makefile.pl
./scripts/make_myconfig.pl
Unable to write Makefile.media at scripts/make_makefile.pl line 201.
perl scripts/make_config_compat.pl /lib/modules/2.6.32-21-generic/build ./.myconfig ./config-compat.h
make[1]: *** No rule to make target `Makefile.media', needed by `default'.  Stop.
make[1]: *** Waiting for unfinished jobs....
File not found: ./.myconfig at scripts/make_config_compat.pl line 384.
make[1]: *** [config-compat.h] Error 2
make[1]: Leaving directory `/lib/firmware/v4l-dvb/v4l'
make: *** [all] Error 2

``` Do i need to update my kernel? install headers? Id rather not update the kernel, because i have had a great deal of trouble getting nvidia's drivers to work on my system with both my monitors.  A kernel update would mean repeating all of that.

---

### Post by Ayasugi on 2010-11-15
No one can help? 
bump.

---

### Post by Cheltspy on 2010-11-25
Why are you using sudo make menuconfig ? ... It is best to install everything and sudo isn't reguired.

If your having trouble undo your sudo

sudo make distclean

make

sudo make install

**note with Ubuntu quit the make on first attempt with ctrl z and

gedit v4l/.config 

find and change to
CONFIG_DVB_FIREDTV=n

You only need to use sudo to install.

Edit:
I assume you had used 
hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

If you really do want to make menuconfig
sudo bash (this will ask for password to continue as root)
make menuconfig

---

