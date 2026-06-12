---
title: "No sound device in 10.10, hda-intel"
date: 2011-01-01
forum: Multimedia Software
---

### Post by battybiologist on 2011-01-01
Hey,

So I was trying to fix my microphone and headphone/mic jack, and the linuxant package failed to unpack right -- that totally killed my sound (the speakers were working before). I've tried a lot of things to fix this, and I'm worried that I'll have to reinstall.

Here are some diagnostics:

[http://www.alsa-project.org/db/?f=85a1862db2f73ecfabae1cda8276635fdf06d07e](http://www.alsa-project.org/db/?f=85a1862db2f73ecfabae1cda8276635fdf06d07e)
```
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Thu Dec 30 21:59:43 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      LENOVO
Product Name:      3508CTO


!!Kernel Information
!!------------------

Kernel release:    2.6.35-24-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.23
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------



!!PCI Soundcards installed in the system
!!--------------------------------------

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:14.2 0403: 1002:4383
    Subsystem: 17aa:21b2


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------



!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:235: no soundcards found...

ARECORD

arecord: device_list:235: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
aes_i586
aes_generic
binfmt_misc
joydev
parport_pc
ppdev
dm_crypt
fglrx
uvcvideo
r8192se_pci
videodev
v4l1_compat
cfg80211
agpgart
led_class
nvram
psmouse
shpchp
serio_raw
i2c_piix4
k8temp
lp
parport
usbhid
hid
usb_storage
ahci
video
output
r8169
libahci
mii


!!ALSA/HDA dmesg
!!------------------

```driver compile failure, full text:
```
for i in control postinst postrm ; do \                                      
        if [ -f debian/$i.orig ]; then \                                     
        mv -f debian/$i.orig debian/$i ; \                                   
        fi ; \                                                               
        done                                                                 
rm -f control-munge                                                          
make mrproper                                                                
make[1]: Entering directory `/usr/src/modules/alsa-driver'                   
rm -f .depend *.o snd.map*                                                   
rm -f modules/*.o modules/*.ko                                               
make[2]: Entering directory `/usr/src/modules/alsa-driver/include'           
make[2]: Leaving directory `/usr/src/modules/alsa-driver/include'            
make[1]: Leaving directory `/usr/src/modules/alsa-driver'                    
rm -f configure-stamp                                                        
rm -f build-stamp                                                            
/usr/bin/make -f debian/rules binary-modules                                 
make[1]: Entering directory `/usr/src/modules/alsa-driver'                   
CC="gcc" ./configure --prefix=/usr --with-kernel=/usr/src/linux              
--with-build=/usr/src/linux                                                  
--with-moddir=/lib/modules/2.6.35-24-generic/updates/alsa                    
--with-sequencer=yes --with-isapnp=yes --with-debug=detect                   
--with-cards="hda-intel"                                                     
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
checking for current directory... /usr/src/modules/alsa-driver               
checking cross compile...                                                    
checking for directory with ALSA kernel sources... ../alsa-kmirror           
checking for directory with kernel source... /usr/src/linux                  
checking for directory with kernel build... /usr/src/linux                   
checking for kernel linux/version.h ... linux/version.h                      
checking for kernel linux/autoconf.h generated/autoconf.h...                 
generated/autoconf.h                                                         
checking for kernel linux/utsrelease.h generated/utsrelease.h...             
generated/utsrelease.h                                                       
checking for kernel version... 2.6.35-24-generic                             
checking for GCC version... Kernel compiler:  Used compiler: gcc             
(Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5                                        
                                                                             
*** NO PREDEFINED KERNEL COMPILER IS DETECTED                                
*** Assuming the same compiler is used with the current system compiler.     
                                                                             
*** Please make sure that the same compiler version was used for building    
kernel.     
    
checking for built-in ALSA... no                                             
checking for existing ALSA module... yes                                     
checking for Red Hat kernel... auto                                          
checking for Red Hat kernel... no                                            
checking for SUSE kernel... auto                                             
checking for SUSE kernel... no                                               
checking for updating alsa-kernel version.h... yes                           
checking for CONFIG_EXPERIMENTAL... yes                                      
checking for directory to store kernel modules...                            
/lib/modules/2.6.35-24-generic/updates/alsa                                  
checking for verbose procfs... on                                            
checking for verbose printk... on                                            
checking for debug level... verbose                                          
checking for ISA support in kernel... yes                                    
checking for processor type... i686                                          
checking for ISA DMA API... yes                                              
checking for kernel linux/config.h... no                                     
Creating <linux/config.h>...                                                 
checking for deprecated linux/config.h... checking to modify of kernel       
linux/kmod.h... no                                                           
checking for kernel linux/utsrelease.h... no                                 
Creating a dummy <linux/utsrelease.h>...                                     
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
checking for kernel linux/gfp.h... yes                                       
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
checking for driver version... 1.0.23                                        
checking for dynamic minor numbers... no                                     
checking for sequencer support... yes                                        
checking for OSS/Free emulation... yes                                       
checking for OSS PCM plugin system inclusion... yes                          
checking for RTC support... no                                               
checking for HPET support... yes                                             
checking for Procfs support... yes                                           
checking for USB support... yes                                              
checking for kernel linux/usb/audio-v2.h... yes                              
checking for kernel linux/usb/audio.h... yes
checking for valid v1 in linux/usb/audio.h... no                             
Creating <linux/usb/audio.h>...                                              
checking for kernel linux/usb/ch9.h... yes                                   
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
checking for cards to compile driver for... hda-intel                        
checking for additonal options to compile driver for... all                  
configure: creating ./config.status                                          
config.status: creating version                                              
config.status: creating Makefile.conf                                        
config.status: WARNING:  Makefile.conf.in seems to ignore the                
--datarootdir setting
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
touch configure-stamp
/usr/bin/make  compile                                                       
make[2]: Entering directory `/usr/src/modules/alsa-driver'                   
/usr/bin/make dep                                                            
make[3]: Entering directory `/usr/src/modules/alsa-driver'                   
make[4]: Entering directory `/usr/src/modules/alsa-driver/include'           
/usr/bin/make -C sound prepare                                               
make[5]: Entering directory `/usr/src/modules/alsa-driver/include/sound'     
/usr/bin/make .includes.tmp                                                  
make[6]: Entering directory `/usr/src/modules/alsa-driver/include/sound'     
make[6]: Leaving directory `/usr/src/modules/alsa-driver/include/sound'      
/usr/bin/make prepare2                                                       
make[6]: Entering directory `/usr/src/modules/alsa-driver/include/sound'     
cp ../../alsa-kernel/include/ac97_codec.h .                                  
patch -p0 -i ac97_codec.patch ac97_codec.h                                   
patching file ac97_codec.h
ln -s ../../alsa-kernel/include/aci.h                                        
ln -s ../../alsa-kernel/include/ad1816a.h                                    
ln -s ../../alsa-kernel/include/ad1843.h                                     
ln -s ../../alsa-kernel/include/ak4113.h                                     
ln -s ../../alsa-kernel/include/ak4114.h                                     
ln -s ../../alsa-kernel/include/ak4117.h                                     
ln -s ../../alsa-kernel/include/ak4531_codec.h                               
ln -s ../../alsa-kernel/include/ak4xxx-adda.h                                
ln -s ../../alsa-kernel/include/asequencer.h                                 
ln -s ../../alsa-kernel/include/asound.h                                     
ln -s ../../alsa-kernel/include/asound_fm.h                                  
ln -s ../../alsa-kernel/include/asoundef.h                                   
ln -s ../../alsa-kernel/include/atmel-abdac.h                                
ln -s ../../alsa-kernel/include/atmel-ac97c.h                                
ln -s ../../alsa-kernel/include/control.h
cp ../../alsa-kernel/include/core.h .                                        
patch -p0 -i core.patch core.h                                               
patching file core.h                                                         
ln -s ../../alsa-kernel/include/cs4231-regs.h                                
ln -s ../../alsa-kernel/include/cs46xx.h                                     
ln -s ../../alsa-kernel/include/cs46xx_dsp_scb_types.h                       
ln -s ../../alsa-kernel/include/cs46xx_dsp_spos.h                            
ln -s ../../alsa-kernel/include/cs46xx_dsp_task_types.h                      
ln -s ../../alsa-kernel/include/cs8403.h                                     
ln -s ../../alsa-kernel/include/cs8427.h                                     
ln -s ../../alsa-kernel/include/emu10k1.h                                    
ln -s ../../alsa-kernel/include/emu10k1_synth.h                              
ln -s ../../alsa-kernel/include/emu8000.h                                    
ln -s ../../alsa-kernel/include/emu8000_reg.h                                
ln -s ../../alsa-kernel/include/emux_legacy.h
ln -s ../../alsa-kernel/include/emux_synth.h                                 
ln -s ../../alsa-kernel/include/es1688.h                                     
ln -s ../../alsa-kernel/include/gus.h                                        
ln -s ../../alsa-kernel/include/hda_hwdep.h                                  
ln -s ../../alsa-kernel/include/hdsp.h                                       
ln -s ../../alsa-kernel/include/hdspm.h                                      
ln -s ../../alsa-kernel/include/hwdep.h                                      
ln -s ../../alsa-kernel/include/i2c.h                                        
ln -s ../../alsa-kernel/include/info.h                                       
ln -s ../../alsa-kernel/include/initval.h                                    
ln -s ../../alsa-kernel/include/jack.h                                       
ln -s ../../alsa-kernel/include/l3.h                                         
ln -s ../../alsa-kernel/include/memalloc.h                                   
ln -s ../../alsa-kernel/include/minors.h                                     
ln -s ../../alsa-kernel/include/mixer_oss.h
ln -s ../../alsa-kernel/include/mpu401.h                                     
ln -s ../../alsa-kernel/include/opl3.h                                       
ln -s ../../alsa-kernel/include/opl4.h                                       
ln -s ../../alsa-kernel/include/pcm-indirect.h                               
cp ../../alsa-kernel/include/pcm.h .                                         
patch -p0 -i pcm.patch pcm.h                                                 
patching file pcm.h                                                          
ln -s ../../alsa-kernel/include/pcm_oss.h                                    
ln -s ../../alsa-kernel/include/pcm_params.h                                 
ln -s ../../alsa-kernel/include/pt2258.h                                     
ln -s ../../alsa-kernel/include/pxa2xx-lib.h                                 
ln -s ../../alsa-kernel/include/rawmidi.h                                    
ln -s ../../alsa-kernel/include/s3c24xx_uda134x.h                            
ln -s ../../alsa-kernel/include/sb.h                                         
ln -s ../../alsa-kernel/include/sb16_csp.h
ln -s ../../alsa-kernel/include/seq_device.h                                 
ln -s ../../alsa-kernel/include/seq_kernel.h                                 
ln -s ../../alsa-kernel/include/seq_midi_emul.h                              
ln -s ../../alsa-kernel/include/seq_midi_event.h                             
ln -s ../../alsa-kernel/include/seq_oss.h                                    
ln -s ../../alsa-kernel/include/seq_oss_legacy.h                             
ln -s ../../alsa-kernel/include/seq_virmidi.h                                
ln -s ../../alsa-kernel/include/sfnt_info.h                                  
ln -s ../../alsa-kernel/include/sh_dac_audio.h                               
ln -s ../../alsa-kernel/include/sh_fsi.h                                     
ln -s ../../alsa-kernel/include/snd_wavefront.h                              
ln -s ../../alsa-kernel/include/soc-dai.h                                    
ln -s ../../alsa-kernel/include/soc-dapm.h                                   
ln -s ../../alsa-kernel/include/soc-of-simple.h                              
ln -s ../../alsa-kernel/include/soc.h
ln -s ../../alsa-kernel/include/soundfont.h                                  
ln -s ../../alsa-kernel/include/tea575x-tuner.h                              
ln -s ../../alsa-kernel/include/tea6330t.h                                   
ln -s ../../alsa-kernel/include/timer.h                                      
ln -s ../../alsa-kernel/include/tlv.h                                        
ln -s ../../alsa-kernel/include/tlv320dac33-plat.h                           
ln -s ../../alsa-kernel/include/tpa6130a2-plat.h                             
ln -s ../../alsa-kernel/include/trident.h                                    
ln -s ../../alsa-kernel/include/uda134x.h                                    
ln -s ../../alsa-kernel/include/uda1380.h                                    
ln -s ../../alsa-kernel/include/util_mem.h                                   
ln -s ../version.h                                                           
ln -s ../../alsa-kernel/include/vx_core.h                                    
ln -s ../../alsa-kernel/include/wavefront.h                                  
ln -s ../../alsa-kernel/include/wm2000.h
ln -s ../../alsa-kernel/include/wm8903.h                                     
ln -s ../../alsa-kernel/include/wm8904.h                                     
ln -s ../../alsa-kernel/include/wm8955.h                                     
ln -s ../../alsa-kernel/include/wm8960.h                                     
ln -s ../../alsa-kernel/include/wm8993.h                                     
ln -s ../../alsa-kernel/include/wm9081.h                                     
ln -s ../../alsa-kernel/include/wss.h                                        
ln -s ../../alsa-kernel/include/ymfpci.h                                     
make[6]: Leaving directory `/usr/src/modules/alsa-driver/include/sound'      
make[5]: Leaving directory `/usr/src/modules/alsa-driver/include/sound'      
make[4]: Leaving directory `/usr/src/modules/alsa-driver/include'            
make[4]: Entering directory `/usr/src/modules/alsa-driver/acore'             
copying file alsa-kernel/core/info.c                                         
patching file info.c                                                         
Hunk #2 succeeded at 90 (offset 1 line).
Hunk #3 succeeded at 162 (offset 1 line).                                    
Hunk #4 succeeded at 496 (offset 13 lines).                                  
Hunk #5 succeeded at 536 (offset 13 lines).                                  
Hunk #6 succeeded at 952 (offset 13 lines).                                  
Hunk #7 succeeded at 992 (offset 13 lines).                                  
Hunk #8 succeeded at 1026 (offset 13 lines).                                 
copying file alsa-kernel/core/pcm.c                                          
patching file pcm.c                                                          
Hunk #2 succeeded at 934 (offset 5 lines).                                   
Hunk #3 succeeded at 950 (offset 5 lines).                                   
Hunk #4 succeeded at 962 (offset 5 lines).                                   
Hunk #5 succeeded at 1018 (offset 5 lines).                                  
copying file alsa-kernel/core/pcm_native.c                                   
patching file pcm_native.c                                                   
copying file alsa-kernel/core/pcm_memory.c
patching file pcm_memory.c                                                   
Hunk #2 succeeded at 452 (offset 1 line).                                    
copying file alsa-kernel/core/control.c                                      
patching file control.c                                                      
copying file alsa-kernel/core/hwdep.c                                        
patching file hwdep.c                                                        
Hunk #3 succeeded at 308 (offset 1 line).                                    
copying file alsa-kernel/core/init.c                                         
patching file init.c                                                         
copying file alsa-kernel/core/rawmidi.c                                      
patching file rawmidi.c                                                      
copying file alsa-kernel/core/sound.c                                        
patching file sound.c                                                        
Hunk #4 succeeded at 191 (offset 3 lines).                                   
Hunk #5 succeeded at 269 (offset 3 lines).
Hunk #6 succeeded at 281 (offset 3 lines).                                   
Hunk #7 succeeded at 298 (offset 3 lines).                                   
Hunk #8 succeeded at 322 (offset 3 lines).                                   
Hunk #9 succeeded at 377 (offset 3 lines).                                   
Hunk #10 succeeded at 388 (offset 3 lines).                                  
Hunk #11 succeeded at 414 (offset 3 lines).                                  
Hunk #12 succeeded at 521 (offset 3 lines).                                  
copying file alsa-kernel/core/timer.c                                        
patching file timer.c                                                        
copying file alsa-kernel/core/memalloc.c                                     
patching file memalloc.c                                                     
copying file alsa-kernel/core/misc.c                                         
patching file misc.c                                                         
Hunk #2 succeeded at 49 (offset 1 line).                                     
Hunk #3 succeeded at 150 (offset 1 line).
copying file alsa-kernel/core/hrtimer.c                                      
patching file hrtimer.c                                                      
Hunk #2 succeeded at 67 (offset 1 line).                                     
make[5]: Entering directory `/usr/src/modules/alsa-driver/acore/ioctl32'     
make[5]: Leaving directory `/usr/src/modules/alsa-driver/acore/ioctl32'      
make[5]: Entering directory `/usr/src/modules/alsa-driver/acore/oss'         
copying file alsa-kernel/core/oss/mixer_oss.c                                
patching file mixer_oss.c                                                    
copying file alsa-kernel/core/oss/pcm_oss.c                                  
patching file pcm_oss.c                                                      
make[5]: Leaving directory `/usr/src/modules/alsa-driver/acore/oss'          
make[5]: Entering directory `/usr/src/modules/alsa-driver/acore/seq'         
copying file alsa-kernel/core/seq/seq.c                                      
patching file seq.c                                                          
Hunk #2 succeeded at 59 (offset 2 lines).
copying file alsa-kernel/core/seq/seq_clientmgr.c                            
patching file seq_clientmgr.c                                                
copying file alsa-kernel/core/seq/seq_memory.c                               
patching file seq_memory.c                                                   
Hunk #3 succeeded at 250 (offset 2 lines).                                   
make[6]: Entering directory `/usr/src/modules/alsa-driver/acore/seq/oss'     
copying file alsa-kernel/core/seq/oss/seq_oss.c                              
patching file seq_oss.c                                                      
Hunk #3 succeeded at 192 (offset 3 lines).                                   
Hunk #4 succeeded at 227 (offset 4 lines).                                   
Hunk #5 succeeded at 330 (offset 4 lines).                                   
make[6]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq/oss'      
make[5]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq'          
make[4]: Leaving directory `/usr/src/modules/alsa-driver/acore'              
make[4]: Entering directory `/usr/src/modules/alsa-driver/i2c'
make[5]: Entering directory `/usr/src/modules/alsa-driver/i2c/l3'            
make[5]: Leaving directory `/usr/src/modules/alsa-driver/i2c/l3'             
make[5]: Entering directory `/usr/src/modules/alsa-driver/i2c/other'         
make[5]: Leaving directory `/usr/src/modules/alsa-driver/i2c/other'          
make[4]: Leaving directory `/usr/src/modules/alsa-driver/i2c'                
make[4]: Entering directory `/usr/src/modules/alsa-driver/drivers'           
copying file alsa-kernel/drivers/mts64.c                                     
patching file mts64.c                                                        
Hunk #2 succeeded at 835 (offset 1 line).                                    
Hunk #3 succeeded at 1094 (offset 1 line).                                   
copying file alsa-kernel/drivers/portman2x4.c                                
patching file portman2x4.c                                                   
Hunk #2 succeeded at 612 (offset 1 line).                                    
Hunk #3 succeeded at 883 (offset 1 line).                                    
make[5]: Entering directory `/usr/src/modules/alsa-driver/drivers/mpu401'
copying file alsa-kernel/drivers/mpu401/mpu401.c                             
patching file mpu401.c                                                       
make[5]: Leaving directory `/usr/src/modules/alsa-driver/drivers/mpu401'     
make[5]: Entering directory `/usr/src/modules/alsa-driver/drivers/opl3'      
copying file alsa-kernel/drivers/opl3/opl3_lib.c                             
patching file opl3_lib.c                                                     
Hunk #2 succeeded at 438 (offset 2 lines).                                   
make[5]: Leaving directory `/usr/src/modules/alsa-driver/drivers/opl3'       
make[5]: Entering directory `/usr/src/modules/alsa-driver/drivers/opl4'      
make[5]: Leaving directory `/usr/src/modules/alsa-driver/drivers/opl4'       
make[5]: Entering directory `/usr/src/modules/alsa-driver/drivers/pcsp'      
copying file alsa-kernel/drivers/pcsp/pcsp.c                                 
patching file pcsp.c                                                         
make[5]: Leaving directory `/usr/src/modules/alsa-driver/drivers/pcsp'       
make[5]: Entering directory `/usr/src/modules/alsa-driver/drivers/vx'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/drivers/vx'         
make[4]: Leaving directory `/usr/src/modules/alsa-driver/drivers'            
make[4]: Entering directory `/usr/src/modules/alsa-driver/isa'               
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/ad1816a'       
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/ad1816a'        
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/ad1848'        
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/ad1848'         
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/cs423x'        
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/cs423x'         
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/es1688'        
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/es1688'         
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/gus'           
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/gus'            
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/msnd'          
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/msnd'
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/opti9xx'       
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/opti9xx'        
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/sb'            
copying file alsa-kernel/isa/sb/sb16_csp.c                                   
patching file sb16_csp.c                                                     
Hunk #2 succeeded at 712 (offset 2 lines).                                   
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/sb'             
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/wavefront'     
copying file alsa-kernel/isa/wavefront/wavefront_fx.c                        
patching file wavefront_fx.c                                                 
Hunk #2 succeeded at 251 (offset -3 lines).                                  
copying file alsa-kernel/isa/wavefront/wavefront_synth.c                     
patching file wavefront_synth.c                                              
Hunk #2 succeeded at 1947 (offset 1 line).                                   
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/wavefront'
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/wss'           
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/wss'            
make[4]: Leaving directory `/usr/src/modules/alsa-driver/isa'                
make[4]: Entering directory `/usr/src/modules/alsa-driver/synth'             
make[5]: Entering directory `/usr/src/modules/alsa-driver/synth/emux'        
make[5]: Leaving directory `/usr/src/modules/alsa-driver/synth/emux'         
make[4]: Leaving directory `/usr/src/modules/alsa-driver/synth'              
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci'               
copying file alsa-kernel/pci/ad1889.c                                        
patching file ad1889.c                                                       
copying file alsa-kernel/pci/atiixp.c                                        
patching file atiixp.c                                                       
Hunk #2 succeeded at 1680 (offset 9 lines).                                  
Hunk #3 succeeded at 1725 (offset 9 lines).                                  
copying file alsa-kernel/pci/atiixp_modem.c
patching file atiixp_modem.c                                                 
Hunk #2 succeeded at 1313 (offset 6 lines).                                  
Hunk #3 succeeded at 1356 (offset 6 lines).                                  
copying file alsa-kernel/pci/bt87x.c                                         
patching file bt87x.c                                                        
Hunk #2 succeeded at 850 (offset 4 lines).                                   
Hunk #3 succeeded at 1004 (offset 4 lines).                                  
copying file alsa-kernel/pci/cmipci.c                                        
patching file cmipci.c                                                       
Hunk #2 succeeded at 3142 (offset -34 lines).                                
Hunk #3 succeeded at 3437 (offset -34 lines).                                
copying file alsa-kernel/pci/ens1370.c                                       
patching file ens1370.c                                                      
Hunk #2 succeeded at 2121 (offset -10 lines).                                
Hunk #3 succeeded at 2497 (offset -10 lines).
copying file alsa-kernel/pci/fm801.c                                         
patching file fm801.c                                                        
Hunk #3 succeeded at 1434 (offset 5 lines).                                  
Hunk #4 succeeded at 1624 (offset 14 lines).                                 
copying file alsa-kernel/pci/intel8x0.c                                      
patching file intel8x0.c                                                     
Hunk #3 succeeded at 715 (offset 9 lines).                                   
Hunk #4 succeeded at 725 (offset 9 lines).                                   
Hunk #5 succeeded at 3295 (offset 167 lines).                                
copying file alsa-kernel/pci/via82xx.c                                       
patching file via82xx.c                                                      
Hunk #2 succeeded at 2500 (offset 6 lines).                                  
Hunk #3 succeeded at 2510 (offset 6 lines).                                  
Hunk #4 succeeded at 2525 (offset 6 lines).                                  
Hunk #5 succeeded at 2536 (offset 6 lines).
Hunk #6 succeeded at 2547 (offset 6 lines).                                  
Hunk #7 succeeded at 2630 (offset 6 lines).                                  
copying file alsa-kernel/pci/via82xx_modem.c                                 
patching file via82xx_modem.c                                                
Hunk #2 succeeded at 1187 (offset 7 lines).                                  
Hunk #3 succeeded at 1247 (offset 7 lines).                                  
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/ac97'          
copying file alsa-kernel/pci/ac97/ac97_codec.c                               
patching file ac97_codec.c                                                   
Hunk #3 succeeded at 1928 (offset 10 lines).                                 
Hunk #4 succeeded at 1940 (offset 10 lines).                                 
Hunk #5 succeeded at 1964 (offset 10 lines).                                 
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/ac97'           
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/ali5451'       
copying file alsa-kernel/pci/ali5451/ali5451.c
patching file ali5451.c                                                      
Hunk #2 succeeded at 2148 (offset -57 lines).                                
Hunk #3 succeeded at 2318 (offset -57 lines).                                
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/ali5451'        
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/asihpi'        
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/asihpi'         
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/au88x0'        
copying file alsa-kernel/pci/au88x0/au88x0.c                                 
patching file au88x0.c                                                       
Hunk #2 succeeded at 339 (offset -2 lines).                                  
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/au88x0'         
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/aw2'           
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/aw2'            
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/ca0106'        
copying file alsa-kernel/pci/ca0106/ca0106_main.c
patching file ca0106_main.c                                                  
Hunk #3 succeeded at 1636 (offset 73 lines).                                 
Hunk #4 succeeded at 1908 (offset 83 lines).                                 
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/ca0106'         
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/cs46xx'        
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/cs46xx'         
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/cs5535audio'   
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/cs5535audio'    
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/ctxfi'         
copying file alsa-kernel/pci/ctxfi/ctatc.c                                   
patching file ctatc.c                                                        
Hunk #2 succeeded at 1238 (offset -10 lines).                                
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/ctxfi'          
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/echoaudio'     
copying file alsa-kernel/pci/echoaudio/echoaudio.c
patching file echoaudio.c                                                    
Hunk #1 succeeded at 1945 (offset 2 lines).                                  
Hunk #2 succeeded at 2017 (offset 2 lines).                                  
Hunk #3 succeeded at 2252 (offset 1 line).                                   
Hunk #4 succeeded at 2260 (offset 1 line).                                   
copying file alsa-kernel/pci/echoaudio/darla20.c                             
patching file darla20.c                                                      
copying file alsa-kernel/pci/echoaudio/darla24.c                             
patching file darla24.c                                                      
copying file alsa-kernel/pci/echoaudio/echo3g.c                              
patching file echo3g.c                                                       
copying file alsa-kernel/pci/echoaudio/gina20.c                              
patching file gina20.c                                                       
copying file alsa-kernel/pci/echoaudio/gina24.c                              
patching file gina24.c
copying file alsa-kernel/pci/echoaudio/indigo.c                              
patching file indigo.c                                                       
copying file alsa-kernel/pci/echoaudio/indigodj.c                            
patching file indigodj.c                                                     
copying file alsa-kernel/pci/echoaudio/indigoio.c                            
patching file indigoio.c                                                     
copying file alsa-kernel/pci/echoaudio/indigodjx.c                           
patching file indigodjx.c                                                    
Hunk #2 succeeded at 112 (offset 1 line).                                    
copying file alsa-kernel/pci/echoaudio/indigoiox.c                           
patching file indigoiox.c                                                    
Hunk #2 succeeded at 114 (offset 1 line).                                    
copying file alsa-kernel/pci/echoaudio/layla20.c                             
patching file layla20.c                                                      
copying file alsa-kernel/pci/echoaudio/layla24.c
patching file layla24.c                                                      
copying file alsa-kernel/pci/echoaudio/mia.c                                 
patching file mia.c                                                          
Hunk #2 succeeded at 125 (offset 1 line).                                    
copying file alsa-kernel/pci/echoaudio/mona.c                                
patching file mona.c                                                         
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/echoaudio'      
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/emu10k1'       
copying file alsa-kernel/pci/emu10k1/emu10k1_main.c                          
patching file emu10k1_main.c                                                 
Hunk #4 succeeded at 1409 (offset -1 lines).                                 
Hunk #5 succeeded at 1452 (offset -1 lines).                                 
Hunk #6 succeeded at 1767 (offset 3 lines).                                  
copying file alsa-kernel/pci/emu10k1/emu10k1x.c                              
patching file emu10k1x.c
Hunk #2 succeeded at 941 (offset 1 line).                                    
Hunk #3 succeeded at 1634 (offset 6 lines).                                  
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/emu10k1'        
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/hda'           
copying file alsa-kernel/pci/hda/hda_intel.c                                 
patching file hda_intel.c                                                    
Hunk #2 succeeded at 2360 (offset 7 lines).                                  
Hunk #3 succeeded at 2376 (offset 8 lines).                                  
Hunk #4 succeeded at 2392 (offset 8 lines).                                  
Hunk #5 succeeded at 2405 (offset 8 lines).                                  
Hunk #6 succeeded at 2526 (offset 8 lines).                                  
copying file alsa-kernel/pci/hda/hda_beep.c                                  
patching file hda_beep.c                                                     
Hunk #2 succeeded at 95 (offset 1 line).                                     
Hunk #3 succeeded at 123 with fuzz 2 (offset 1 line).
Hunk #4 succeeded at 141 (offset 1 line).                                    
Hunk #5 succeeded at 163 (offset 1 line).                                    
Hunk #6 succeeded at 282 with fuzz 2 (offset 18 lines).                      
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/hda'            
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/ice1712'       
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/ice1712'        
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/korg1212'      
copying file alsa-kernel/pci/korg1212/korg1212.c                             
patching file korg1212.c                                                     
Hunk #2 succeeded at 2344 (offset 5 lines).                                  
Hunk #3 succeeded at 2500 (offset 5 lines).                                  
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/korg1212'       
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/lx6464es'      
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/lx6464es'       
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/mixart'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/mixart'         
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/nm256'         
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/nm256'          
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/oxygen'        
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/oxygen'         
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/pcxhr'         
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/pcxhr'          
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/pdplus'        
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/pdplus'         
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/riptide'       
copying file alsa-kernel/pci/riptide/riptide.c                               
patching file riptide.c                                                      
Hunk #3 succeeded at 2221 (offset 3 lines).                                  
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/riptide'        
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/rme9652'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/rme9652'        
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/trident'       
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/trident'        
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/vx222'         
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/vx222'          
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/ymfpci'        
copying file alsa-kernel/pci/ymfpci/ymfpci_main.c                            
patching file ymfpci_main.c                                                  
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/ymfpci'         
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci'                
make[4]: Entering directory `/usr/src/modules/alsa-driver/aoa'               
make[5]: Entering directory `/usr/src/modules/alsa-driver/aoa/codecs'        
make[5]: Leaving directory `/usr/src/modules/alsa-driver/aoa/codecs'         
make[5]: Entering directory `/usr/src/modules/alsa-driver/aoa/core'          
make[5]: Leaving directory `/usr/src/modules/alsa-driver/aoa/core'
make[5]: Entering directory `/usr/src/modules/alsa-driver/aoa/fabrics'       
make[5]: Leaving directory `/usr/src/modules/alsa-driver/aoa/fabrics'        
make[5]: Entering directory `/usr/src/modules/alsa-driver/aoa/soundbus'      
make[6]: Entering directory                                                  
`/usr/src/modules/alsa-driver/aoa/soundbus/i2sbus'                           
make[6]: Leaving directory                                                   
`/usr/src/modules/alsa-driver/aoa/soundbus/i2sbus'                           
make[5]: Leaving directory `/usr/src/modules/alsa-driver/aoa/soundbus'       
make[4]: Leaving directory `/usr/src/modules/alsa-driver/aoa'                
make[4]: Entering directory `/usr/src/modules/alsa-driver/soc'               
copying file alsa-kernel/soc/soc-core.c                                      
patching file soc-core.c                                                     
Hunk #2 succeeded at 1331 (offset 90 lines).                                 
make[5]: Entering directory `/usr/src/modules/alsa-driver/soc/atmel'         
make[5]: Leaving directory `/usr/src/modules/alsa-driver/soc/atmel'
make[5]: Entering directory `/usr/src/modules/alsa-driver/soc/au1x'          
make[5]: Leaving directory `/usr/src/modules/alsa-driver/soc/au1x'           
make[5]: Entering directory `/usr/src/modules/alsa-driver/soc/blackfin'      
make[5]: Leaving directory `/usr/src/modules/alsa-driver/soc/blackfin'       
make[5]: Entering directory `/usr/src/modules/alsa-driver/soc/codecs'        
make[5]: Leaving directory `/usr/src/modules/alsa-driver/soc/codecs'         
make[5]: Entering directory `/usr/src/modules/alsa-driver/soc/davinci'       
make[5]: Leaving directory `/usr/src/modules/alsa-driver/soc/davinci'        
make[5]: Entering directory `/usr/src/modules/alsa-driver/soc/fsl'           
make[5]: Leaving directory `/usr/src/modules/alsa-driver/soc/fsl'            
make[5]: Entering directory `/usr/src/modules/alsa-driver/soc/imx'           
make[5]: Leaving directory `/usr/src/modules/alsa-driver/soc/imx'            
make[5]: Entering directory `/usr/src/modules/alsa-driver/soc/omap'          
make[5]: Leaving directory `/usr/src/modules/alsa-driver/soc/omap'           
make[5]: Entering directory `/usr/src/modules/alsa-driver/soc/pxa'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/soc/pxa'            
make[5]: Entering directory `/usr/src/modules/alsa-driver/soc/s3c24xx'       
make[5]: Leaving directory `/usr/src/modules/alsa-driver/soc/s3c24xx'        
make[5]: Entering directory `/usr/src/modules/alsa-driver/soc/s6000'         
make[5]: Leaving directory `/usr/src/modules/alsa-driver/soc/s6000'          
make[5]: Entering directory `/usr/src/modules/alsa-driver/soc/sh'            
make[5]: Leaving directory `/usr/src/modules/alsa-driver/soc/sh'             
make[5]: Entering directory `/usr/src/modules/alsa-driver/soc/txx9'          
make[5]: Leaving directory `/usr/src/modules/alsa-driver/soc/txx9'           
make[4]: Leaving directory `/usr/src/modules/alsa-driver/soc'                
make[4]: Entering directory `/usr/src/modules/alsa-driver/usb'               
copying file alsa-kernel/usb/card.c                                          
patching file card.c                                                         
copying file alsa-kernel/usb/endpoint.c                                      
patching file endpoint.c
Hunk #2 succeeded at 187 (offset 2 lines).                                   
Hunk #3 succeeded at 278 (offset 2 lines).                                   
Hunk #4 succeeded at 309 (offset 2 lines).                                   
copying file alsa-kernel/usb/helper.c                                        
patching file helper.c                                                       
Hunk #2 succeeded at 93 (offset 1 line).                                     
copying file alsa-kernel/usb/quirks.c                                        
patching file quirks.c                                                       
Hunk #2 succeeded at 161 (offset 2 lines).                                   
Hunk #3 succeeded at 236 (offset 2 lines).                                   
Hunk #4 succeeded at 325 (offset 2 lines).                                   
Hunk #5 succeeded at 343 (offset 2 lines).                                   
Hunk #6 succeeded at 357 (offset 2 lines).                                   
Hunk #7 succeeded at 370 (offset 2 lines).                                   
copying file alsa-kernel/usb/urb.c
patching file urb.c                                                          
Hunk #2 succeeded at 72 (offset 1 line).                                     
Hunk #3 succeeded at 87 (offset 1 line).                                     
Hunk #4 succeeded at 171 (offset 1 line).                                    
Hunk #5 succeeded at 198 (offset 1 line).                                    
Hunk #6 succeeded at 350 (offset 1 line).                                    
copying file alsa-kernel/usb/midi.c                                          
patching file midi.c                                                         
Hunk #6 succeeded at 1004 with fuzz 1.                                       
Hunk #7 succeeded at 1021 (offset 2 lines).                                  
Hunk #8 succeeded at 1031 (offset 2 lines).                                  
Hunk #9 succeeded at 1749 (offset 12 lines).                                 
Hunk #10 succeeded at 2120 (offset 12 lines).                                
copying file alsa-kernel/usb/mixer.c                                         
patching file mixer.c
copying file alsa-kernel/usb/mixer_quirks.c                                  
patching file mixer_quirks.c                                                 
Hunk #2 succeeded at 64 (offset 1 line).                                     
make[5]: Entering directory `/usr/src/modules/alsa-driver/usb/caiaq'         
copying file alsa-kernel/usb/caiaq/audio.c                                   
patching file audio.c                                                        
Hunk #2 succeeded at 465 (offset 1 line).                                    
Hunk #3 succeeded at 528 (offset 1 line).                                    
copying file alsa-kernel/usb/caiaq/device.c                                  
patching file device.c                                                       
Hunk #2 succeeded at 139 (offset 7 lines).                                   
Hunk #3 succeeded at 401 (offset 7 lines).                                   
copying file alsa-kernel/usb/caiaq/input.c                                   
patching file input.c                                                        
Hunk #2 succeeded at 21 with fuzz 1 (offset 1 line).
Hunk #3 succeeded at 301 (offset 1 line).                                    
Hunk #4 succeeded at 322 (offset 1 line).                                    
Hunk #5 succeeded at 364 (offset 1 line).                                    
Hunk #6 succeeded at 378 (offset 1 line).                                    
Hunk #7 succeeded at 507 (offset 1 line).                                    
make[5]: Leaving directory `/usr/src/modules/alsa-driver/usb/caiaq'          
make[5]: Entering directory `/usr/src/modules/alsa-driver/usb/misc'          
make[5]: Leaving directory `/usr/src/modules/alsa-driver/usb/misc'           
make[5]: Entering directory `/usr/src/modules/alsa-driver/usb/usx2y'         
copying file alsa-kernel/usb/usx2y/usX2Yhwdep.c                              
patching file usX2Yhwdep.c                                                   
Hunk #2 succeeded at 33 (offset 1 line).                                     
Hunk #3 succeeded at 56 (offset 1 line).                                     
Hunk #4 succeeded at 142 (offset 1 line).                                    
Hunk #5 succeeded at 181 (offset 1 line).
Hunk #6 succeeded at 237 (offset 1 line).                                    
Hunk #7 succeeded at 290 (offset 1 line).                                    
copying file alsa-kernel/usb/usx2y/usbusx2y.c                                
patching file usbusx2y.c                                                     
Hunk #2 succeeded at 174 (offset 1 line).                                    
Hunk #3 succeeded at 190 (offset 1 line).                                    
Hunk #4 succeeded at 254 (offset 1 line).                                    
Hunk #5 succeeded at 267 (offset 1 line).                                    
Hunk #6 succeeded at 313 (offset 1 line).                                    
Hunk #7 succeeded at 377 (offset 1 line).                                    
Hunk #8 succeeded at 401 (offset 1 line).                                    
Hunk #9 succeeded at 427 (offset 1 line).                                    
Hunk #10 succeeded at 448 (offset 1 line).                                   
Hunk #11 succeeded at 508 (offset 1 line).                                   
Hunk #12 succeeded at 528 (offset 1 line).
copying file alsa-kernel/usb/usx2y/usbusx2yaudio.c                           
patching file usbusx2yaudio.c                                                
Hunk #2 succeeded at 69 (offset 1 line).                                     
Hunk #3 succeeded at 317 (offset 1 line).                                    
Hunk #4 succeeded at 350 (offset 1 line).                                    
Hunk #5 succeeded at 366 (offset 1 line).                                    
Hunk #6 succeeded at 392 (offset 1 line).                                    
Hunk #7 succeeded at 408 (offset 1 line).                                    
Hunk #8 succeeded at 525 (offset 1 line).                                    
Hunk #9 succeeded at 548 (offset 1 line).                                    
Hunk #10 succeeded at 697 (offset 1 line).                                   
Hunk #11 succeeded at 1061 (offset 1 line).                                  
copying file alsa-kernel/usb/usx2y/usx2yhwdeppcm.c                           
patching file usx2yhwdeppcm.c                                                
Hunk #2 succeeded at 153 (offset 1 line).
Hunk #3 succeeded at 233 (offset 1 line).                                    
Hunk #4 succeeded at 267 (offset 1 line).                                    
Hunk #5 succeeded at 307 (offset 1 line).                                    
Hunk #6 succeeded at 328 (offset 1 line).                                    
Hunk #7 succeeded at 454 (offset 1 line).                                    
Hunk #8 succeeded at 482 (offset 1 line).                                    
Hunk #9 succeeded at 715 (offset 1 line).                                    
Hunk #10 succeeded at 728 (offset 1 line).                                   
Hunk #11 succeeded at 803 (offset 1 line).                                   
make[5]: Leaving directory `/usr/src/modules/alsa-driver/usb/usx2y'          
make[4]: Leaving directory `/usr/src/modules/alsa-driver/usb'                
make[4]: Entering directory `/usr/src/modules/alsa-driver/pcmcia'            
make[5]: Entering directory                                                  
`/usr/src/modules/alsa-driver/pcmcia/pdaudiocf'                              
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia/pdaudiocf'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pcmcia/vx'         
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia/vx'          
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia'             
make[3]: Leaving directory `/usr/src/modules/alsa-driver'                    
/usr/bin/make -C /usr/src/linux SUBDIRS=/usr/src/modules/alsa-driver         
CPP="gcc -E" CC="gcc" modules                                                
make[3]: Entering directory `/usr/src/linux-headers-2.6.35-24-generic'       
  CC [M]  /usr/src/modules/alsa-driver/acore/hwdep.o                         
In file included from /usr/src/modules/alsa-driver/include/config.h:6,       
                 from /usr/src/modules/alsa-driver/include/adriver.h:25,     
                 from /usr/src/modules/alsa-driver/acore/hwdep.c:1:          
/usr/src/modules/alsa-driver/include/config1.h:175: warning:                 
"CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined                                   
./include/generated/autoconf.h:2222: note: this is the location of the       
previous definition
In file included from /usr/src/modules/alsa-driver/include/config.h:6,       
                 from /usr/src/modules/alsa-driver/include/adriver.h:25,     
                 from /usr/src/modules/alsa-driver/acore/hwdep.c:1:          
/usr/src/modules/alsa-driver/include/config1.h:175: warning:                 
"CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined                                   
./include/generated/autoconf.h:2222: note: this is the location of the       
previous definition                                                          
  CC [M]  /usr/src/modules/alsa-driver/acore/memory_wrapper.o                
In file included from /usr/src/modules/alsa-driver/include/config.h:6,       
                 from                                                        
/usr/src/modules/alsa-driver/include/alsa-autoconf.h:4,                      
                 from                                                        
/usr/src/modules/alsa-driver/acore/memory_wrapper.c:1:                       
/usr/src/modules/alsa-driver/include/config1.h:175: warning:                 
"CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2222: note: this is the location of the       
previous definition                                                          
  CC [M]  /usr/src/modules/alsa-driver/acore/memalloc.o                      
In file included from /usr/src/modules/alsa-driver/include/config.h:6,       
                 from                                                        
/usr/src/modules/alsa-driver/include/alsa-autoconf.h:4,                      
                 from /usr/src/modules/alsa-driver/acore/memalloc.inc:1,     
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1:       
/usr/src/modules/alsa-driver/include/config1.h:175: warning:                 
"CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined                                   
./include/generated/autoconf.h:2222: note: this is the location of the       
previous definition                                                          
In file included from include/linux/pci.h:58,                                
                 from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,    
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
./include/generated/autoconf.h:2222: note: this is the location of the       
previous definition                                                          
  CC [M]  /usr/src/modules/alsa-driver/acore/memalloc.o                      
In file included from /usr/src/modules/alsa-driver/include/config.h:6,       
                 from                                                        
/usr/src/modules/alsa-driver/include/alsa-autoconf.h:4,                      
                 from /usr/src/modules/alsa-driver/acore/memalloc.inc:1,     
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1:       
/usr/src/modules/alsa-driver/include/config1.h:175: warning:                 
"CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined                                   
./include/generated/autoconf.h:2222: note: this is the location of the       
previous definition                                                          
In file included from include/linux/pci.h:58,                                
                 from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,    
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1: 
```driver compile failure log part, I think this contains all of the errors:

```
In file included from include/linux/pci.h:58,                                
                 from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,    
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1:       
/usr/src/modules/alsa-driver/include/linux/pci_ids.h:2: fatal error:         
@CONFIG_SND_KERNELSRC@/include/linux/pci_ids.h: No such file or directory    
compilation terminated.                                                      
make[5]: *** [/usr/src/modules/alsa-driver/acore/memalloc.o] Error 1         
make[4]: *** [/usr/src/modules/alsa-driver/acore] Error 2                    
make[3]: *** [_module_/usr/src/modules/alsa-driver] Error 2                  
make[3]: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic'        
make[2]: *** [compile] Error 2                                               
make[2]: Leaving directory `/usr/src/modules/alsa-driver'                    
make[1]: *** [build-stamp] Error 2                                           
make[1]: Leaving directory `/usr/src/modules/alsa-driver'                    
make: *** [kdist_image] Error 2    
```

---

### Post by lidex on 2011-01-01
You can try resetting alsa:
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

Now run the alsa-info script again please.

---

### Post by battybiologist on 2011-01-01
Alright, that worked this time (I think it has to do with the formatting? The other two times I tried that, I didn't use copy+paste), thanks! 
edit: fixed the other bits by looking at [http://ubuntuforums.org/showthread.php?t=1489185&page=4](http://ubuntuforums.org/showthread.php?t=1489185&page=4)

[http://www.alsa-project.org/db/?f=8a59842541e8065ce743282196a6f29e79ba8385](http://www.alsa-project.org/db/?f=8a59842541e8065ce743282196a6f29e79ba8385)

```
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Sat Jan  1 11:02:24 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      LENOVO
Product Name:      3508CTO


!!Kernel Information
!!------------------

Kernel release:    2.6.35-24-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------

snd_hda_intel
thinkpad_acpi


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xd0600000 irq 16
29 [ThinkPadEC     ]: ThinkPad EC - ThinkPad Console Audio Control
                      ThinkPad Console Audio Control at EC reg 0x30, fw 6XHT40WW-1.180000


!!PCI Soundcards installed in the system
!!--------------------------------------

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:14.2 0403: 1002:4383
    Subsystem: 17aa:21b2


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
    bdl_pos_adj : 32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    single_cmd : N

!!Module: thinkpad_acpi
    brightness_enable : 2
    brightness_mode : 4
    dbg_bluetoothemul : 0
    dbg_uwbemul : 0
    dbg_wlswemul : 0
    dbg_wwanemul : 0
    enable : Y
    experimental : 0
    fan_control : N
    force_load : N
    hotkey_report_mode : 0
    id : ThinkPadEC
    index : -536870912
    volume_capabilities : 0
    volume_control : N
    volume_mode : 3


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Conexant CX20582 (Pebble)
Address: 0
Function Id: 0x1
Vendor Id: 0x14f15066
Subsystem Id: 0x17aa21b2
Revision Id: 0x100302
No Modem Function Group found
Default PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=4, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x10 [Audio Output] wcaps 0xc1d: Stereo Amp-Out R/L
  Control: name="Master Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="CONEXANT Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-Out vals:  [0x25 0x25]
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x11 [Audio Output] wcaps 0xc1d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-Out vals:  [0x3c 0x3c]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x12 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x13 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x07, nsteps=0x07, stepsize=0x0f, mute=0
  Amp-Out vals:  [0x00]
Node 0x14 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Device: name="CONEXANT Analog", type="Audio", device=0
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x4f 0x4f] [0x80 0x80] [0x4f 0x4f] [0x80 0x80]
  Converter: stream=1, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x17 0x18 0x23* 0x24
Node 0x15 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x17* 0x18 0x23 0x24
Node 0x16 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x17* 0x18 0x23 0x24
Node 0x17 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x02 0x02]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x1a 0x1b* 0x1d 0x1e
Node 0x18 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x1a* 0x1b 0x1d 0x1e
Node 0x19 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x032110f0: [Jack] HP Out at Ext Left
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=37, enabled=1
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1a [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00001324: IN Detect
    Vref caps: HIZ 50 80
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x1b [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00011334: IN OUT EAPD Detect
    Vref caps: HIZ 50 80
  EAPD 0x2: EAPD
  Pin Default 0x03a110f0: [Jack] Mic at Ext Left
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00: VREF_HIZ
  Unsolicited: tag=38, enabled=1
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1c [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1d [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00010034: IN OUT EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1e [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x1f [Pin Complex] wcaps 0x400501: Stereo
  Pincap 0x00000010: OUT
  Pin Default 0x921701f0: [Fixed] Speaker at Int Front
    Conn = Analog, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x20 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 1
     0x12
Node 0x21 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x22 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 1
     0x21
Node 0x23 [Pin Complex] wcaps 0x40040b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x04, stepsize=0x2f, mute=0
  Amp-In vals:  [0x02 0x02]
  Pincap 0x00000020: IN
  Pin Default 0x95a601f0: [Fixed] Mic at Int Top
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x24 [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
  Amp-In caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10 0x11
Node 0x25 [Vendor Defined Widget] wcaps 0xf00000: Mono
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116, 8 Jan  1 02:52 /dev/snd/controlC0
crw-rw----  1 root audio 116, 4 Jan  1 02:52 /dev/snd/controlC29
crw-rw----  1 root audio 116, 7 Jan  1 02:52 /dev/snd/hwC0D0
crw-rw----  1 root audio 116, 6 Jan  1 02:53 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116, 5 Jan  1 02:57 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116, 3 Jan  1 02:52 /dev/snd/seq
crw-rw----  1 root audio 116, 2 Jan  1 02:52 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Jan  1 02:52 .
drwxr-xr-x 3 root root 200 Jan  1 02:52 ..
lrwxrwxrwx 1 root root  12 Jan  1 02:52 pci-0000:00:14.2 -> ../controlC0
lrwxrwxrwx 1 root root  13 Jan  1 02:52 platform-thinkpad_acpi -> ../controlC29


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [SB]

Card hw:0 'SB'/'HDA ATI SB at 0xd0600000 irq 16'
  Mixer name    : 'Conexant CX20582 (Pebble)'
  Components    : 'HDA:14f15066,17aa21b2,00100302'
  Controls      : 6
  Simple ctrls  : 4
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 37 [50%] [-37.00dB] [on]
  Front Right: Playback 37 [50%] [-37.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 79 [99%] [5.00dB] [on]
  Front Right: Capture 79 [99%] [5.00dB] [on]
Simple mixer control 'Analog Mic Boost',0
  Capabilities: cenum
  Items: '0dB' '10dB' '20dB' '30dB' '40dB'
  Item0: '20dB'

!!-------Mixer controls for card 29 [ThinkPadEC]

Card hw:29 'ThinkPadEC'/'ThinkPad Console Audio Control at EC reg 0x30, fw 6XHT40WW-1.180000'
  Mixer name    : 'ThinkPad EC 6XHT40WW-1.180000'
  Components    : ''
  Controls      : 1
  Simple ctrls  : 1
Simple mixer control 'Console',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!-------------

--startcollapse--
state.SB {
    control.1 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 74'
        comment.dbmin -7400
        comment.dbmax 0
        iface MIXER
        name 'Master Playback Volume'
        value.0 37
        value.1 37
    }
    control.2 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Master Playback Switch'
        value true
    }
    control.3 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 '0dB'
        comment.item.1 '10dB'
        comment.item.2 '20dB'
        comment.item.3 '30dB'
        comment.item.4 '40dB'
        iface MIXER
        name 'Analog Mic Boost Capture Enum'
        value '20dB'
    }
    control.4 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 80'
        comment.dbmin -7400
        comment.dbmax 600
        iface MIXER
        name 'Capture Volume'
        value.0 79
        value.1 79
    }
    control.5 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Capture Switch'
        value.0 true
        value.1 true
    }
    control.6 {
        comment.access 'read write user'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        comment.tlv '0000000100000008ffffec1400000014'
        comment.dbmin -5100
        comment.dbmax 0
        iface MIXER
        name 'PCM Playback Volume'
        value.0 255
        value.1 255
    }
}
state.ThinkPadEC {
    control.1 {
        comment.access read
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Console Playback Switch'
        value true
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
aes_i586
aes_generic
binfmt_misc
parport_pc
ppdev
dm_crypt
snd_hda_codec_conexant
snd_hda_intel
snd_hda_codec
snd_hwdep
thinkpad_acpi
snd_pcm
snd_seq_midi
snd_rawmidi
joydev
snd_seq_midi_event
fglrx
snd_seq
snd_timer
snd_seq_device
snd
uvcvideo
videodev
v4l1_compat
psmouse
r8192se_pci
led_class
agpgart
nvram
soundcore
serio_raw
shpchp
lp
k8temp
i2c_piix4
parport
snd_page_alloc
cfg80211
usbhid
hid
usb_storage
ahci
video
output
r8169
libahci
mii


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x19 0x032110f0
0x1a 0x400001f0
0x1b 0x03a110f0
0x1c 0x400001f0
0x1d 0x400001f0
0x1e 0x400001f0
0x1f 0x921701f0
0x20 0x400001f0
0x22 0x400001f0
0x23 0x95a601f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   11.096554] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input9
[   11.802548] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.931750] psmouse serio5: ID: 10 00 64
--
[  581.232173] =====>rtl8192_set_chan()====ch:8
[  581.292013] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x001f000a
[  581.344031] =====>rtl8192_set_chan()====ch:9
--
[  581.792038] =====>rtl8192_set_chan()====ch:13
[  582.296029] hda_intel: azx_get_response timeout, switching to single_cmd mode: last cmd=0x001f000a


```

---

### Post by lidex on 2011-01-01
Nice work. Question - is this with default 1.0.23 or did you install linuxant?

---

### Post by battybiologist on 2011-01-02
This is with default 1.0.23; I tried installing linuxant, but the package failed, and I reinstalled baseline alsa a few times before I managed to purge it right.

---

