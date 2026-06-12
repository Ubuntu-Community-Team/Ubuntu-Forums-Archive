---
title: "[SOLVED] Sound Card Has disappeared"
date: 2007-10-03
forum: Multimedia &amp; Video
---

### Post by squirage on 2007-10-03
Hi,

I have been trying to figure this out for days. Absolutely nothing I have tried has worked thus far. I started keeping a document to trace what I had done, it is now 38 pages long.

I started asking about this here: [http://ubuntuforums.org/showthread.php?t=564031](http://ubuntuforums.org/showthread.php?t=564031)

I have not received one reply, unless you count the one to myself.

Here is what I did since then:

10/03/07 06:24:12 AM

Tried one more thing, retried this:
```

sudo dpkg-reconfigure alsa-source
```
ran through the options and deselected intel8x0, then selected intel8x0m.

I then ran:
```

 sudo module-assistant a-i alsa-source

Updated infos about 1 packages
Getting source for kernel version: 2.6.17-12-generic
Kernel headers available in /lib/modules/2.6.17-12-generic/build
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  libpopt-dev libsm-dev libattr1-dev libice-dev libaspell-dev
  x11proto-xext-dev libtasn1-3-dev libaudiofile-dev libaudio-dev
  x11proto-kb-dev libglib2.0-dev libgpg-error-dev x11proto-xinerama-dev
  comerr-dev libpcre3-dev libopencdk8-dev x11proto-render-dev libgcrypt11-dev
  liblualib50-dev libxi-dev libxmu-headers libxrender-dev mesa-common-dev
  libxdmcp-dev libkrb5-dev qt3-dev-tools libsasl2-dev libavahi-client-dev
  libogg-dev libjasper-1.701-dev libpng12-dev libfontconfig1-dev libpcrecpp0
  xtrans-dev liblua50-dev x11proto-core-dev libxcursor-dev lua50
  libavahi-qt3-dev libacl1-dev libglu1-mesa-dev libgnutls-dev libqt3-mt-dev
  x11proto-randr-dev hspell libdbus-1-dev libxslt1-dev libssl-dev libxt-dev
  libxmu-dev libxext-dev libjpeg62-dev zlib1g-dev libxml2-dev
  x11proto-input-dev libtiff4-dev libfreetype6-dev libart-2.0-dev libesd0-dev
  x11proto-fixes-dev libxau-dev liblzo-dev libqt3-headers libasound2-dev
  libtiffxx0c2 libgl1-mesa-dev liblcms1-dev libxrandr-dev libkadm55
  libexpat1-dev libxft-dev libx11-dev libartsc0-dev libopenexr-dev
  libxfixes-dev libmng-dev libavahi-common-dev libxinerama-dev kdesdk-scripts
  libcupsys2-dev libvorbis-dev gettext-kde libidn11-dev libbz2-dev
  libarts1-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Done!
unpack 
Extracting the package tarball, /usr/src/alsa-driver.tar.bz2, please wait...
Target package file 
/usr/src/alsa-modules-2.6.17-12-generic_1.0.11-5ubuntu1+2.6.17.1-12.41_i386.deb
already exists, not rebuilding!
(however, you could use the -f switch to ignore it)
dpkg -Ei /usr/src/alsa-modules-2.6.17-12-generic_1.0.11-5ubuntu1+2.6.17.1-12.41_i386.deb 
Version 1.0.11-5ubuntu1+2.6.17.1-12.41 of alsa-modules-2.6.17-12-generic already installed, skipping.

```
I'm not sure why it did not run through the utility again so I did the next thing.
```

sean@sean-laptop:~$ sudo modprobe snd-intel8x0m
FATAL: Module snd_intel8x0m not found.
```

I am officially at a total loss.

07:28:41 AM Back at it with the advice from [http://ubuntuforums.org/showthread.php?t=515578&highlight=sound+on+ubuntu](http://ubuntuforums.org/showthread.php?t=515578&highlight=sound+on+ubuntu)
```

sudo apt-get install build-essential

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2

```
okay
```

tar xjf alsa-driver-1.0.14.tar.bz2
```

gave me another prompt
```

cd alsa*
```

switched to /alsa-driver-1.0.14
```

./configure

checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/sean/alsa-driver-1.0.14
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.17-12-generic/build
checking for directory with kernel build... 
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.17-12-generic
checking for GCC version... Kernel compiler: gcc 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5) Used compiler: gcc (GCC) 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)
checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for CONFIG_EXPERIMENTAL... yes
checking for kernel linux/config.h... yes
checking to modify of kernel linux/kmod.h... no
checking for kernel linux/utsrelease.h... no
Creating a dummy <linux/utsrelease.h>...
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel media/v4l2-dev.h... no
Creating a dummy <media/v4l2-dev.h>...
checking for kernel linux/devfs_fs_kernel.h... yes
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... yes
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
checking for kernel linux/isa.h... no
Creating <linux/isa.h>...
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/log2.h... no
Creating a dummy <linux/log2.h>...
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for kernel linux/latency.h... no
Creating <linux/latency.h>...
checking for kernel asm/irq_regs.h... no
Creating a dummy <asm/irq_regs.h>...
checking for kernel module symbol versions... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... module
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.17-12-generic/kernel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... yes
checking for processor type... i586
checking for i386 machine type... default
checking for ISA DMA API... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... yes
checking for strlcpy... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for scnprintf... yes
checking for sscanf... yes
checking for vmalloc_to_page... yes
checking for old kmod... no
checking for PDE... yes
checking for pci_set_consistent_dma_mask... yes
checking for pci_dev_present... yes
checking for msleep... yes
checking for msleep_interrupt... yes
checking for msecs_to_jiffies... yes
checking for tty->count is the atomic type... no
checking for video_get_drvdata... yes
checking for io_remap_pfn_range... yes
checking for kcalloc... yes
checking for kstrdup... yes
checking for kzalloc... yes
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... yes
checking for new pci_save_state... yes
checking for register_sound_special_device... yes
checking for driver version... 1.0.14
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC callback support in kernel... yes
checking for HPET support... yes
checking for dynamic minor numbers... no
checking for support of old API... yes
checking for Procfs support... yes
checking for USB support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... yes
checking for nested class_device... yes
checking for new IRQ handler... no
checking for gfp_t... yes
checking for PnP suspend/resume... yes
checking for new unlocked/compat_ioctl... yes
checking for PC-Speaker hook... no
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for which soundcards to compile driver for... all
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: WARNING:  Makefile.conf.in seems to ignore the --datarootdir setting
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/pci_ids_compat.h
config.status: creating include/i2c-id_compat.h
config.status: creating include/config.h
config.status: creating include/config1.h
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...
```
```

make
```

A lot of stuff came down, I can't seem to get all the way back to the top but the last line sums it up:
```

ALSA modules were successfully compiled.

sudo make install
```

Does its thing, and reminds me that the mixer is muted by default.

08:27:05 AM Rebooted, still have the circle slash symbol over volume, alsamixer gives:
```

samixer: function snd_ctl_open failed for default: No such device

lsmod | grep snd
snd_timer              27529  1 
snd                    66924  1 snd_timer
soundcore              11232  1 snd
snd_page_alloc         12040  0 
```

Which seems to substantiate that something is pretty wrong.
```

aplay -l
aplay: device_list:222: no soundcards found...

cat /proc/asound/card0/codec#0
cat: /proc/asound/card0/codec#0: No such file or directory

```
[http://ubuntuforums.org/showthread.php?t=539215](http://ubuntuforums.org/showthread.php?t=539215)

tried this:

"EDIT: Nevermind, I got it working. The trick was to create a file called asound.conf in /etc with the text:"
```

pcm.!default {
    type hw
    card ICH
}
ctl.!default {
    type hw
    card ICH
}
```

I had done something like this before with ./asoundrc, that did not work.

Another similar post mentioned something about removing power/ battery and then rebooting. It's worth a shot.

Thanks.

---

### Post by squirage on 2007-10-05
I finally fixed this problem.

I posted how here [http://ubuntuforums.org/showthread.php?p=3482677](http://ubuntuforums.org/showthread.php?p=3482677)

---

