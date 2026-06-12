---
title: "New install, no sound using realtek AC97"
date: 2008-01-28
forum: Multimedia &amp; Video
---

### Post by shoeshrimp on 2008-01-28
Hey Guys,

I have recently installed ubuntu (dual boot with windows xp) on my laptop and everything is running swimmingly, and I am very pleased with it. Apart from the sound. My problems are as follows:

1) I get a log in sound but nothing else. When I try to play any music files with any program the program crashes.

2) I have followed the comprehensive sound thread but to no avail - installing fresh drivers did nothing.

3) My soundcard is an ATI realtek AC97.

My readouts are as follows:
```
tom@tom-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
tom@tom-laptop:~$ 
tom@tom-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS300 Host Bridge (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
00:14.0 SMBus: ATI Technologies Inc SMBus (rev 17)
00:14.1 IDE interface: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
tom@tom-laptop:~$ 

```


Any help would be greatly appreciated.

---

### Post by codesplice on 2008-01-28
Have you tried installing the linux-backports-modules package?

Contains a newer version of the ALSA stuff.  might be worth a shot.

---

### Post by shoeshrimp on 2008-01-28
> **codesplice said:**
> Have you tried installing the linux-backports-modules package?

Contains a newer version of the ALSA stuff.  might be worth a shot.
sorry to be a newb.. how do i do that?

Thanks!

---

### Post by codesplice on 2008-01-28
From the terminal,  

```
$ sudo aptitude install linux-backports-modules
```

---

### Post by lhardyl on 2008-01-28
wewt!

i had the same problem shoeshrimp but this has solved my sound issues. I can actually play an audio cd now!!!

thanks codesplice

---

### Post by codesplice on 2008-01-28
> **lhardyl said:**
> wewt!

i had the same problem shoeshrimp but this has solved my sound issues. I can actually play an audio cd now!!!

thanks codesplice

you're welcome, glad I could help :)

---

### Post by humanform on 2008-01-28
I tried the same command but got this:

Couldn't find package "linux-backports-modules".  However, the following
packages contain "linux-backports-modules" in their name:
  linux-backports-modules-server-bigiron 
  linux-backports-modules-2.6.20-15-server 
  linux-backports-modules-2.6.20-15-generic 
  linux-backports-modules-lowlatency 
  linux-backports-modules-2.6.20-15-server-bigiron 
  linux-backports-modules-generic linux-backports-modules-2.6.20-15-386 
  linux-backports-modules-386 linux-backports-modules-2.6.20-15-lowlatency 
  linux-backports-modules-server 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

Any ideas?

---

### Post by codesplice on 2008-01-28
> **humanform said:**
> 
  linux-backports-modules-2.6.20-15-generic 

Any ideas?

Try that one :)

---

### Post by humanform on 2008-01-28
I was able to install that one but still no sound after rebooting.
The sound was working after the original install but quit working after i did the updates.
If I right click on the sound icon and try to open the volume control, I get an error "No volume control GStreamer plugins and or/devises found."

I'm using a Gateway laptop.

aplay -l shows no cards found
lspci -v shows the ATI SB450

Any help would be appreciated.

---

### Post by xc3RnbFO8P on 2008-01-30
Try this:

 sudo aptitude install module-assistant build-essential

sudo module-assistant prepare,update

sudo module-assistant build,install alsa

sudo depmod

reboot

---

### Post by shoeshrimp on 2008-01-31
I have tried the above (with the exception of Ringi's suggestion - I'll try that when I get home), and have had no success. I can access the volume controls, but still when I try to play an mp3 track, amarok crashes, last.fm radio crashes, and audio cd's crash. Is this crashing definitely related to alsa?

Thanks

---

### Post by shoeshrimp on 2008-01-31
Still no joy - I tried Ringi's suggestion. Does anyone know why I get the log in sound (though it seems to cut off short) and nothing else?

---

### Post by xc3RnbFO8P on 2008-01-31
If you search in Synaptic Package Manager "linux-backports", what do you get?

---

### Post by shoeshrimp on 2008-01-31
> **Ringi said:**
> If you search in Synaptic Package Manager "linux-backports", what do you get?



I get:

