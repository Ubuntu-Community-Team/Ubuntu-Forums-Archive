---
title: "Dvb-t2"
date: 2011-04-29
forum: Multimedia Software
---

### Post by jon890 on 2011-04-29
There seems to be no work being done to produce a driver for the (Hauppauge) PCTV Nano 290e Freeview HD USB stick, or any other Freeview HD stick. Linux TV Org has the stick as unknown, yet it has been out for a while, Hauppauge Tuner drivers were usually quickly available.
Presumably in the UK we have to revert to Windows 7 for Freeview HD, I don't want to have to use Windows but keep being forced back into it, particularly as Windows 7 seems to have most drivers already included.

---

### Post by robho on 2011-05-02
There is an experimental driver available for the USB stick you mention. Check here: [http://stevekerrison.com/290e/index.html](http://stevekerrison.com/290e/index.html)

linuxtv.org has been updated with a link to the experimental driver.

Also the BGT 3620 card will get drivers Q3 2011.

But, drivers isn't enough. There needs to be DVB-T2 support in APIs and applications and that's not in place yet.

So, things are actually moving forward.

---

### Post by Wrapperband-0 on 2011-07-29
Help - I am relatively new to Linux Ubuntu and have 11.04 x64. I have managed to get my 290e DVB-T2 USB stick working with the experimental .git on LinuxTV.org. However, there is no sound / no audio when watching the HD Freeview channels in either Kaffeine or MeTV. The DVB-T2 HD video stream works.

I have reinstalled (build) the .git repository a number of times and did get some HD sound with VLC, so it can be done. However VLC was impractical to watch (I had to do a full channel scan each time I started it up)

I did notice some advice to change Buffers in a config file HD get sound on DVB-S2, so maybe it could be that. Or it could be MeTV and Kaffeine need updating?

Has anyone got sound on Freeview HD, or any idea what I might try to get the audio / sound going when viewing HD TV?

Is it because the HD sound is AC3  and the stereo is not being decoded from 5.1 ??

At the moment I'm just watching the normal channels through the 290e (USB stick) and MeTV - (Hauppauge) PCTV Nano 290e Freeview HD USB stick

I have tried updating Kaffeine to 1.2.2. 

I have also tried updating Me TV to the latest version 2.01 - which is a download ./configure, make , make install. Despite a lot of trying (updating dependencies) this wouldn't compile. Has anyone else managed to compile MeTv 2.01 on Ubuntu? If so, any tips?

Wrapperband

---

### Post by eexcellent on 2011-08-04
I have the same problem, no sound with kaffeine on hd channels
ubuntu 10.10 64bit
kaffeine 1.1-0ubuntu1
pctv290e

Any help please?

---

### Post by Wrapperband-0 on 2011-08-12
Please Help

Is there anyone who has got Freeview HD TV dvb-t2 working with audio in Ubuntu 11.04 at all? 

Is there a way of using VLC to view HD programs and save the channel list?

Wrapperband

---

### Post by eexcellent on 2011-08-20
This might help:

[HTML]http://ubuntuforums.org/showthread.php?t=967862[/HTML]

---

### Post by Wrapperband-0 on 2011-09-08
Hi, thanks for the links to "How to create a TV channel list for VLC media player". 

I am relatively newbie, and am finding that explanation of how to set up VLC quite complicated and haven't got it to work. 
I have given up trying to find how to get scan to generate a config file in the correct directory for the moment. I'll have another go, when I have a spare hour.

I am still interested to find if anyone has got Audio working with UK,  HD Freeview. 

I have a DVB-T2 USB stick (290e). I can watch all the normal programs with Kaffeine 1.2.2 or MeTV 1.3.6 , using the LinuxTV.org experimental git. My system is Ubuntu 11.04 with KDE added and 2.6.38-11 generic kernel.

The lack of audio seems to be a problem that the system is not using the correct audio codec to decode the HD TV signal. I believe both Me and Kaffeine could decode ac3 on other files types? So it isn't a problem of a missing codec?

---

### Post by howefield on 2011-09-08
> **Wrapperband-0 said:**
> I am relatively newbie, and am finding that explanation of how to set up VLC quite complicated and haven't got it to work. 
I have given up trying to find how to get scan to generate a config file in the correct directory for the moment. I'll have another go, when I have a spare hour.

Can't help you with the HD audio query but for creating a config.conf file try installing dvb-apps if not installed already and run the following command..

```
scan /usr/share/dvb/dvb-t/uk-Darvel -o zap | tee ~/channels.conf
```

Substitute the Darvel part with the name of your local transmitter, if unsure I think you will find the available list in the /usr/share/dvb/dvb-t folder.

Assuming you produce the config.conf file, open vlc and from the Media menu select Open Advanced File and the rest should be self explanatory.

---

### Post by Wrapperband-0 on 2011-09-10
Cheers for that information, 

I managed to create the channels.conf file, which appeared in my home directory by using those instructions.

Unfortunately, when I scan my normal transmitter  uk-Winterhill it comes back - tuning failed!!!

uk-Winterhill is the transmitter I use with Me-tv and Kaffiene.

I re scanned for uk-Saddleworth - which created the channels.conf file - but only  some of the Freeveiw TV programs are available on that transmitter, not HD. 

I assume there might be other settings of scan needed, + I may need to use 2 transmitters, and the above instructions seem to blank the file with each scan?

---

### Post by BicyclerBoy on 2011-09-10
The dvb-t2 in UK is using AAC & optional dolby digital plus.
The problem **could be** the audio is muxed using LOAS/LATM.
This is the case with dvb-t HD broadcasts in my corner & most places..

LATM AAC was supported by MythTV & VLC for last 3 years.

If you can work out how to tune the card you can 'cat' the card output stream into a file.
Then point 'mediainfo' at the file..

I think kaffeine is **xine** based, you could go looking for a xine update.
[http://old.nabble.com/-PATCH--Add-AAC-LATM-support-from-FFmpeg-0.7%2B-td32355161.html](http://old.nabble.com/-PATCH--Add-AAC-LATM-support-from-FFmpeg-0.7%2B-td32355161.html)

The tuning problems could be resource sharing, for e.g. mythtv backend does not share the tuner cards.

---

### Post by howefield on 2011-09-11
> **Wrapperband-0 said:**
> ... and the above instructions seem to blank the file with each scan?

Change the file name before doing the second scan. The file doesn't have to be named channels.conf, could be maninthemoon.conf or whatever you like. :)

Eg,

```
scan /usr/share/dvb/dvb-t/uk-Darvel -o zap | tee ~/maninthemoon.conf
```

---

### Post by Wrapperband-0 on 2011-11-25
Help - since the 2nd November 2011 - I have not been able to build the linuxtv.org media experimental git.

It may have been due to upgrading the kernel to 3.0.0 , but I have run <make distclean> and the compile it is pointing to the correct directories.

Hans Verkuil
2011-11-02 Mauro Carvalho... Fix compilation for staging drivers
2011-10-11  Igor M. Liplianin

 ** There are no simple instructions on how to do a new post in this forum, I've only got a PhD, so I'm hoping there will be an option to make this a new post, as I can't find any other way of doing it. Please feel free to bump this to a new thread**

These are the main error messages that now come up during the build in terminal...

The final message

CC [M]  /home/tony/media_build/v4l/benq.o
/home/tony/media_build/v4l/benq.c:21:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/tony/media_build/v4l/conex.o
/home/tony/media_build/v4l/conex.c:22:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
/home/tony/media_build/v4l/conex.c:46:14: error: 'JPEG_HDR_SZ' undeclared here (not in a function)
/home/tony/media_build/v4l/conex.c: In function 'sd_start':
/home/tony/media_build/v4l/conex.c:850:2: error: implicit declaration of function 'jpeg_define' [-Werror=implicit-function-declaration]
/home/tony/media_build/v4l/conex.c:852:2: error: implicit declaration of function 'jpeg_set_qual' [-Werror=implicit-function-declaration]
/home/tony/media_build/v4l/conex.c: At top level:
/home/tony/media_build/v4l/jpeg.h:23:22: warning: 'jpeg_header' defined but not used [-Wunused-variable]
cc1: some warnings being treated as errors

make[3]: *** [/home/tony/media_build/v4l/conex.o] Error 1
make[2]: *** [_module_/home/tony/media_build/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.0.0-14-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/tony/media_build/v4l'
make: *** [all] Error 2
build failed at ./build line 380.
----------------------------------------------

Other main messages from the top:

****************************
Updating the building system
****************************
remote: Counting objects: 9, done.
remote: Compressing objects: 100% (5/5), done.
remote: Total 5 (delta 4), reused 0 (delta 0)
Unpacking objects: 100% (5/5), done.
From git://linuxtv.org/media_build
 * branch            master     -> FETCH_HEAD
Updating 18eb796..6ac08a5
Fast-forward
 build            |    8 ++++----
 linux/use_dir.pl |    4 ++--
 2 files changed, 6 insertions(+), 6 deletions(-)
make: Entering directory `/home/tony/media_build/linux'
wget [http://linuxtv.org/downloads/drivers/linux-media-LATEST.tar.bz2.md5](http://linuxtv.org/downloads/drivers/linux-media-LATEST.tar.bz2.md5) -O linux-media.tar.bz2.md5.tmp
--2011-11-25 10:14:19--  [http://linuxtv.org/downloads/drivers/linux-media-LATEST.tar.bz2.md5](http://linuxtv.org/downloads/drivers/linux-media-LATEST.tar.bz2.md5)
Resolving linuxtv.org... 130.149.80.248
Connecting to linuxtv.org|130.149.80.248|:80... connected.
HTTP request sent, awaiting response... 200 OK                                                                                                                     
Length: 93 [application/x-bzip2]                                                                                                                                   
Saving to: `linux-media.tar.bz2.md5.tmp'                                                                                                                           
                                                                                                                                                                   
100%[=========================================================================================================================>] 93          --.-K/s   in 0s       
                                                                                                                                                                   
2011-11-25 10:14:20 (9.13 MB/s) - `linux-media.tar.bz2.md5.tmp' saved [93/93]                                                                                      
                                                                                                                                                                   
--2011-11-25 10:14:20--  [http://linuxtv.org/downloads/drivers/linux-media-LATEST.tar.bz2](http://linuxtv.org/downloads/drivers/linux-media-LATEST.tar.bz2)                                                                           
Resolving linuxtv.org... 130.149.80.248                                                                                                                            
Connecting to linuxtv.org|130.149.80.248|:80... connected.                                                                                                         
HTTP request sent, awaiting response... 200 OK                                                                                                                     
Length: 4211573 (4.0M) [application/x-bzip2]                                                                                                                       
Saving to: `linux-media.tar.bz2'                                                                                                                                   

100%[=========================================================================================================================>] 4,211,573   1.03M/s   in 4.0s    

2011-11-25 10:14:24 (1020 KB/s) - `linux-media.tar.bz2' saved [4211573/4211573]

make: Leaving directory `/home/tony/media_build/linux'
make: Entering directory `/home/tony/media_build/linux'
tar xfj linux-media.tar.bz2
rm -f .patches_applied .linked_dir .git_log.md5
make: Leaving directory `/home/tony/media_build/linux'
**********************************************************
* Downloading firmwares from linuxtv.org.                *
**********************************************************
dvb-fe-bcm3510-01.fw
dvb-fe-or51132-qam.fw

<----------------------------------->

v4l-cx25840.fw
******************
* Start building *
******************
make -C /home/tony/media_build/v4l allyesconfig
make[1]: Entering directory `/home/tony/media_build/v4l'
make[2]: Entering directory `/home/tony/media_build/linux'
Applying patches for kernel 3.0.0-14-generic
patch -s -f -N -p1 -i ../backports/api_version.patch
patch -s -f -N -p1 -i ../backports/v3.1_no_export_h.patch
patch -s -f -N -p1 -i ../backports/v3.1_no_pm_qos.patch
patch -s -f -N -p1 -i ../backports/no_atomic_include.patch
patch -s -f -N -p1 -i ../backports/v4l2-compat-timespec.patch
Patched drivers/media/dvb/dvb-core/dvbdev.c
Patched drivers/media/video/v4l2-dev.c
Patched drivers/media/rc/rc-main.c
make[2]: Leaving directory `/home/tony/media_build/linux'
./scripts/make_kconfig.pl /lib/modules/3.0.0-14-generic/build /lib/modules/3.0.0-14-generic/build 1
Preparing to compile for kernel version 3.0.0

***WARNING:*** You do not have the full kernel sources installed.
This does not prevent you from building the v4l-dvb tree if you have the
kernel headers, but the full kernel source may be required in order to use
make menuconfig / xconfig / qconfig.

If you are experiencing problems building the v4l-dvb tree, please try
building against a vanilla kernel before reporting a bug.

Vanilla kernels are available at [http://kernel.org](http://kernel.org).
On most distros, this will compile a newly downloaded kernel:

cp /boot/config-`uname -r` <your kernel dir>/.config
cd <your kernel dir>
make all modules_install install

Please see your distro's web site for instructions to build a new kernel.

WARNING: This is the V4L/DVB backport tree, with experimental drivers
         backported to run on legacy kernels from the development tree at:
                [http://git.linuxtv.org/media-tree.git](http://git.linuxtv.org/media-tree.git).
         It is generally safe to use it for testing a new driver or
         feature, but its usage on production environments is risky.
         Don't use it in production. You've been warned.
SOC_CAMERA: Requires at least kernel 3.2.0
SOC_CAMERA_MT9M001: Requires at least kernel 3.2.0
SOC_CAMERA_MT9M111: Requires at least kernel 3.2.0
SOC_CAMERA_MT9T031: Requires at least kernel 3.2.0
SOC_CAMERA_MT9V022: Requires at least kernel 3.2.0
SOC_CAMERA_TW9910: Requires at least kernel 3.2.0
SOC_CAMERA_PLATFORM: Requires at least kernel 3.2.0
SOC_CAMERA_OV772X: Requires at least kernel 3.2.0
Created default (all yes) .config file
./scripts/fix_kconfig.pl
make[1]: Leaving directory `/home/tony/media_build/v4l'
make -C /home/tony/media_build/v4l 
make[1]: Entering directory `/home/tony/media_build/v4l'
./scripts/make_myconfig.pl
make[1]: Leaving directory `/home/tony/media_build/v4l'
make[1]: Entering directory `/home/tony/media_build/v4l'
perl scripts/make_config_compat.pl /lib/modules/3.0.0-14-generic/build ./.myconfig ./config-compat.h
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/tony/media_build/v4l/firmware'
make[2]: Leaving directory `/home/tony/media_build/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/tony/media_build/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/tony/media_build/v4l/firmware'
Kernel build directory is /lib/modules/3.0.0-14-generic/build
make -C ../linux apply_patches
make[2]: Entering directory `/home/tony/media_build/linux'
Patches for 3.0.0-14-generic already applied.
make[2]: Leaving directory `/home/tony/media_build/linux'
make -C /lib/modules/3.0.0-14-generic/build SUBDIRS=/home/tony/media_build/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-3.0.0-14-generic'
  CC [M]  /home/tony/media_build/v4l/altera-lpt.o
  CC [M]  /home/tony/media_build/v4l/altera-jtag.o
  CC [M]  /home/tony/media_build/v4l/altera-comp.o
  CC [M]  /home/tony/media_build/v4l/altera.o
  CC [M]  /home/tony/media_build/v4l/au0828-core.o
  CC [M]  /home/tony/media_build/v4l/au0828-i2c.o

<------------------------------------------------------------------>

CC [M]  /home/tony/media_build/v4l/flexcop-dma.o
  CC [M]  /home/tony/media_build/v4l/bttv-driver.o
/home/tony/media_build/v4l/bttv-driver.c:37:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/tony/media_build/v4l/bttv-cards.o
/home/tony/media_build/v4l/bttv-cards.c:28:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/tony/media_build/v4l/bttv-if.o
  CC [M]  /home/tony/media_build/v4l/bttv-risc.o
/home/tony/media_build/v4l/bttv-risc.c:27:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/tony/media_build/v4l/bttv-vbi.o
/home/tony/media_build/v4l/bttv-vbi.c:26:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/tony/media_build/v4l/bttv-i2c.o
/home/tony/media_build/v4l/bttv-i2c.c:30:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/tony/media_build/v4l/bttv-gpio.o
/home/tony/media_build/v4l/bttv-gpio.c:29:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
/home/tony/media_build/v4l/bttv-gpio.c:29:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/tony/media_build/v4l/bttv-input.o
/home/tony/media_build/v4l/bttv-input.c:21:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/tony/media_build/v4l/bttv-audio-hook.o
  CC [M]  /home/tony/media_build/v4l/cafe-driver.o
  CC [M]  /home/tony/media_build/v4l/mcam-core.o

<------------------------------------------------------------->

Cheers for any help, I have tried everything I can think of, and have searched for anyone with the same problem...

I (think) I need the v4l drivers for the 290e PCTV dvb-t2, hoping that HD will get sorted on Linux. I also use 2 web cams, but I now think they may use v4l2 with some applications.

Dr T

---

### Post by Wrapperband-0 on 2011-11-30
Please help. 

The Nightly build has been updated but I still can't compile it. As no one else seems to be having the same trouble, what am I doing wrong?

Error message when trying to ./build media v4l experimental git at linuxtv.org. TV drivers for Linux / Ubuntu won't compile. I am using 64 bit Kubuntu, with 3.0.0.14 kernel. It was working every time before 2 November 2011.

Dr T

---

### Post by Wrapperband-0 on 2011-12-15
Please help - now up to 3.0.0.15 kernel, and still can't build v4l git at linuxtv.org.

include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/tony/media_build/v4l/conex.o
/home/tony/media_build/v4l/conex.c:22:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
/home/tony/media_build/v4l/conex.c:46:14: error: 'JPEG_HDR_SZ' undeclared here (not in a function)
/home/tony/media_build/v4l/conex.c: In function 'sd_start':
/home/tony/media_build/v4l/conex.c:850:2: error: implicit declaration of function 'jpeg_define' [-Werror=implicit-function-declaration]
/home/tony/media_build/v4l/conex.c:852:2: error: implicit declaration of function 'jpeg_set_qual' [-Werror=implicit-function-declaration]
/home/tony/media_build/v4l/conex.c: At top level:
/home/tony/media_build/v4l/jpeg.h:23:22: warning: 'jpeg_header' defined but not used [-Wunused-variable]
cc1: some warnings being treated as errors

make[3]: *** [/home/tony/media_build/v4l/conex.o] Error 1
make[2]: *** [_module_/home/tony/media_build/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.0.0-15-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/tony/media_build/v4l'
make: *** [all] Error 2
build failed at ./build line 380.

---

### Post by BicyclerBoy on 2011-12-15
Wild guess but..
Are you sure you have the linux kernel headers package installed that matches your kernel ?

I can't tell from the error messages what is the root cause..

---

### Post by Wrapperband-0 on 2011-12-18
sudo apt-get install linux-headers-`uname -r`

I thought I did go through the procedure of having the kernel headers downloaded, and included in the package manager. 
I'll check again and see if they are highlighted in Muon package manager, if not I'll run the install command above.

Let you know if that fixes it.

>>>>>>>>>>
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.0.0-15-generic is already the newest version.
linux-headers-3.0.0-15-generic set to manually installed.

Hertes the full terminal printout - including distclean >>>>>>>>>>>>>>>

tony@wrapperband:~$ cd media_build
tony@wrapperband:~/media_build$ sudo make distclean
[sudo] password for tony: 
make -C /home/tony/media_build/v4l distclean
make[1]: Entering directory `/home/tony/media_build/v4l'
rm -f *~ *.o *.ko .*.o.cmd .*.ko.cmd *.mod.c av7110_firm.h fdump \
                config-compat.h Module.symvers Module.markers modules.order \
                *.unsigned .*.ko.unsigned.cmd
make -C firmware clean
make[2]: Entering directory `/home/tony/media_build/v4l/firmware'
rm -f ihex2fw
rm -f vicam/firmware.fw dabusb/firmware.fw dabusb/bitstream.bin ttusb-budget/dspbootcode.bin cpia2/stv0672_vp4.bin av7110/bootcode.bin
make[2]: Leaving directory `/home/tony/media_build/v4l/firmware'
rm -f .version .*.o.flags .*.o.d Makefile.media \
                Kconfig Kconfig.kern .config .config.cmd .myconfig \
                .kconfig.dep
rm -rf .tmp_versions .tmp*.ver .tmp*.o
rm -f scripts/lxdialog scripts/kconfig
make -C firmware distclean
make[2]: Entering directory `/home/tony/media_build/v4l/firmware'
rm -f ihex2fw
rm -f vicam/firmware.fw dabusb/firmware.fw dabusb/bitstream.bin ttusb-budget/dspbootcode.bin cpia2/stv0672_vp4.bin av7110/bootcode.bin
for i in av7110/ cpia2/ dabusb/ ttusb-budget/ vicam/; do if [ -d $i ]; then rm -rf $i; fi; done
make[2]: Leaving directory `/home/tony/media_build/v4l/firmware'
make[1]: Leaving directory `/home/tony/media_build/v4l'
tony@wrapperband:~/media_build$ sudo ./build
Checking if the needed tools for Ubuntu 11.10 are available
Needed package dependencies are met.

************************************************************
* This script will download the latest tarball and build it*
* Assuming that your kernel is compatible with the latest  *
* drivers. If not, you'll need to add some extra backports,*
* ./backports/<kernel> directory.                          *
* It will also update this tree to be sure that all compat *
* bits are there, to avoid compilation failures            *
************************************************************
************************************************************
* All drivers and build system are under GPLv2 License     *                                                            
* Firmware files are under the license terms found at:     *                                                            
* [http://www.linuxtv.org/downloads/firmware/](http://www.linuxtv.org/downloads/firmware/)               *                                                            
* Please abort if you don't agree with the license         *                                                            
************************************************************                                                            
                                                                                                                        
****************************                                                                                            
Updating the building system                                                                                            
****************************                                                                                            
From git://linuxtv.org/media_build                                                                                      
 * branch            master     -> FETCH_HEAD                                                                           
Already up-to-date.                                                                                                     
make: Entering directory `/home/tony/media_build/linux'                                                                 
wget [http://linuxtv.org/downloads/drivers/linux-media-LATEST.tar.bz2.md5](http://linuxtv.org/downloads/drivers/linux-media-LATEST.tar.bz2.md5) -O linux-media.tar.bz2.md5.tmp                 
--2011-12-18 12:59:55--  [http://linuxtv.org/downloads/drivers/linux-media-LATEST.tar.bz2.md5](http://linuxtv.org/downloads/drivers/linux-media-LATEST.tar.bz2.md5)                            
Resolving linuxtv.org... 130.149.80.248                                                                                 
Connecting to linuxtv.org|130.149.80.248|:80... connected.                                                              
HTTP request sent, awaiting response... 200 OK                                                                          
Length: 93 [application/x-bzip2]
Saving to: `linux-media.tar.bz2.md5.tmp'

100%[==============================================================================>] 93          --.-K/s   in 0s      

2011-12-18 12:59:56 (9.04 MB/s) - `linux-media.tar.bz2.md5.tmp' saved [93/93]

make: Leaving directory `/home/tony/media_build/linux'
make: Entering directory `/home/tony/media_build/linux'
tar xfj linux-media.tar.bz2
rm -f .patches_applied .linked_dir .git_log.md5
make: Leaving directory `/home/tony/media_build/linux'
**********************************************************
* Downloading firmwares from linuxtv.org.                *
**********************************************************
dvb-fe-bcm3510-01.fw
dvb-fe-or51132-qam.fw
dvb-fe-or51132-vsb.fw
dvb-fe-or51211.fw
dvb-fe-xc5000-1.6.114.fw
dvb-ttpci-01.fw-261a
dvb-ttpci-01.fw-261b
dvb-ttpci-01.fw-261c
dvb-ttpci-01.fw-261d
dvb-ttpci-01.fw-261f
dvb-ttpci-01.fw-2622
dvb-usb-avertv-a800-02.fw
dvb-usb-bluebird-01.fw
dvb-usb-dib0700-1.20.fw
dvb-usb-dibusb-5.0.0.11.fw
dvb-usb-dibusb-6.0.0.8.fw
dvb-usb-dtt200u-01.fw
dvb-usb-terratec-h5-drxk.fw
dvb-usb-terratec-h7-az6007.fw
dvb-usb-terratec-h7-drxk.fw
dvb-usb-umt-010-02.fw
dvb-usb-vp702x-01.fw
dvb-usb-vp7045-01.fw
dvb-usb-wt220u-01.fw
dvb-usb-wt220u-02.fw
v4l-cx231xx-avcore-01.fw
v4l-cx23418-apu.fw
v4l-cx23418-cpu.fw
v4l-cx23418-dig.fw
v4l-cx23885-avcore-01.fw
v4l-cx23885-enc.fw
v4l-cx25840.fw
******************
* Start building *
******************
make -C /home/tony/media_build/v4l allyesconfig
make[1]: Entering directory `/home/tony/media_build/v4l'
No version yet, using 3.0.0-15-generic
make[1]: Leaving directory `/home/tony/media_build/v4l'
make[1]: Entering directory `/home/tony/media_build/v4l'
make[2]: Entering directory `/home/tony/media_build/linux'
Applying patches for kernel 3.0.0-15-generic
patch -s -f -N -p1 -i ../backports/api_version.patch
patch -s -f -N -p1 -i ../backports/v3.1_no_export_h.patch
patch -s -f -N -p1 -i ../backports/v3.1_no_pm_qos.patch
patch -s -f -N -p1 -i ../backports/no_atomic_include.patch
patch -s -f -N -p1 -i ../backports/v4l2-compat-timespec.patch
Patched drivers/media/dvb/dvb-core/dvbdev.c
Patched drivers/media/video/v4l2-dev.c
Patched drivers/media/rc/rc-main.c
make[2]: Leaving directory `/home/tony/media_build/linux'
./scripts/make_kconfig.pl /lib/modules/3.0.0-15-generic/build /lib/modules/3.0.0-15-generic/build 1
Preparing to compile for kernel version 3.0.0

***WARNING:*** You do not have the full kernel sources installed.
This does not prevent you from building the v4l-dvb tree if you have the
kernel headers, but the full kernel source may be required in order to use
make menuconfig / xconfig / qconfig.

If you are experiencing problems building the v4l-dvb tree, please try
building against a vanilla kernel before reporting a bug.

Vanilla kernels are available at [http://kernel.org](http://kernel.org).
On most distros, this will compile a newly downloaded kernel:

cp /boot/config-`uname -r` <your kernel dir>/.config
cd <your kernel dir>
make all modules_install install

Please see your distro's web site for instructions to build a new kernel.

WARNING: This is the V4L/DVB backport tree, with experimental drivers
         backported to run on legacy kernels from the development tree at:
                [http://git.linuxtv.org/media-tree.git](http://git.linuxtv.org/media-tree.git).
         It is generally safe to use it for testing a new driver or
         feature, but its usage on production environments is risky.
         Don't use it in production. You've been warned.
SOC_CAMERA: Requires at least kernel 3.2.0
SOC_CAMERA_MT9M001: Requires at least kernel 3.2.0
SOC_CAMERA_MT9M111: Requires at least kernel 3.2.0
SOC_CAMERA_MT9T031: Requires at least kernel 3.2.0
SOC_CAMERA_MT9V022: Requires at least kernel 3.2.0
SOC_CAMERA_TW9910: Requires at least kernel 3.2.0
SOC_CAMERA_PLATFORM: Requires at least kernel 3.2.0
SOC_CAMERA_OV772X: Requires at least kernel 3.2.0
Created default (all yes) .config file
./scripts/fix_kconfig.pl
make[1]: Leaving directory `/home/tony/media_build/v4l'
make -C /home/tony/media_build/v4l 
make[1]: Entering directory `/home/tony/media_build/v4l'
scripts/make_makefile.pl
./scripts/make_myconfig.pl
make[1]: Leaving directory `/home/tony/media_build/v4l'
make[1]: Entering directory `/home/tony/media_build/v4l'
perl scripts/make_config_compat.pl /lib/modules/3.0.0-15-generic/build ./.myconfig ./config-compat.h
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/tony/media_build/v4l/firmware'
make[2]: Leaving directory `/home/tony/media_build/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/tony/media_build/v4l/firmware'
  CC  ihex2fw
Generating vicam/firmware.fw
Generating dabusb/firmware.fw
Generating dabusb/bitstream.bin
Generating ttusb-budget/dspbootcode.bin
Generating cpia2/stv0672_vp4.bin
Generating av7110/bootcode.bin
make[2]: Leaving directory `/home/tony/media_build/v4l/firmware'
Kernel build directory is /lib/modules/3.0.0-15-generic/build
make -C ../linux apply_patches
make[2]: Entering directory `/home/tony/media_build/linux'
Patches for 3.0.0-15-generic already applied.
make[2]: Leaving directory `/home/tony/media_build/linux'
make -C /lib/modules/3.0.0-15-generic/build SUBDIRS=/home/tony/media_build/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-3.0.0-15-generic'
  CC [M]  /home/tony/media_build/v4l/altera-lpt.o
  CC [M]  /home/tony/media_build/v4l/altera-jtag.o
  CC [M]  /home/tony/media_build/v4l/altera-comp.o
  CC [M]  /home/tony/media_build/v4l/altera.o
  CC [M]  /home/tony/media_build/v4l/au0828-core.o
  CC [M]  /home/tony/media_build/v4l/au0828-i2c.o
  CC [M]  /home/tony/media_build/v4l/au0828-cards.o
  CC [M]  /home/tony/media_build/v4l/au0828-dvb.o
  CC [M]  /home/tony/media_build/v4l/au0828-video.o
  CC [M]  /home/tony/media_build/v4l/au0828-vbi.o
  CC [M]  /home/tony/media_build/v4l/au8522_dig.o
  CC [M]  /home/tony/media_build/v4l/au8522_decoder.o
  CC [M]  /home/tony/media_build/v4l/flexcop-pci.o
  CC [M]  /home/tony/media_build/v4l/flexcop-usb.o
  CC [M]  /home/tony/media_build/v4l/flexcop.o
  CC [M]  /home/tony/media_build/v4l/flexcop-fe-tuner.o
  CC [M]  /home/tony/media_build/v4l/flexcop-i2c.o
  CC [M]  /home/tony/media_build/v4l/flexcop-sram.o
  CC [M]  /home/tony/media_build/v4l/flexcop-eeprom.o
  CC [M]  /home/tony/media_build/v4l/flexcop-misc.o
  CC [M]  /home/tony/media_build/v4l/flexcop-hw-filter.o
  CC [M]  /home/tony/media_build/v4l/flexcop-dma.o
  CC [M]  /home/tony/media_build/v4l/bttv-driver.o
/home/tony/media_build/v4l/bttv-driver.c:37:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/tony/media_build/v4l/bttv-cards.o
/home/tony/media_build/v4l/bttv-cards.c:28:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/tony/media_build/v4l/bttv-if.o
  CC [M]  /home/tony/media_build/v4l/bttv-risc.o
/home/tony/media_build/v4l/bttv-risc.c:27:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/tony/media_build/v4l/bttv-vbi.o
/home/tony/media_build/v4l/bttv-vbi.c:26:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/tony/media_build/v4l/bttv-i2c.o
/home/tony/media_build/v4l/bttv-i2c.c:30:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/tony/media_build/v4l/bttv-gpio.o
/home/tony/media_build/v4l/bttv-gpio.c:29:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
/home/tony/media_build/v4l/bttv-gpio.c:29:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/tony/media_build/v4l/bttv-input.o
/home/tony/media_build/v4l/bttv-input.c:21:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/tony/media_build/v4l/bttv-audio-hook.o
  CC [M]  /home/tony/media_build/v4l/cafe-driver.o
  CC [M]  /home/tony/media_build/v4l/mcam-core.o
  CC [M]  /home/tony/media_build/v4l/cpia2_v4l.o
  CC [M]  /home/tony/media_build/v4l/cpia2_usb.o
  CC [M]  /home/tony/media_build/v4l/cpia2_core.o
  CC [M]  /home/tony/media_build/v4l/cx18-alsa-main.o
  CC [M]  /home/tony/media_build/v4l/cx18-alsa-pcm.o
  CC [M]  /home/tony/media_build/v4l/cx18-driver.o
  CC [M]  /home/tony/media_build/v4l/cx18-cards.o
  CC [M]  /home/tony/media_build/v4l/cx18-i2c.o
  CC [M]  /home/tony/media_build/v4l/cx18-firmware.o
  CC [M]  /home/tony/media_build/v4l/cx18-gpio.o
  CC [M]  /home/tony/media_build/v4l/cx18-queue.o
  CC [M]  /home/tony/media_build/v4l/cx18-streams.o
  CC [M]  /home/tony/media_build/v4l/cx18-fileops.o
  CC [M]  /home/tony/media_build/v4l/cx18-ioctl.o
  CC [M]  /home/tony/media_build/v4l/cx18-controls.o
  CC [M]  /home/tony/media_build/v4l/cx18-mailbox.o
  CC [M]  /home/tony/media_build/v4l/cx18-vbi.o
  CC [M]  /home/tony/media_build/v4l/cx18-audio.o
  CC [M]  /home/tony/media_build/v4l/cx18-video.o
  CC [M]  /home/tony/media_build/v4l/cx18-irq.o
  CC [M]  /home/tony/media_build/v4l/cx18-av-core.o
  CC [M]  /home/tony/media_build/v4l/cx18-av-audio.o
  CC [M]  /home/tony/media_build/v4l/cx18-av-firmware.o
  CC [M]  /home/tony/media_build/v4l/cx18-av-vbi.o
  CC [M]  /home/tony/media_build/v4l/cx18-scb.o
  CC [M]  /home/tony/media_build/v4l/cx18-dvb.o
  CC [M]  /home/tony/media_build/v4l/cx18-io.o
  CC [M]  /home/tony/media_build/v4l/cx231xx-audio.o
  CC [M]  /home/tony/media_build/v4l/cx231xx-video.o
  CC [M]  /home/tony/media_build/v4l/cx231xx-i2c.o
  CC [M]  /home/tony/media_build/v4l/cx231xx-cards.o
  CC [M]  /home/tony/media_build/v4l/cx231xx-core.o
  CC [M]  /home/tony/media_build/v4l/cx231xx-avcore.o
  CC [M]  /home/tony/media_build/v4l/cx231xx-417.o
  CC [M]  /home/tony/media_build/v4l/cx231xx-pcb-cfg.o
  CC [M]  /home/tony/media_build/v4l/cx231xx-vbi.o
  CC [M]  /home/tony/media_build/v4l/cx231xx-input.o
  CC [M]  /home/tony/media_build/v4l/cx23885-cards.o
  CC [M]  /home/tony/media_build/v4l/cx23885-video.o
  CC [M]  /home/tony/media_build/v4l/cx23885-vbi.o
  CC [M]  /home/tony/media_build/v4l/cx23885-core.o
  CC [M]  /home/tony/media_build/v4l/cx23885-i2c.o
  CC [M]  /home/tony/media_build/v4l/cx23885-dvb.o
  CC [M]  /home/tony/media_build/v4l/cx23885-417.o
  CC [M]  /home/tony/media_build/v4l/cx23885-ioctl.o
  CC [M]  /home/tony/media_build/v4l/cx23885-ir.o
  CC [M]  /home/tony/media_build/v4l/cx23885-av.o
  CC [M]  /home/tony/media_build/v4l/cx23885-input.o
  CC [M]  /home/tony/media_build/v4l/cx23888-ir.o
  CC [M]  /home/tony/media_build/v4l/netup-init.o
  CC [M]  /home/tony/media_build/v4l/cimax2.o
  CC [M]  /home/tony/media_build/v4l/netup-eeprom.o
  CC [M]  /home/tony/media_build/v4l/cx23885-f300.o
  CC [M]  /home/tony/media_build/v4l/cx23885-alsa.o
  CC [M]  /home/tony/media_build/v4l/cx25821-core.o
/home/tony/media_build/v4l/cx25821-core.c:24:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
/home/tony/media_build/v4l/cx25821-core.c:24:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/tony/media_build/v4l/cx25821-cards.o
/home/tony/media_build/v4l/cx25821-cards.c:24:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/tony/media_build/v4l/cx25821-i2c.o
/home/tony/media_build/v4l/cx25821-i2c.c:24:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/tony/media_build/v4l/cx25821-gpio.o
  CC [M]  /home/tony/media_build/v4l/cx25821-medusa-video.o
/home/tony/media_build/v4l/cx25821-medusa-video.c:23:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/tony/media_build/v4l/cx25821-video.o
/home/tony/media_build/v4l/cx25821-video.c:27:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/tony/media_build/v4l/cx25821-video-upstream.o
/home/tony/media_build/v4l/cx25821-video-upstream.c:23:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/tony/media_build/v4l/cx25821-video-upstream-ch2.o
/home/tony/media_build/v4l/cx25821-video-upstream-ch2.c:23:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/tony/media_build/v4l/cx25821-audio-upstream.o
/home/tony/media_build/v4l/cx25821-audio-upstream.c:23:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/tony/media_build/v4l/cx25840-core.o
  CC [M]  /home/tony/media_build/v4l/cx25840-audio.o
  CC [M]  /home/tony/media_build/v4l/cx25840-firmware.o
  CC [M]  /home/tony/media_build/v4l/cx25840-vbi.o
  CC [M]  /home/tony/media_build/v4l/cx25840-ir.o
  CC [M]  /home/tony/media_build/v4l/cx88-video.o
  CC [M]  /home/tony/media_build/v4l/cx88-vbi.o
  CC [M]  /home/tony/media_build/v4l/cx88-mpeg.o
  CC [M]  /home/tony/media_build/v4l/cx88-cards.o
  CC [M]  /home/tony/media_build/v4l/cx88-core.o
  CC [M]  /home/tony/media_build/v4l/cx88-i2c.o
  CC [M]  /home/tony/media_build/v4l/cx88-tvaudio.o
  CC [M]  /home/tony/media_build/v4l/cx88-dsp.o
  CC [M]  /home/tony/media_build/v4l/cx88-input.o
  CC [M]  /home/tony/media_build/v4l/cxd2820r_core.o
  CC [M]  /home/tony/media_build/v4l/cxd2820r_c.o
  CC [M]  /home/tony/media_build/v4l/cxd2820r_t.o
  CC [M]  /home/tony/media_build/v4l/cxd2820r_t2.o
  CC [M]  /home/tony/media_build/v4l/ddbridge-core.o
  CC [M]  /home/tony/media_build/v4l/drxd_firm.o
  CC [M]  /home/tony/media_build/v4l/drxd_hard.o
  CC [M]  /home/tony/media_build/v4l/drxk_hard.o
  CC [M]  /home/tony/media_build/v4l/dvbdev.o
  CC [M]  /home/tony/media_build/v4l/dmxdev.o
  CC [M]  /home/tony/media_build/v4l/dvb_demux.o
  CC [M]  /home/tony/media_build/v4l/dvb_filter.o
  CC [M]  /home/tony/media_build/v4l/dvb_ca_en50221.o
  CC [M]  /home/tony/media_build/v4l/dvb_frontend.o
  CC [M]  /home/tony/media_build/v4l/dvb_net.o
  CC [M]  /home/tony/media_build/v4l/dvb_ringbuffer.o
  CC [M]  /home/tony/media_build/v4l/dvb_math.o
  CC [M]  /home/tony/media_build/v4l/av7110_hw.o
  CC [M]  /home/tony/media_build/v4l/av7110_v4l.o
/home/tony/media_build/v4l/av7110_v4l.c:28:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/tony/media_build/v4l/av7110_av.o
  CC [M]  /home/tony/media_build/v4l/av7110_ca.o
  CC [M]  /home/tony/media_build/v4l/av7110.o
  CC [M]  /home/tony/media_build/v4l/av7110_ipack.o
  CC [M]  /home/tony/media_build/v4l/av7110_ir.o
  CC [M]  /home/tony/media_build/v4l/a800.o
  CC [M]  /home/tony/media_build/v4l/af9005-remote.o
  CC [M]  /home/tony/media_build/v4l/af9005.o
  CC [M]  /home/tony/media_build/v4l/af9005-fe.o
  CC [M]  /home/tony/media_build/v4l/af9015.o
  CC [M]  /home/tony/media_build/v4l/anysee.o
  CC [M]  /home/tony/media_build/v4l/au6610.o
  CC [M]  /home/tony/media_build/v4l/az6027.o
  CC [M]  /home/tony/media_build/v4l/ce6230.o
  CC [M]  /home/tony/media_build/v4l/cinergyT2-core.o
  CC [M]  /home/tony/media_build/v4l/cinergyT2-fe.o
  CC [M]  /home/tony/media_build/v4l/cxusb.o
  CC [M]  /home/tony/media_build/v4l/dib0700_core.o
  CC [M]  /home/tony/media_build/v4l/dib0700_devices.o
  CC [M]  /home/tony/media_build/v4l/dibusb-common.o
  CC [M]  /home/tony/media_build/v4l/dibusb-mb.o
  CC [M]  /home/tony/media_build/v4l/dibusb-mc.o
  CC [M]  /home/tony/media_build/v4l/digitv.o
  CC [M]  /home/tony/media_build/v4l/dtt200u.o
  CC [M]  /home/tony/media_build/v4l/dtt200u-fe.o
  CC [M]  /home/tony/media_build/v4l/dtv5100.o
  CC [M]  /home/tony/media_build/v4l/dw2102.o
  CC [M]  /home/tony/media_build/v4l/ec168.o
  CC [M]  /home/tony/media_build/v4l/friio.o
  CC [M]  /home/tony/media_build/v4l/friio-fe.o
  CC [M]  /home/tony/media_build/v4l/gl861.o
  CC [M]  /home/tony/media_build/v4l/gp8psk.o
  CC [M]  /home/tony/media_build/v4l/gp8psk-fe.o
  CC [M]  /home/tony/media_build/v4l/it913x.o
  CC [M]  /home/tony/media_build/v4l/lmedm04.o
  CC [M]  /home/tony/media_build/v4l/m920x.o
  CC [M]  /home/tony/media_build/v4l/mxl111sf.o
  CC [M]  /home/tony/media_build/v4l/mxl111sf-phy.o
  CC [M]  /home/tony/media_build/v4l/mxl111sf-i2c.o
  CC [M]  /home/tony/media_build/v4l/mxl111sf-gpio.o
  CC [M]  /home/tony/media_build/v4l/nova-t-usb2.o
  CC [M]  /home/tony/media_build/v4l/opera1.o
  CC [M]  /home/tony/media_build/v4l/pctv452e.o
  CC [M]  /home/tony/media_build/v4l/technisat-usb2.o
  CC [M]  /home/tony/media_build/v4l/ttusb2.o
  CC [M]  /home/tony/media_build/v4l/umt-010.o
  CC [M]  /home/tony/media_build/v4l/vp702x.o
  CC [M]  /home/tony/media_build/v4l/vp702x-fe.o
  CC [M]  /home/tony/media_build/v4l/vp7045.o
  CC [M]  /home/tony/media_build/v4l/vp7045-fe.o
  CC [M]  /home/tony/media_build/v4l/dvb-usb-firmware.o
  CC [M]  /home/tony/media_build/v4l/dvb-usb-init.o
  CC [M]  /home/tony/media_build/v4l/dvb-usb-urb.o
  CC [M]  /home/tony/media_build/v4l/dvb-usb-i2c.o
  CC [M]  /home/tony/media_build/v4l/dvb-usb-dvb.o
  CC [M]  /home/tony/media_build/v4l/dvb-usb-remote.o
  CC [M]  /home/tony/media_build/v4l/usb-urb.o
  CC [M]  /home/tony/media_build/v4l/pt1.o
  CC [M]  /home/tony/media_build/v4l/va1j5jf8007s.o
  CC [M]  /home/tony/media_build/v4l/va1j5jf8007t.o
  CC [M]  /home/tony/media_build/v4l/em28xx-audio.o
  CC [M]  /home/tony/media_build/v4l/em28xx-video.o
  CC [M]  /home/tony/media_build/v4l/em28xx-i2c.o
  CC [M]  /home/tony/media_build/v4l/em28xx-cards.o
  CC [M]  /home/tony/media_build/v4l/em28xx-core.o
  CC [M]  /home/tony/media_build/v4l/em28xx-vbi.o
  CC [M]  /home/tony/media_build/v4l/em28xx-input.o
  CC [M]  /home/tony/media_build/v4l/et61x251_core.o
/home/tony/media_build/v4l/et61x251_core.c:21:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/tony/media_build/v4l/et61x251_tas5130d1b.o
/home/tony/media_build/v4l/et61x251_tas5130d1b.c:22:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/tony/media_build/v4l/firedtv-avc.o
  CC [M]  /home/tony/media_build/v4l/firedtv-ci.o
  CC [M]  /home/tony/media_build/v4l/firedtv-dvb.o
  CC [M]  /home/tony/media_build/v4l/firedtv-fe.o
  CC [M]  /home/tony/media_build/v4l/firedtv-fw.o
  CC [M]  /home/tony/media_build/v4l/firedtv-rc.o
  CC [M]  /home/tony/media_build/v4l/fmdrv_common.o
  CC [M]  /home/tony/media_build/v4l/fmdrv_rx.o
  CC [M]  /home/tony/media_build/v4l/fmdrv_tx.o
  CC [M]  /home/tony/media_build/v4l/fmdrv_v4l2.o
  CC [M]  /home/tony/media_build/v4l/benq.o
/home/tony/media_build/v4l/benq.c:21:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/tony/media_build/v4l/conex.o
/home/tony/media_build/v4l/conex.c:22:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
/home/tony/media_build/v4l/conex.c:46:14: error: 'JPEG_HDR_SZ' undeclared here (not in a function)
/home/tony/media_build/v4l/conex.c: In function 'sd_start':
/home/tony/media_build/v4l/conex.c:850:2: error: implicit declaration of function 'jpeg_define' [-Werror=implicit-function-declaration]
/home/tony/media_build/v4l/conex.c:852:2: error: implicit declaration of function 'jpeg_set_qual' [-Werror=implicit-function-declaration]
/home/tony/media_build/v4l/conex.c: At top level:
/home/tony/media_build/v4l/jpeg.h:23:22: warning: 'jpeg_header' defined but not used [-Wunused-variable]
cc1: some warnings being treated as errors

make[3]: *** [/home/tony/media_build/v4l/conex.o] Error 1
make[2]: *** [_module_/home/tony/media_build/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.0.0-15-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/tony/media_build/v4l'
make: *** [all] Error 2
build failed at ./build line 380.
tony@wrapperband:~/media_build$

---

### Post by Cuppa-Chino on 2011-12-20
Wrapperband I am confused I thought the 290e drivers were included in kernel 3.0 is your device not started in the boot up (please excuse if you think I am pulling your leg I am not I am just trying to think of a solution)

---

### Post by Wrapperband-0 on 2011-12-23
Don't worry any suggestions welcome. I also have 2 web cameras, which are covered by the git. I haven't been able to install the v4l git  because it won't compile. It should be able to compile?? My version was compiled just before that, as I was updating regularly, when any changes were made.

The point is I was able to compile and install the v4l git, up 2 Nov 2011. I've been hoping someone will work around the issue of no HD TV sound with 290e. Basically the 290e is the only HD freeview USB pen drive.

Wrapperband

---

### Post by Wrapperband-0 on 2012-01-04
[Hi, Cuppa-Chino ]("http://ubuntuforums.org/member.php?u=49973")

Thanks for your post. 
I still need to compile the experimental LinuxTV.org git. I believe it contains the experimental v4L-2 drivers. The original post was about the problem that I can not receive HD TV with Linux. I only get the picture and no sound. I was assuming it may appear in the git eventually?

It may be possible to get VLC to view HD TV, as it uses different audio decoding method. But I have not been able to save the VLC programs channel scan. This is not automatic. I have found that non-automatic functions in Linux take extreme levels of commitment, technical knowledge and research to achieve.
  
After much asking and research; I understand the lack of audio for HD TV in the Xine functionality is due to HD freeview being (sometimes) broadcasts with Dolby. 
Dolby is proprietary so no open source committed Linux programmer has written any drivers to include HD TV audio in Linux? and there are no current plans to do so?

Correct me if I'm wrong.

Dr Anthony Doyle

---

### Post by BicyclerBoy on 2012-01-04
It is not dolby but the use of loas/latm-aac with dvb-t..

latm-aac has been supported by VLC & MythTV & HandBrake for > 3 years by use of patched versions of ffmpeg & now with full ffmpeg support.

Xine is a little behind the times considering it's user base is in the heart of dvb-t/t2.. 

If you can record the broadcast to file you can play with VLC or MythTV XBMC/HandBrake.

There was a rumour that Xine & AviDemux would get latm-aac support..

---

### Post by Wrapperband-0 on 2012-01-17
I finally got VLC working as a TV viewer. In the end it was easy to save the playlist file, and call it "channels.xspf". You can then load that next time you start VLC.

I had to scan each of my 2 USB TV sticks separately and save each file. I was able to combine the 2 saved playlist files by loading the first then the second scan and saving the modified combined playlist.

Unfortunately, I haven't been able to get my current configuration of VLC to display the HD or get any HD audio. The other problem with VLC is that, there is no EPG which makes viewing TV through VLC a bit of a pain.

I was in Ubuntu when I thought I was able to see HD TV and audio with in VLC, so perhaps my current Kubuntu set up needs a tweak. 

Wrapperband

---

### Post by Wrapperband-0 on 2012-01-25
Hi All,

I have now fixed the v4l compile problem error 380 or line 383.

 I deleted  (renamed) media_build folder - then I reinstalled the git from scratch. The ./build then worked.

Wrapperband

---

### Post by Wrapperband-0 on 2012-04-16
Brilliant news, sort of....

I have managed to get, HD TV on Linux, in a normal TV scheduler...

I have installed Me-TV 2.0, and also ran "w_scan". I found the settings to produce a a Xine style channels.conf. 

I then managed to import the file into the new "server version" of Me-TV (2.0).

Unfortunately, I tried to import a a second, slower scan, to find some missing channels, and the Me-TV database became corrupt?, and now Me-TV 2 and 1.4 won't start, I have reverted to 1.3. 

I'm still working on why it doesn't work now. I have reinstalled Me-TV in all its versions and have purged the files a number of times. Some thing is being left or is incorrectly set. ... Any help finding the me-tv files / database and deleting it/them (I assume) would be appreciated...

  sudo w_scan -ft -X -c GB > xchannels.conf -t 3

I have Kubuntu and installed w-scan with Muon.

T.

---

### Post by Wrapperband-0 on 2012-04-16
Re: corrupt me-tv channels database ...

I've found how to delete the database for Me-TV which was in /.Local/share/me-tv, (after ticking show hidden files), renamed me-tv folder to me-tv backup.

On install from Muon, Me-TV 2.0 recreated the folder and is it is now working. The database was blank, and the channels.conf file has imported correctly. The channels now show in me-tv

T.

---

### Post by Wrapperband-0 on 2012-04-17
Although you can now hear and view HD TV from 290e USB stick by using Me-TV 2.0.1, in Linux, I have found it to be very flaky.

It has crashed a number of times, seeming to do with the server / channel database corruption. The same faults exhibit themselves in version Me-TV 1.4, on my system. 

It also exhibits the Xine colour mismatch bug, (in my Kubuntu / nVidea system) where the Hue is incorrectly set, or changed when viewed by different graphics programs.

Unfortunately for Me-TV 2.0.1, unlike say,  Dragon video player; there is no video adjust available in Me-TV to correct the bug and everything looks purple.

I'll update if any further news, and please help if you have ideas for fixing "incorrect Hue colour Bug in X video".

T.

** UPDATE **

The (gnome application) hue bug appears to have been due to a small change in the Hue setting of the nVidia card settings, being amplified in Xine / X clients (?) ie Me-TV, Totem, mPlayer, Dragon media players. I adjusted that setting back to zero and it all now appears OK.  I didn't change that myself so some application or update must have adjusted it??.

I have created a channels.conf file, and have manually adjusted the channel order, using a text editor. When Me-TV version 2.0.1 crashes, I can do as follows to correct the fault :

1. delete the Me-TV local channels database in ~/.local/share/me-tv   (show hidden files)
2. Stop the me-tv server process, with system monitor
3. restart me-tv 2.0.1. use the re-ordered xchannels.conf file to refill the channels database.

Hopefully someone will correct the flaky code, now that Me-tv 2.0.1 is standard release? It seems to lack good error handling of the channels database...

I have tried Kaffiene 1.2.2 again and the hue problem is also corrected in that application. The HD channels still have no sound in Kaffiene.

---

### Post by Wrapperband-0 on 2012-05-16
Getting High Definition Freeview TV in Linux

DVB-T2  - HD - TV from Freeview with Linux / Ubuntu / Kubuntu

Because Me-TV ( 1.3) broke when I updated to Precise (12.04) so I tried Kaffeine again. It was still suffering from the Video and Audio out of sync bug.

After much searching and a bit of adjusting of the Kaffeine config file, I found that changing the audio device driver to ALSA from Pulse seems to have fixed that Sync problem.

The EPG in Kaffeine is pretty bad, not like ME-TV where you can see whats on each channel without clicking on it. So I have downloaded TV-Browser, a Java App that gives the TV in a Radio Times like format...

It's worth noteing VLC also can decode Freeview HD with audio, and the reason I didn't use that before was the poor EPG. i.e that would also be a good solution with TV-Browser as the EPG.

TV-Browser in the KDE menu system of my Kubuntu, under Multimedia.

Wrapperband



ADDITION:   Kaffeine still goes out of audio visual Sync after an hour of watching, even with the ALSA driver - Very Poor
I have now switched to VLC, with its extremely bad EPG...  Until I can go back to a Me-TV thats compatible with 12.04, with or without HD...

---

### Post by Wrapperband-0 on 2012-07-12
Some further information and tips..

Me-TV has been updated and the current version now works with Linux 12.04 (precise)
Me-TV is now was showing HD TV with good audio and a good epg.

Kernel 3.2 has HD TV driver compiled in for the [***Hauppauge***]("http://www.google.com/search?hl=en&client=ubuntu&hs=qnI&channel=fs&gl=uk&sa=X&ei=G7X-T_ibEsW00QWdofyoBQ&ved=0CFIQvwUoAQ&q=Hauppauge&spell=1&biw=1534&bih=849") 290e DVB-T2 USB stick.

The improvement (xine based software?) in correctly handling HD audio was due to a ffmpeg upgrade in Nov 2011. VLC has been able to do it for a while before that.

If you are updating an old Kernel to view TV or webcams - you need to install v4l drivers, use the media_build git at :

[http://git.linuxtv.org/media_build.git](http://git.linuxtv.org/media_build.git)

The changes are uploaded once a day (manually) so I found once that,  a fix had not been uploaded. Then you can update from the absolute latest version ...
./build --main-git switch 

- takes a bit more time to download the full source.I am now using TV-Browser to as a very good TV guide, as Kaffeine is a bit deficient in EPG.  I have also tried FreeGuide, which is in the repositories and found that good as well, so far ..

---

