---
title: "generic ALSA driver for USB soundcard: permission denied"
date: 2010-01-03
forum: Multimedia Software
---

### Post by sojournerC on 2010-01-03
I have been attempting to configure my Edirol 1 usb soundcard to work with alsa and ultimately with jack through alsa. I have downloaded alsa drivers from this site [http://www.alsa-project.org/main/index.php/Download]("http://http://www.alsa-project.org/main/index.php/Download") and followed his instructions for installation here [http://alsa-project.org/main/index.php/Matrix:Module-usb-audio. ]("http://alsa-project.org/main/index.php/Matrix:Module-usb-audio")

Here is where I get stuck. I move the files to /usr/src/alsa, unzip them and go to configure but arrive at the following. It seems to be a simple oversight on my part somehow. Still pretty new to this, but I feel I am getting closer to getting this thing to work. I want to record in HQ!

```
chris@chris-desktop:/usr/src/alsa/alsa-driver-1.0.22.1$ sudo ./configure --with-cards=usb-audio --with-sequencer=yes ; make ; make install
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
checking for current directory... /usr/src/alsa/alsa-driver-1.0.22.1
checking cross compile... 
checking for directory with ALSA kernel sources... ./configure: line 5107: cd: ../alsa-kmirror: No such file or directory
../alsa-kmirror
checking for directory with kernel source... /lib/modules/2.6.31-9-rt/build
checking for directory with kernel build... 
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.31-9-rt
checking for GCC version... ./configure: eval: line 5495: syntax error near unexpected token `)'
./configure: eval: line 5495: `my_compiler_version=4.4.1-4ubuntu8)'
Kernel compiler:  Used compiler: gcc (Ubuntu 4.4.1-4ubuntu8) 4.4.1

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for updating alsa-kernel version.h... yes
checking for CONFIG_EXPERIMENTAL... yes
checking for directory to store kernel modules... /lib/modules/2.6.31-9-rt/kernel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... no
checking for processor type... x86_64
checking for ISA DMA API... yes
checking for 32bit compat support... yes
checking for kernel linux/config.h... no
Creating <linux/config.h>...
checking for deprecated linux/config.h... checking to modify of kernel linux/kmod.h... no
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
checking for kernel linux/io.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for kernel linux/pm_qos_params.h... yes
checking for kernel linux/kthread.h... yes
checking for kernel asm/irq_regs.h... yes
checking for kernel linux/seq_file.h... yes
checking for kernel linux/debugfs.h... yes
checking for kernel linux/gpio.h... yes
checking for kernel linux/bug.h... yes
checking for kernel linux/math64.h... yes
checking for kernel linux/regulator/consumer.h... yes
checking for kernel linux/dmi.h... yes
checking for kernel linux/bitrev.h... yes
checking for kernel linux/hrtimer.h... yes
checking for kernel linux/gcd.h... yes
checking for kernel module symbol versions... yes
checking for has ioport support... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... yes
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for pc-speaker platform in kernel... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... no
checking for Kernel ISA-PnP module support... no
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
checking for tty->count is the atomic type... yes
checking for video_get_drvdata... yes
checking for video_drvdata... yes
checking for V4L1 layer... yes
checking for V4L2 layer... yes
checking for io_remap_pfn_range... yes
checking for kcalloc... yes
checking for kstrdup... yes
checking for kstrndup... yes
checking for kzalloc... yes
checking for create_workqueue with flags... no
checking for pci_ioremap_bar... yes
checking for saved_config_space in pci_dev... yes
checking for new pci_save_state... yes
checking for register_sound_special_device... yes
checking for driver extra-version... 
checking for driver version... 1.0.22.1
checking for dynamic minor numbers... no
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC support... no
checking for HPET support... yes
checking for Procfs support... yes
checking for USB support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for new IRQ handler... yes
checking for gfp_t... yes
checking for GFP_DMA32... yes
checking for page_to_pfn... yes
checking for PnP suspend/resume... yes
checking for device_create_drvdata... no
checking for new unlocked/compat_ioctl... yes
checking for builtin _Bool support... yes
checking for x86-compatible PC... no
checking for High-Res timers... yes
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for CONFIG_HAS_DMA... yes
checking for cards to compile driver for... usb-audio
checking for additonal options to compile driver for... all
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
Hacking autoconf.h...
make dep
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.22.1'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.22.1/include'
make -C sound prepare
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.22.1/include/sound'
/bin/sh: cannot create .includes.tmp: Permission denied
make[3]: *** [.includes.tmp] Error 2
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.22.1/include/sound'
make[2]: *** [prepare] Error 2
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.22.1/include'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.22.1'
make: *** [include/sndversions.h] Error 2
if [ -L /usr/include/sound ]; then \
        rm -f /usr/include/sound; \
        ln -sf /usr/src/alsa/alsa-driver-1.0.22.1/include/sound /usr/include/sound; \
    else \
        rm -rf /usr/include/sound; \
        install -d -m 755 -g root -o root /usr/include/sound; \
        for f in include/sound/*.h; do \
            install -m 644 -g root -o root $f /usr/include/sound; \
        done \
    fi
rm: cannot remove `/usr/include/sound/asound.h': Permission denied
rm: cannot remove `/usr/include/sound/hdspm.h': Permission denied
rm: cannot remove `/usr/include/sound/sscape_ioctl.h': Permission denied
rm: cannot remove `/usr/include/sound/asound_fm.h': Permission denied
rm: cannot remove `/usr/include/sound/asequencer.h': Permission denied
rm: cannot remove `/usr/include/sound/sfnt_info.h': Permission denied
rm: cannot remove `/usr/include/sound/sb16_csp.h': Permission denied
rm: cannot remove `/usr/include/sound/hdsp.h': Permission denied
rm: cannot remove `/usr/include/sound/emu10k1.h': Permission denied
install: cannot stat `include/sound/*.h': No such file or directory
make: *** [install-headers] Error 1

```Thanks for your help