```
linux-backports-modules: [version 2.6.22.14.21]
linux-backports-modules-2.6.22-14-386 [version 2.6.22-14.10]
linux-backports-modules-2.6.22-14-generic 
linux-backports-modules-2.6.2-14-rt version 
linux-backports-modules-2.6.22-14-server
linux-backports-modules-2.6.22-14-ume
linux-backports-modules-2.6.22-14-xen
linux-backports-modules-386
linux-backports-modules-generic [version 2.6.22.14.21]
linux-backports-module-rt
linux-backports-module-server
linux-backports-module-ume
linux-backports-module-virtual
linux-backports-module-xen

```

Thank you for your help!

---

### Post by xc3RnbFO8P on 2008-02-01
Do you have /usr/src/alsa/alsa-driver-1.0.15
and /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko

---

### Post by shoeshrimp on 2008-02-02
> **Ringi said:**
> Do you have /usr/src/alsa/alsa-driver-1.0.15
and /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko

I don't have /usr/src/alsa/alsa-driver-1.0.15, I have, /usr/src/alsa/alsa-driver-1.0.16rc1

but I do have the 2nd file.

Thank you very much for your help!

---

### Post by xc3RnbFO8P on 2008-02-02
> **shoeshrimp said:**
> I don't have /usr/src/alsa/alsa-driver-1.0.15, I have, /usr/src/alsa/alsa-driver-1.0.16rc1

but I do have the 2nd file.

Thank you very much for your help!

In /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/       delete **snd-hda-intel.ko**

Then you have to recompile 1.0.16rc1

in terminal cd /usr/src/alsa/alsa-driver-1.0.16rc1

./configure

sudo make

sudo make install

---

### Post by shoeshrimp on 2008-02-02
I seem to have got a couple of errors while doing this...

