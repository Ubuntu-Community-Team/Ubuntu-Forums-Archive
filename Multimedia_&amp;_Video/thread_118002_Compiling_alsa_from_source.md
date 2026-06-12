---
title: "Compiling alsa from source"
date: 2006-01-15
forum: Multimedia &amp; Video
---

### Post by rossjman1 on 2006-01-15
Hi. I have an HP that had an Conext Riptide. I pulled that crap card out and bought another crap wincard (SB Live! 24-bit - alsa driver ca0106). This didnt work. I found another sound card that i had lying around (Ensoniq ES1370 - alsa driver ens1370). However none of these cards work. So in a desperate move to get either the SB or the Ensoniq card to work I'm compiling the dev build of alsa-driver, alsa-lib, and alsa-utils from source. I get errors on the first step about permissions, but I used sudo! Please help. Thanks in advance.

---

### Post by rossjman1 on 2006-01-15
```
jeff@ubuntu:~/alsa-driver-1.0.11rc2$ sudo ./configure --with-cards=ca0106,ens1370 --with-sequencer=yes;make;make install
Password:
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/jeff/alsa-driver-1.0.11rc2
checking cross compile...
checking for directory with kernel source... /lib/modules/2.6.12-9-386/build
checking for directory with kernel build...
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.12-9-386
checking for GCC version... Kernel compiler: gcc 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8) Used compiler: gcc (GCC) 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
checking for built-in ALSA... "no"
checking for existing ALSA module... "yes"
checking for Red Hat kernel... "auto"
checking for Red Hat kernel... "no"
checking for SUSE kernel... "auto"
checking for SUSE kernel... "no"
checking to modify of kernel linux/kmod.h... "no"
checking for kernel linux/compiler.h... "yes"
checking for kernel linux/pm.h... "yes"
checking for kernel linux/spinlock.h... "yes"
checking for kernel linux/irq.h... "yes"
checking for kernel linux/threads.h... "yes"
checking for kernel linux/rwsem.h... "yes"
checking for kernel linux/gameport.h... "yes"
checking for kernel linux/devfs_fs_kernel.h... "yes"
checking for kernel linux/highmem.h... "yes"
checking for kernel linux/workqueue.h... "yes"
checking for kernel linux/dma-mapping.h... "yes"
checking for kernel asm/hw_irq.h... "yes"
checking for kernel linux/device.h... "yes"
checking for kernel linux/platform_device.h... "no"
Creating <linux/platform_device.h>...
checking for kernel linux/jiffies.h... "yes"
checking for kernel linux/compat.h... "yes"
checking for kernel linux/adb.h... "yes"
checking for kernel linux/cuda.h... "yes"
checking for kernel linux/pmu.h... "yes"
checking for kernel linux/moduleparam.h... "yes"
checking for kernel linux/syscalls.h... "yes"
checking for kernel linux/firmware.h... "yes"
checking for kernel linux/err.h... "yes"
checking for kernel linux/bitmap.h... "yes"
checking for kernel module symbol versions... "yes"
checking for PCI support in kernel... "yes"
checking for I2C driver in kernel... module
checking for firmware loader... module
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.12-9-386/kernel/sound
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... "yes"
checking for processor type... i386
checking for i386 machine type... default
checking for ISA DMA API... "yes"
checking for SMP... "no"
checking for Video device support in kernel... "yes"
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... "yes"
checking for strlcpy... "yes"
checking for snprintf... "yes"
checking for vsnprintf... "yes"
checking for scnprintf... "yes"
checking for sscanf... "yes"
checking for vmalloc_to_page... "yes"
checking for old kmod... "no"
checking for PDE... "yes"
checking for pci_set_consistent_dma_mask... "yes"
checking for pci_dev_present... "yes"
checking for msleep... "yes"
checking for msleep_interrupt... "yes"
checking for msecs_to_jiffies... "yes"
checking for tty->count is the atomic type... "no"
checking for video_get_drvdata... "yes"
checking for io_remap_pfn_range... "yes"
checking for kcalloc... "yes"
checking for kstrdup... "no"
checking for kzalloc... "no"
checking for create_workqueue with flags... "no"
checking for saved_config_space in pci_dev... "yes"
checking for new pci_save_state... "yes"
checking for register_sound_special_device... "no"
checking for driver version... 1.0.11rc2
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for RTC callback support in kernel... may be buggy, skipped
checking for HPET support... "yes"
checking for dynamic minor numbers... no
checking for support of old API... yes
checking for Procfs support... "yes"
checking for USB support... "yes"
checking for class_simple... "yes"
checking for old driver suspend/resume callbacks... "yes"
checking for removal of page-reservation for nopage/mmap... "no"
checking for nested class_device... "no"
checking for PnP suspend/resume... "no"
checking for new unlocked/compat_ioctl... "yes"
checking for PC-Speaker hook... "no"
checking for kernel PCMCIA
checking for PCMCIA support... "yes"
checking for PC9800 support in kernel... "no"
checking for parallel port support... "yes"
checking for which soundcards to compile driver for... ca0106 ens1370
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/pci_ids_compat.h
config.status: creating include/config.h
config.status: include/config.h is unchanged
config.status: creating include/config1.h
config.status: include/config1.h is unchanged
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...
make dep
make[1]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2'
make[2]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/acore'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/acore/ioctl32'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/acore/ioctl32'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/acore/oss'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/acore/oss'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/acore/seq'
make[4]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/acore/seq/instr'
make[4]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/acore/seq/instr'
make[4]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/acore/seq/oss'
make[4]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/acore/seq/oss'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/acore/seq'
make[2]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/acore'
make[2]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/i2c'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/i2c/other'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/i2c/other'
make[2]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/i2c'
make[2]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/drivers'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/drivers/mpu401'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/drivers/mpu401'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/drivers/opl3'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/drivers/opl3'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/drivers/opl4'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/drivers/opl4'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/drivers/pcsp'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/drivers/pcsp'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/drivers/vx'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/drivers/vx'
make[2]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/drivers'
make[2]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/isa'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/isa/ad1816a'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/isa/ad1816a'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/isa/ad1848'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/isa/ad1848'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/isa/cs423x'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/isa/cs423x'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/isa/es1688'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/isa/es1688'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/isa/gus'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/isa/gus'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/isa/msnd'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/isa/msnd'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/isa/opti9xx'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/isa/opti9xx'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/isa/sb'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/isa/sb'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/isa/wavefront'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/isa/wavefront'
make[2]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/isa'
make[2]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/synth'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/synth/emux'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/synth/emux'
make[2]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/synth'
make[2]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/pci'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/pci/ac97'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/pci/ac97'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/pci/ali5451'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/pci/ali5451'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/pci/asihpi'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/pci/asihpi'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/pci/au88x0'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/pci/au88x0'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/pci/ca0106'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/pci/ca0106'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/pci/cs46xx'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/pci/cs46xx'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/pci/cs5535audio'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/pci/cs5535audio'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/pci/echoaudio'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/pci/echoaudio'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/pci/emu10k1'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/pci/emu10k1'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/pci/hda'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/pci/hda'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/pci/ice1712'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/pci/ice1712'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/pci/korg1212'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/pci/korg1212'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/pci/mixart'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/pci/mixart'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/pci/nm256'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/pci/nm256'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/pci/pcxhr'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/pci/pcxhr'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/pci/pdplus'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/pci/pdplus'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/pci/riptide'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/pci/riptide'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/pci/rme9652'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/pci/rme9652'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/pci/trident'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/pci/trident'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/pci/vx222'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/pci/vx222'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/pci/ymfpci'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/pci/ymfpci'
make[2]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/pci'
make[2]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/usb'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/usb/usx2y'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/usb/usx2y'
make[2]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/usb'
make[2]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/pcmcia'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/pcmcia/pdaudiocf'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/pcmcia/pdaudiocf'
make[3]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/pcmcia/vx'
make[3]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/pcmcia/vx'
make[2]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/pcmcia'
make[1]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2'
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/jeff/alsa-driver-1.0.11rc2  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /home/jeff/alsa-driver-1.0.11rc2/acore/memalloc.o
  CC [M]  /home/jeff/alsa-driver-1.0.11rc2/acore/init.o
  CC [M]  /home/jeff/alsa-driver-1.0.11rc2/acore/misc_driver.o
/home/jeff/alsa-driver-1.0.11rc2/acore/misc_driver.c: In function `register_pnp_pm_callback':
/home/jeff/alsa-driver-1.0.11rc2/acore/misc_driver.c:687: warning: `pm_register' is deprecated (declared at include/linux/pm.h:106)
/home/jeff/alsa-driver-1.0.11rc2/acore/misc_driver.c: In function `unregister_pnp_pm_callback':
/home/jeff/alsa-driver-1.0.11rc2/acore/misc_driver.c:706: warning: `pm_unregister' is deprecated (declared at include/linux/pm.h:111)
  LD [M]  /home/jeff/alsa-driver-1.0.11rc2/acore/snd.o
  LD [M]  /home/jeff/alsa-driver-1.0.11rc2/acore/snd-timer.o
  LD [M]  /home/jeff/alsa-driver-1.0.11rc2/acore/snd-pcm.o
  LD [M]  /home/jeff/alsa-driver-1.0.11rc2/acore/snd-page-alloc.o
  LD [M]  /home/jeff/alsa-driver-1.0.11rc2/acore/snd-rawmidi.o
  CC [M]  /home/jeff/alsa-driver-1.0.11rc2/pci/ens1370.o
  LD [M]  /home/jeff/alsa-driver-1.0.11rc2/pci/snd-ens1370.o
  CC [M]  /home/jeff/alsa-driver-1.0.11rc2/pci/ac97/ac97_codec.o
  LD [M]  /home/jeff/alsa-driver-1.0.11rc2/pci/ac97/snd-ac97-bus.o
  LD [M]  /home/jeff/alsa-driver-1.0.11rc2/pci/ac97/snd-ac97-codec.o
  LD [M]  /home/jeff/alsa-driver-1.0.11rc2/pci/ac97/snd-ak4531-codec.o
  CC [M]  /home/jeff/alsa-driver-1.0.11rc2/pci/ca0106/ca0106_main.o
  CC [M]  /home/jeff/alsa-driver-1.0.11rc2/pci/ca0106/ca0106_proc.o
  CC [M]  /home/jeff/alsa-driver-1.0.11rc2/pci/ca0106/ca0106_mixer.o
  LD [M]  /home/jeff/alsa-driver-1.0.11rc2/pci/ca0106/snd-ca0106.o
  Building modules, stage 2.
  MODPOST
  LD [M]  /home/jeff/alsa-driver-1.0.11rc2/acore/snd-page-alloc.ko
  LD [M]  /home/jeff/alsa-driver-1.0.11rc2/acore/snd-pcm.ko
  LD [M]  /home/jeff/alsa-driver-1.0.11rc2/acore/snd-rawmidi.ko
  LD [M]  /home/jeff/alsa-driver-1.0.11rc2/acore/snd-timer.ko
  LD [M]  /home/jeff/alsa-driver-1.0.11rc2/acore/snd.ko
  LD [M]  /home/jeff/alsa-driver-1.0.11rc2/pci/ac97/snd-ac97-bus.ko
  LD [M]  /home/jeff/alsa-driver-1.0.11rc2/pci/ac97/snd-ac97-codec.ko
  LD [M]  /home/jeff/alsa-driver-1.0.11rc2/pci/ac97/snd-ak4531-codec.ko
  LD [M]  /home/jeff/alsa-driver-1.0.11rc2/pci/ca0106/snd-ca0106.ko
  LD [M]  /home/jeff/alsa-driver-1.0.11rc2/pci/snd-ens1370.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
utils/link-modules /home/jeff/alsa-driver-1.0.11rc2

ALSA modules were successfully compiled.

find /lib/modules/2.6.12-9-386/kernel/sound -name 'snd*.*o' | xargs rm -f
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/core/snd-hwdep.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/core/oss/snd-mixer-oss.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/core/oss/snd-pcm-oss.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/core/seq/snd-seq-dummy.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/core/seq/instr/snd-ainstr-simple.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/core/seq/instr/snd-ainstr-fm.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/core/seq/instr/snd-ainstr-gf1.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/core/seq/instr/snd-ainstr-iw.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/core/seq/oss/snd-seq-oss.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/core/seq/snd-seq-midi-emul.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/core/seq/snd-seq-device.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/core/seq/snd-seq-instr.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/core/seq/snd-seq-midi-event.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/core/seq/snd-seq-midi.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/core/seq/snd-seq-virmidi.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/core/seq/snd-seq.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/core/snd-page-alloc.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/core/snd-pcm.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/core/snd-rawmidi.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/core/snd-rtctimer.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/core/snd-timer.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/core/snd.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/drivers/snd-dummy.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/drivers/mpu401/snd-mpu401.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/drivers/opl3/snd-opl3-synth.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/drivers/opl3/snd-opl3-lib.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/drivers/opl4/snd-opl4-synth.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/drivers/opl4/snd-opl4-lib.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/drivers/snd-serial-u16550.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/drivers/snd-mtpav.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/drivers/vx/snd-vx-lib.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/drivers/snd-virmidi.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/i2c/snd-cs8427.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/i2c/other/snd-ak4xxx-adda.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/i2c/other/snd-ak4114.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/i2c/other/snd-ak4117.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/i2c/other/snd-tea575x-tuner.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/i2c/snd-tea6330t.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/i2c/snd-i2c.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/snd-als100.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/ad1816a/snd-ad1816a-lib.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/ad1816a/snd-ad1816a.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/ad1848/snd-ad1848-lib.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/ad1848/snd-ad1848.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/cs423x/snd-cs4231-lib.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/cs423x/snd-cs4231.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/cs423x/snd-cs4232.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/cs423x/snd-cs4236-lib.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/cs423x/snd-cs4236.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/es1688/snd-es1688-lib.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/es1688/snd-es1688.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/gus/snd-gus-synth.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/gus/snd-gus-lib.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/gus/snd-interwave-stb.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/gus/snd-gusclassic.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/gus/snd-gusextreme.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/gus/snd-gusmax.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/gus/snd-interwave.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/opti9xx/snd-opti92x-ad1848.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/opti9xx/snd-opti92x-cs4231.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/opti9xx/snd-opti93x.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/sb/snd-emu8000-synth.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/sb/snd-es968.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/sb/snd-sb-common.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/sb/snd-sb16-csp.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/sb/snd-sb16-dsp.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/sb/snd-sb16.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/sb/snd-sb8-dsp.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/sb/snd-sb8.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/sb/snd-sbawe.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/snd-azt2320.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/snd-cmi8330.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/snd-dt019x.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/snd-es18xx.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/snd-opl3sa2.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/snd-sgalaxy.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/snd-sscape.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/isa/wavefront/snd-wavefront.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/korg1212/snd-korg1212.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/ac97/snd-ac97-codec.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/ac97/snd-ak4531-codec.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/ali5451/snd-ali5451.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/au88x0/snd-au8810.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/au88x0/snd-au8820.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/au88x0/snd-au8830.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/ca0106/snd-ca0106.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/cs46xx/snd-cs46xx.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/emu10k1/snd-emu10k1.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/emu10k1/snd-emu10k1x.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/hda/snd-hda-codec.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/hda/snd-hda-intel.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/ice1712/snd-ice1712.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/ice1712/snd-ice1724.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-als4000.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/mixart/snd-mixart.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/nm256/snd-nm256.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/rme9652/snd-hdspm.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/rme9652/snd-hdsp.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/rme9652/snd-rme9652.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-via82xx-modem.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-atiixp-modem.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-atiixp.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-azt3328.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-bt87x.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-cmipci.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-cs4281.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-ens1370.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-ens1371.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-es1938.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-es1968.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-fm801.ko': 
``` continued in next post

