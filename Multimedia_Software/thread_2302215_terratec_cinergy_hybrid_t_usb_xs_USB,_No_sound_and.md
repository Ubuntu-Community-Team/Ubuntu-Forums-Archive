---
title: "terratec cinergy hybrid t usb xs USB, No sound and VLC does not seek channels"
date: 2015-11-08
forum: Multimedia Software
---

### Post by ecomp2015 on 2015-11-08
Good morning


I sold and bought a previous tuner tuner
terratec cinergy hybrid t usb xs USB


the configuration error pops up


$ hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
$ cd v4l-dvb


After entering the terminal command "make"


pops up an error

```





root@fcomp:/home/fcomp/v4l-dvb# sudo make
make -C /home/fcomp/v4l-dvb/v4l 
make[1]: Wej&#347;cie do katalogu '/home/fcomp/v4l-dvb/v4l'
No version yet, using 4.2.0-17-generic
scripts/make_makefile.pl
Updating/Creating .config
Preparing to compile for kernel version 4.2.0


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


WARNING: You're using an obsolete driver! You shouldn't be using it!
	 If you want anything new, you can use:
		http://git.linuxtv.org/media_build.git.
	 The tree is still here just to preserve the development history.
	 You've been warned.
Created default (all yes) .config file
./scripts/make_myconfig.pl
perl scripts/make_config_compat.pl /lib/modules/4.2.0-17-generic/build ./.myconfig ./config-compat.h
creating symbolic links...
ln -sf . oss
make -C firmware prep
make[2]: Entering directory '/home/fcomp/v4l-dvb/v4l/firmware'
make[2]: Leaving directory '/home/fcomp/v4l-dvb/v4l/firmware'
make -C firmware
make[2]: Entering directory '/home/fcomp/v4l-dvb/v4l/firmware'
  CC  ihex2fw
Generating vicam/firmware.fw
Generating dabusb/firmware.fw
Generating dabusb/bitstream.bin
Generating ttusb-budget/dspbootcode.bin
Generating cpia2/stv0672_vp4.bin
Generating av7110/bootcode.bin
make[2]: Leaving directory '/home/fcomp/v4l-dvb/v4l/firmware'
Kernel build directory is /lib/modules/4.2.0-17-generic/build
make -C /lib/modules/4.2.0-17-generic/build SUBDIRS=/home/fcomp/v4l-dvb/v4l CFLAGS="-I../linux/include -D__KERNEL__ -I/include -DEXPORT_SYMTAB" modules
make[2]: Entering directory '/usr/src/linux-headers-4.2.0-17-generic'
  CC [M]  /home/fcomp/v4l-dvb/v4l/tuner-xc2028.o
cc1: fatal error: include/linux/version.h: No such file or directory
compilation terminated.
scripts/Makefile.build:264: polecenia dla obiektu '/home/fcomp/v4l-dvb/v4l/tuner-xc2028.o' nie powiod&#322;y si&#281;
make[3]: *** [/home/fcomp/v4l-dvb/v4l/tuner-xc2028.o] B&#322;&#261;d 1
Makefile:1398: recipe for target '_module_/home/fcomp/v4l-dvb/v4l' failed
make[2]: *** [_module_/home/fcomp/v4l-dvb/v4l] Error 2
make[2]: Leaving directory '/usr/src/linux-headers-4.2.0-17-generic'
Makefile:43: polecenia dla obiektu 'default' nie powiod&#322;y si&#281;
make[1]: *** [default] B&#322;&#261;d 2
make[1]: Opuszczenie katalogu '/home/fcomp/v4l-dvb/v4l'
Makefile:27: polecenia dla obiektu 'all' nie powiod&#322;y si&#281;
make: *** [all] B&#322;&#261;d 2
root@fcomp:/home/fcomp/v4l-dvb# 



```





stop
$ sudo make install


but the program tvtime is it, no problem but there is no sound.
After starting in the terminal "tvtime"
 ```

tvtime

```
pops up an error
```

ALSA: Can not open capture device hw: 1,0: Device or resource busy

```


device hw:1,0 is a bug wants to set hw: 0,0 or hw:0 just do not know how


Please help voice settings in the tvtime.
The same VLC does not search for analogue and digital channels
in other programs DVB-T works flawlessly

2.
On the Internet I found the program to launch the settings for tvtime
now I can not find it, using this program option enabled voice in the table, but not explicit maybe someone knows this program.
If anyone knows this command to tvtime please enter
of which advance thank you very much
Thank you for your help

---