```
tom@tom-laptop:/usr/src/alsa/alsa-driver-1.0.16rc1$ sudo ./configure
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
checking for current directory... /usr/src/alsa/alsa-driver-1.0.16rc1
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.22-14-generic/build
checking for directory with kernel build... 
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.22-14-generic
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for CONFIG_EXPERIMENTAL... yes
checking for kernel linux/config.h... no
Creating <linux/config.h>...
checking to modify of kernel linux/kmod.h... no
checking for kernel linux/utsrelease.h... yes
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel media/v4l2-dev.h... yes
checking for kernel linux/devfs_fs_kernel.h... no
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... yes
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
checking for kernel linux/isa.h... yes
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/log2.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for kernel linux/latency.h... yes
checking for kernel linux/kthread.h... yes
checking for kernel asm/irq_regs.h... yes
checking for kernel linux/seq_file.h... yes
checking for kernel module symbol versions... yes
checking for has ioport support... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... module
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.22-14-generic/kernel/sound
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
checking for V4L1 layer... yes
checking for io_remap_pfn_range... yes
checking for kcalloc... yes
checking for kstrdup... yes
checking for kzalloc... yes
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... yes
checking for new pci_save_state... yes
checking for register_sound_special_device... yes
checking for driver version... 1.0.16rc1
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
checking for new IRQ handler... yes
checking for gfp_t... yes
checking for init_utsname... no
checking for PnP suspend/resume... yes
checking for new unlocked/compat_ioctl... yes
checking for x86-compatible PC... yes
checking for High-Res timers... yes
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
config.status: include/config.h is unchanged
config.status: creating include/config1.h
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...
tom@tom-laptop:/usr/src/alsa/alsa-driver-1.0.16rc1$ sudo make
make dep
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/acore'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/acore/ioctl32'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/acore/ioctl32'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/acore/oss'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/acore/oss'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/acore/seq'
make[4]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/acore/seq/oss'
make[4]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/acore/seq/oss'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/acore/seq'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/acore'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/i2c'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/i2c/l3'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/i2c/l3'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/i2c/other'
copying file alsa-kernel/i2c/other/tea575x-tuner.c
patching file tea575x-tuner.c
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/i2c/other'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/i2c'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/drivers'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/drivers/mpu401'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/drivers/mpu401'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/drivers/opl3'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/drivers/opl3'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/drivers/opl4'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/drivers/opl4'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/drivers/pcsp'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/drivers/pcsp'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/drivers/vx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/drivers/vx'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/drivers'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/isa'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/isa/ad1816a'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/isa/ad1816a'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/isa/ad1848'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/isa/ad1848'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/isa/cs423x'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/isa/cs423x'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/isa/es1688'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/isa/es1688'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/isa/gus'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/isa/gus'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/isa/msnd'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/isa/msnd'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/isa/opti9xx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/isa/opti9xx'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/isa/sb'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/isa/sb'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/isa/wavefront'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/isa/wavefront'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/isa'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/synth'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/synth/emux'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/synth/emux'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/synth'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/ac97'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/ac97'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/ali5451'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/ali5451'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/asihpi'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/asihpi'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/au88x0'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/au88x0'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/ca0106'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/ca0106'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/cs46xx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/cs46xx'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/cs5535audio'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/cs5535audio'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/echoaudio'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/echoaudio'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/emu10k1'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/emu10k1'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/hda'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/hda'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/ice1712'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/ice1712'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/korg1212'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/korg1212'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/mixart'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/mixart'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/nm256'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/nm256'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/oxygen'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/oxygen'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/pcxhr'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/pcxhr'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/pdplus'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/pdplus'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/riptide'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/riptide'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/rme9652'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/rme9652'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/trident'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/trident'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/vx222'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/vx222'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/ymfpci'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci/ymfpci'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pci'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/aoa'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/aoa/codecs'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/aoa/codecs'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/aoa/core'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/aoa/core'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/aoa/fabrics'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/aoa/fabrics'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/aoa/soundbus'
make[4]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/aoa/soundbus/i2sbus'
make[4]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/aoa/soundbus'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/aoa'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/soc'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/soc/at91'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/soc/at91'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/soc/codecs'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/soc/codecs'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/soc/fsl'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/soc/fsl'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/soc/pxa'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/soc/pxa'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/soc/s3c24xx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/soc/s3c24xx'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/soc/sh'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/soc/sh'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/soc'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/usb'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/usb/caiaq'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/usb/caiaq'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/usb/usx2y'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/usb/usx2y'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/usb'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pcmcia'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pcmcia/pdaudiocf'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pcmcia/pdaudiocf'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pcmcia/vx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pcmcia/vx'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/pcmcia'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/misc'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/misc'
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1'
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/usr/src/alsa/alsa-driver-1.0.16rc1  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /usr/src/alsa/alsa-driver-1.0.16rc1/acore/hwdep.o
  CC [M]  /usr/src/alsa/alsa-driver-1.0.16rc1/acore/memory_wrapper.o
  CC [M]  /usr/src/alsa/alsa-driver-1.0.16rc1/acore/memalloc.o
  CC [M]  /usr/src/alsa/alsa-driver-1.0.16rc1/acore/sgbuf.o
  CC [M]  /usr/src/alsa/alsa-driver-1.0.16rc1/acore/pcm.o
  CC [M]  /usr/src/alsa/alsa-driver-1.0.16rc1/acore/pcm_native.o
  CC [M]  /usr/src/alsa/alsa-driver-1.0.16rc1/acore/pcm_lib.o
  CC [M]  /usr/src/alsa/alsa-driver-1.0.16rc1/acore/pcm_timer.o
  CC [M]  /usr/src/alsa/alsa-driver-1.0.16rc1/acore/pcm_misc.o
  CC [M]  /usr/src/alsa/alsa-driver-1.0.16rc1/acore/pcm_memory.o
  CC [M]  /usr/src/alsa/alsa-driver-1.0.16rc1/acore/rawmidi.o
  CC [M]  /usr/src/alsa/alsa-driver-1.0.16rc1/acore/rtctimer.o
  CC [M]  /usr/src/alsa/alsa-driver-1.0.16rc1/acore/timer.o
  CC [M]  /usr/src/alsa/alsa-driver-1.0.16rc1/acore/wrappers.o
  CC [M]  /usr/src/alsa/alsa-driver-1.0.16rc1/acore/misc_driver.o
  CC [M]  /usr/src/alsa/alsa-driver-1.0.16rc1/acore/sound.o
  CC [M]  /usr/src/alsa/alsa-driver-1.0.16rc1/acore/init.o
  CC [M]  /usr/src/alsa/alsa-driver-1.0.16rc1/acore/memory.o
  CC [M]  /usr/src/alsa/alsa-driver-1.0.16rc1/acore/info.o
  CC [M]  /usr/src/alsa/alsa-driver-1.0.16rc1/acore/control.o
  CC [M]  /usr/src/alsa/alsa-driver-1.0.16rc1/acore/misc.o
  CC [M]  /usr/src/alsa/alsa-driver-1.0.16rc1/acore/device.o
  CC [M]  /usr/src/alsa/alsa-driver-1.0.16rc1/acore/isadma.o
  CC [M]  /usr/src/alsa/alsa-driver-1.0.16rc1/acore/sound_oss.o
  CC [M]  /usr/src/alsa/alsa-driver-1.0.16rc1/acore/info_oss.o
In file included from /usr/src/alsa/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c:29,
                 from /usr/src/alsa/alsa-driver-1.0.16rc1/acore/info_oss.c:7:
include/linux/utsname.h:76:52: error: macro "init_utsname" passed 1 arguments, but takes just 0
In file included from /usr/src/alsa/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c:29,
                 from /usr/src/alsa/alsa-driver-1.0.16rc1/acore/info_oss.c:7:
include/linux/utsname.h:77: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
In file included from /usr/src/alsa/alsa-driver-1.0.16rc1/acore/info_oss.c:7:
/usr/src/alsa/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c: In function ‘snd_sndstat_proc_read’:
/usr/src/alsa/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c:96: error: ‘system_utsname’ undeclared (first use in this function)
/usr/src/alsa/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c:96: error: (Each undeclared identifier is reported only once
/usr/src/alsa/alsa-driver-1.0.16rc1/acore/../alsa-kernel/core/info_oss.c:96: error: for each function it appears in.)
make[3]: *** [/usr/src/alsa/alsa-driver-1.0.16rc1/acore/info_oss.o] Error 1
make[2]: *** [/usr/src/alsa/alsa-driver-1.0.16rc1/acore] Error 2
make[1]: *** [_module_/usr/src/alsa/alsa-driver-1.0.16rc1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [compile] Error 2
tom@tom-laptop:/usr/src/alsa/alsa-driver-1.0.16rc1$ sudo make install
if [ -L /usr/include/sound ]; then \
                rm -f /usr/include/sound; \
                ln -sf /usr/src/alsa/alsa-driver-1.0.16rc1/include/sound /usr/include/sound; \
        else \
                rm -rf /usr/include/sound; \
                install -d -m 755 -g root -o root /usr/include/sound; \
                for f in include/sound/*.h; do \
                        install -m 644 -g root -o root $f /usr/include/sound; \
                done \
        fi
find /lib/modules/2.6.22-14-generic/kernel/sound -name 'snd*.*o' | xargs rm -f
find /lib/modules/2.6.22-14-generic/kernel/sound -name 'snd*.*o.gz' | xargs rm -f
find /lib/modules/2.6.22-14-generic/kernel/sound -name 'ac97_bus.*o' | xargs rm -f
find /lib/modules/2.6.22-14-generic/kernel/sound -name 'ac97_bus.*o.gz' | xargs rm -f
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.16rc1/acore'
mkdir -p /lib/modules/2.6.22-14-generic/kernel/sound/acore
cp snd-hwdep.ko snd-page-alloc.ko snd-pcm.ko snd-rawmidi.ko snd-rtctimer.ko snd-timer.ko snd.ko /lib/modules/2.6.22-14-generic/kernel/sound/acore
cp: cannot stat `snd-hwdep.ko': No such file or directory
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-rawmidi.ko': No such file or directory
cp: cannot stat `snd-rtctimer.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.16rc1/acore'
make: *** [install-modules] Error 1
tom@tom-laptop:/usr/src/alsa/alsa-driver-1.0.16rc1$ 
```