---

### Post by rossjman1 on 2006-01-15
```
Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-intel8x0.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-intel8x0m.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-maestro3.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-rme32.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-rme96.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-sonicvibes.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/snd-via82xx.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/trident/snd-trident-synth.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/trident/snd-trident.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/vx222/snd-vx222.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pci/ymfpci/snd-ymfpci.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pcmcia/vx/snd-vx-cs.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pcmcia/vx/snd-vxp440.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/pcmcia/vx/snd-vxpocket.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/synth/snd-util-mem.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/synth/emux/snd-emux-synth.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/usb/snd-usb-audio.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/usb/snd-usb-lib.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/sound/usb/usx2y/snd-usb-usx2y.ko': Permission denied
make[1]: Entering directory `/home/jeff/alsa-driver-1.0.11rc2/acore'
mkdir -p /lib/modules/2.6.12-9-386/kernel/sound/acore
mkdir: cannot create directory `/lib/modules/2.6.12-9-386/kernel/sound/acore': Permission denied
make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/home/jeff/alsa-driver-1.0.11rc2/acore'
make: *** [install-modules] Error 1
jeff@ubuntu:~/alsa-driver-1.0.11rc2$

```

---

### Post by FarEast on 2006-01-16
Hi rossjman1,

I do not think it good trying to remove existing ALSA modules.
You can install new modules simply by executing:

```
$ sudo make install
```

And I wonder if they will work...

---

### Post by Sef on 2006-01-17
> ... I'm compiling the dev build of alsa-driver, alsa-lib, and alsa-utils from source. I get errors on the first step about permissions....

Before compiling did you download build-essential?  If not, then you will not be able to do make or make install.

sudo apt-get install build-essential

---

### Post by sal on 2006-01-17
[QUOTE=rossjman1]Hi. I have an HP that had an Conext Riptide. I pulled that crap card out and bought another crap wincard (SB Live! 24-bit - alsa driver ca0106). This didnt work. I found another sound card that i had lying around (Ensoniq ES1370 - alsa driver ens1370). However none of these cards work. So in a desperate move to get either the SB or the Ensoniq card to work I'm compiling the dev build of alsa-driver, alsa-lib, and alsa-utils from source. I get errors on the first step about permissions, but I used sudo! Please help. Thanks in advance.[/QUOTE]

last time i did the compile of the alsa drivers (version 1.0.10rc1 i think) i had to do it with sudo su and then it all worked. by the way i was using the same ca0106 card as you. i had to go back to on board (intel8x0) because at the time the mic would not work on the ca0106 card. if you're using the very latest alsa let me know if the mic now works on the ca0106 card. thanks.

---

### Post by rossjman1 on 2006-01-17
The forums were not working for me yesterday, but I figured it out. The sudo was only carried out on the ./configure and not the make or make install. I just did a sudo su to fix this. Everything installed fine with no errors in make or make install. However, when I do a modprobe on either one of the cards I compiled I get errors. I'm not on my computer right now, but I will post the errors once I get home.

---

### Post by rossjman1 on 2006-01-17
After restarting my computer, it works! However, the volume is too low. Everything is unmuted and the volume is all the way up. The speakers are working, since I use these speakers to listen to my ipod. The speakers are pluged in on the 'line out' jack because the ensoniq card has no headphone/speaker jack.
[http://img67.imageshack.us/img67/1360/untitled4la.png](http://img67.imageshack.us/img67/1360/untitled4la.png)

---

### Post by rossjman1 on 2006-01-19
Bump. Anyone have any ideas?

---

### Post by rossjman1 on 2006-03-21
Oh my God, I feel like an idiot, yet am excited as hell. The remote audio (the little chip that has the speaker jack on it) wasn't plugged in.

---