---

### Post by sojournerC on 2010-01-03
if it helps here is the output of cat /proc/asound/cards 

```
chris@chris-desktop:~$ cat /proc/sound
cat: /proc/sound: No such file or directory
chris@chris-desktop:~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe7f4000 irq 16
 1 [PCR1           ]: USB-Audio - PCR-1
                      EDIROL PCR-1 at usb-0000:00:12.1-1.1, full speed
 2 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfe9e8000 irq 19
```

and lsusb

```
chris@chris-desktop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 03f0:5711 Hewlett-Packard PhotoSmart C4100 series
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 006: ID 0582:0064 Roland Corp. EDIROL PCR-1 WAVE
Bus 004 Device 005: ID 0582:0065 Roland Corp. EDIROL PCR-1 MIDI
Bus 004 Device 004: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 004 Device 003: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 004 Device 002: ID 0451:2036 Texas Instruments, Inc. TUSB2036 Hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by dummy910 on 2010-01-03
You probably need to give the account **Privileges**, here's how (in Gnome):

* **System**[color=red]>[/color]**Administration**[color=red]>[/color]**Users and Groups**
then,
* click the **Make Changes** _button_ at lower center section of that window to allow any changes,
then,
* select the account you want to alter by pressing the **Properties** _button_ in the column on the right of window,
then,
* select the **User Privileges** _tab_,
then scroll through the list to assign 'Privileges' to given sections of the Operating System(the **Use Audio Devices** in this case) by placing a **check box-tick**,
then,
* **log out**, then **log back in** and you should be good to go!

---

### Post by sojournerC on 2010-01-04
I appreciate the quick reply. When I went to users and groups, my account [chris] already had permission for sound cards. I gave permission to root, however, but still received the same error. 

Really, I am not sure that I need to reload the driver. I have the alsa driver. I worked on it all night and this morning and have arrived at the following. 

The midi driver for the sound card works, but the built in audio interface is not recognized in preferences>sound.

I think it is due to the fact that the snd-usb-audio module has the alias for the midi but not for the wave driver. I've drawn this conclusion from the following: 

From the output of 'lsusb' above i determine that the midi has vid:0582 and pid:0065 while the wave has vid:0582 and pid:0064. 

Now the output of modinfo snd-usb-audio shows that the alias for the midi is present ion the long list of aliases but not the wave: 

```
alias:          usb:v0582p0074d*dc*dsc*dp*icFFisc*ip*
alias:          usb:v0582p006Dd*dc*dsc*dp*ic*isc*ip*
[COLOR=Red]alias:          usb:v0582p006Ad*dc*dsc*dp*icFFisc*ip*
alias:          usb:v0582p0065d*dc*dsc*dp*ic*isc*ip*[/COLOR]
alias:          usb:v0582p0060d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p0052d*dc*dsc*dp*ic*isc*ip*
```...

SO...somehow I need to patch the driver or alias or whatever into the snd-usb-audio module. 

I think I have found this patch here [http://www.gelato.unsw.edu.au/lxr/source/sound/usb/usbquirks.h?a=sparc64](http://www.gelato.unsw.edu.au/lxr/source/sound/usb/usbquirks.h?a=sparc64) at line 1169, but here also there is not support for the wave driver. Obviously, i need to create that information, but lack the expertise to do so. Moreover, i do not know where to put it if I find it or create it...

This is what I've narrowed it down to. I have even gotten the usb card to take position hw:0 and have tried to run jackd off of it, but jackd returns that it could not load the alsa-module, likely because it isn't there for the particular product id of my card. Right? 

Any light that could be shed would be much appreciated. Thanks...

---