is that to be expected? I'm still having no sound and program crashes. When I try to play last.fm radio it says... "The ALSA soundsystem is either busy or not present."

Thanks.

---

### Post by xc3RnbFO8P on 2008-02-02
In Synaptic Package Manager install this:> f2c

dpkg-dev

fort77

g++,multilib, 2.95, 3.3, 3.4, 4.1, multilib,4.2, multilib 

g77, g77-3.4

gcc, 2.95, 3.3, 3.4, 4.1, 4.2, multilib

gcj, 4.2

gfortran, 4.2

gobjc, 4.1, multillib, 4.2, multilib

lib64gomp1?

libc6-dev

libgomp1

libgsl0

libmikmod2-dev

libncurses5

libncursesw5

libqt3-headers

libstdc++5, 6,

make 3.81

pkg-config

automake, 1.4, 1.7, 1.8, 1.9

Gettext

To speed it up, search: **Compiler** and then **automake**.

Then do it all over again: ./configure, etc.

What kind of laptop do you have?

---

### Post by shoeshrimp on 2008-02-05
No joy again I'm afraid. Amarok still crashes and Last.fm still says the same thing. I have a toshiba A30 satellite laptop. Maybe I'll have to try a different release of linux - would be a shame though, I think I'd rather use ubuntu especially as I'm getting used to it. The silence is stifling though!

Ta

Tom

---

### Post by xc3RnbFO8P on 2008-02-05
Check if got **snd-hda-intel.ko** in **/lib/modules/2.6.22-14-generic/pci/hda**  and  **/usr/src/alsa-driver-1.0.16rc1/modules**


Then try this:

sudo gedit /etc/modprobe.d/options

add this lines

# for soundchip snd_atiixp
options snd-atiixp ac97_codec=0

save and reboot

---

### Post by shoeshrimp on 2008-02-05
> **Ringi said:**
> Check if got **snd-hda-intel.ko** in **/lib/modules/2.6.22-14-generic/pci/hda**  and  **/usr/src/alsa-driver-1.0.16rc1/modules**


Then try this:

sudo gedit /etc/modprobe.d/options

add this lines

# for soundchip snd_atiixp
options snd-atiixp ac97_codec=0

save and reboot

heya, I don't have that file in either folder. I don't actually have the 2nd folder, it's **/usr/src/alsa/alsa-driver-1.0.16rc1/modules**.

I ran the code, but it didn't work.

---

### Post by shoeshrimp on 2008-02-07
Getting there!

Yesterday I booted up, and it played the WHOLE of the login sound (I hadn't realised that it had been cutting off half-way through), and Amarok played 20 seconds of a song before being plunged into darkness. This is definitely an improvement. However, any boot ups after this 1 occassion have resulted in the usual cut off login sound and no response from amarok. It seems to be very temperamental!?

---

### Post by jou770d on 2008-02-07
I've installed gutsy on my A30 and I'm having the same problem. I'm asking and searching around for a solution, I'll share it with you as soon as I find on. (But being a complete linux newb that'll probably take some time).
But I wanted to ask you if you're having some other problems:
Do you get the boot screen when you turn on your device or just a black screen till the log in screen?
Does the device return from hibernation normally?

Thanks in advance!


Edit:
Just remembered something that might be of use for the people trying to help with this problem, I didn't
The sound seems to be working normally when I boot from the cd.

Edit 2:
Sound is working normally for me!!
While trying to fix the sound I've messed up tons of stuff so I've decided to give it a clean start. I've reinstalled gutsy and when I first logged in I decided not to enable the modem when I got the pop-up (I have hardware issues with my modem so it doesn't really matter to me). And now the sound is working (even after rebooting a couple of times). Can you confirm that this is the problem shoeshrimp??
However I'm still not completely satisfied with the way gutsy is working on my laptop, I can't properly use hibernate, suspend and sometimes even restart. And the booting screen still doesn't show.
My next step is to fix that and to figure out how to use a usb 3G modem on linux... :(

---

### Post by shoeshrimp on 2008-02-07
> **Amarus said:**
> I've installed gutsy on my A30 and I'm having the same problem. I'm asking and searching around for a solution, I'll share it with you as soon as I find on. (But being a complete linux newb that'll probably take some time).
But I wanted to ask you if you're having some other problems:
Do you get the boot screen when you turn on your device or just a black screen till the log in screen?
Does the device return from hibernation normally?

Thanks in advance!


Edit:
Just remembered something that might be of use for the people trying to help with this problem, I didn't
The sound seems to be working normally when I boot from the cd.

Edit 2:
Sound is working normally for me!!
While trying to fix the sound I've messed up tons of stuff so I've decided to give it a clean start. I've reinstalled gutsy and when I first logged in I decided not to enable the modem when I got the pop-up (I have hardware issues with my modem so it doesn't really matter to me). And now the sound is working (even after rebooting a couple of times). Can you confirm that this is the problem shoeshrimp??
However I'm still not completely satisfied with the way gutsy is working on my laptop, I can't properly use hibernate, suspend and sometimes even restart. And the booting screen still doesn't show.
My next step is to fix that and to figure out how to use a usb 3G modem on linux... :(

Thanks for your message. I do not see any boot screen when I log in no, so it seems we were having similar problems. Restart will work as long as no programs have crashed during the time I've been logged in. As Amarok usually crashes due to my sound problems, it doesn't work very often. Can't say I really use hibernate though. I wonder if there is a way of me uninstalling the modem (which I don't use) without having to go through the full reinstall? I did hear there was a compatibility issue, but I thought I'd stopped it by uncommenting its entry somewhere. I'll post another message to find out. Thanks for your help.

---

### Post by xc3RnbFO8P on 2008-02-07
I found this on a Fedora forum:

> In terminal:  amixer
.... find a line that this!!!
Simple mixer control 'External Amplifier',0 <<-- 'External amplifier is the problem!!! '
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [off] <.-- here is the problem
Run this two lines !!!:::amixer set 'External Amplifier' unmute
amixer set 'External Amplifier' 100%

I google "set 'External Amplifier' and found this site: [http://de.pastebin.ca/809584]("http://de.pastebin.ca/809584")

And it sould be:
> 
amixer set 'External Amplifier',0 100%,100% on

Here some links with other solution:

> [http://www.linuxquestions.org/questions/linux-laptop-and-handheld-25/no-sound-on-toshiba-satellite-u305-594534/?highlight=atiixp](http://www.linuxquestions.org/questions/linux-laptop-and-handheld-25/no-sound-on-toshiba-satellite-u305-594534/?highlight=atiixp)

> [http://ubuntuforums.org/showthread.php?t=504096](http://ubuntuforums.org/showthread.php?t=504096)

> [http://ubuntuforums.org/showthread.php?t=365342&page=2](http://ubuntuforums.org/showthread.php?t=365342&page=2)

> [http://student.icis.pcz.pl/~89573/laptop/](http://student.icis.pcz.pl/~89573/laptop/)

In /etc/modprobe.d/blacklist 

> blacklist snd-atiixp-modem

---

### Post by jaem on 2008-02-11
> **Ringi said:**
> Try this:

 sudo aptitude install module-assistant build-essential

sudo module-assistant prepare,update

sudo module-assistant build,install alsa

sudo depmod

reboot
This code doesn't work for me either -  I think there's a typo.  Rather than figure that out, I checked, and if you just type in

sudo module-assistant

and follow the directions (e.g. prepare, then update, then get => select "alsa", build, install), it should be pretty straightforward.

I'm still building, so I don't know if this will solve the initial problem of getting the audio to work, but it will at least work for building the module.
I'll post back if/when I get it working - that might be tomorrow, because it's pretty late here.

---

### Post by jaem on 2008-02-11
I can confirm that this does in fact work.

However, I realized after writing the last post, that I have different audio card than you - mine is listed by lspci as "Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)"

Be that as it may, it worked for me, so it may well work for you.  I'll leave any further commentary on this matter to those who know more than I about such matters.

---

### Post by shoeshrimp on 2008-02-11
> **jaem said:**
> I can confirm that this does in fact work.

However, I realized after writing the last post, that I have different audio card than you - mine is listed by lspci as "Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)"

Be that as it may, it worked for me, so it may well work for you.  I'll leave any further commentary on this matter to those who know more than I about such matters.

Hey, thanks. I have done all of this but then it tells me to reload alsa drivers. Do you know how to do this??

---

### Post by xc3RnbFO8P on 2008-02-11
> **shoeshrimp said:**
> Hey, thanks. I have done all of this but then it tells me to reload alsa drivers. Do you know how to do this??

Try this:

> sudo /etc/init.d/alsasound reload

> sudo /etc/init.d/alsasound start

---

### Post by shoeshrimp on 2008-02-12
Could not find the command alsasound. It's not in that folder...

---

### Post by shoeshrimp on 2008-03-03
I haven't had any luck with any of these, and think I should give it up as a lost cause, which is a shame. Is it worth me trying any other releases of ubuntu? Or will the bug still exist?

Thanks for all your help everyone,

Tom

---

### Post by shoeshrimp on 2008-03-09
Does anyone know if xubuntu has the same bug whereby I won't be able to hear any sound? I'd love to use linux as opposed to windows, but I can't until I get some sound!

Thanks

---

### Post by shoeshrimp on 2008-04-18
> **shoeshrimp said:**
> Does anyone know if xubuntu has the same bug whereby I won't be able to hear any sound? I'd love to use linux as opposed to windows, but I can't until I get some sound!

Thanks

does anyone know if i can use a different release of linux to solve my sound problems?
Ta!

---

