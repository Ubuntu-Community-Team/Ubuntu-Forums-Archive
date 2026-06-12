---
title: "Can't install my audio driver"
date: 2009-12-21
forum: Multimedia Software
---

### Post by PHaLaNX on 2009-12-21
Hi,

I had a problem with not being able to record or play with different applications simultaneously, I had my Realtek ALC888 driver installed but on every startup kde would tell me that this driver failed running, and it was falling back to pulseaudio. 

Now I removed pulseaudio and trying to install the driver I downloaded from the Realtek's site, (I don't have sound right now, obviously) but it's trying to run alsaconf and I just can't find it anywhere. It should be in alsa-utils but it's not. 

So with a hope of at least getting sound back I installed pulseaudio again but it doesn't work, it outputs to a "dummy device" instead of my soundcard. 

Now I need to find alsaconf to install this driver. 

Any ideas would be appreciated.

Thanks in advance...

---

### Post by PHaLaNX on 2009-12-21
I found the alsaconf, installed it but it doesn't work (what a surprise!). 

It says:
```
No supported PnP or PCI card found.
```

I'm not even sure if it installed the driver or not. 

Need help, thanks.

---

### Post by Yellow Pasque on 2009-12-21
First, see if you have a driver/kermel module loaded. Post output of:
```
sudo lshw -C multimedia
aplay -l
```

---

### Post by PHaLaNX on 2009-12-21
```
$ sudo lshw -C multimedia

  *-multimedia UNCLAIMED
       description: Audio device
       product: HD48x0 audio
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0
       resources: memory:f5010000-f5013fff
  *-multimedia UNCLAIMED
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f8200000-f8203fff

```

```
$ aplay -l

aplay: device_list:204: no soundcards found...

```

---

### Post by PHaLaNX on 2009-12-21
Here is the install log:

```
$ sudo ./install                                                      
[sudo] password for XXX:                                                                                                    
.....Decompress Driver source v1.0.11-4.06a                                                                                     
^[[D^[[D^[[D^[[D^[[D^[[D.....Decompress ALSA Library source v1.0.9                                                              
.....Decompress ALSA Utility v1.09a                                                                                             
Remove old sound driver                                                                                                         
Compile Driver........                                                                                                          
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
checking for current directory... /home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a                 
checking cross compile...                                                                                                       
checking for directory with kernel source... /lib/modules/2.6.31-14-generic/build                                               
checking for directory with kernel build...                                                                                     
checking for kernel linux/version.h... yes                                                                                      
checking for kernel linux/autoconf.h... yes                                                                                     
checking for kernel version... 2.6.31-14-generic                                                                                
checking for GCC version... ./configure: eval: line 4855: syntax error near unexpected token `)'                                
./configure: eval: line 4855: `my_compiler_version=4.4.1-4ubuntu8)'                                                             
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
Removing a dummy media/v4l2-dev.h.             
checking for kernel linux/devfs_fs_kernel.h... no
Creating a dummy <linux/devfs_fs_kernel.h>...    
checking for kernel linux/highmem.h... yes       
checking for kernel linux/workqueue.h... yes     
checking for kernel linux/dma-mapping.h... yes   
checking for kernel asm/hw_irq.h... no           
Creating a dummy <asm/hw_irq.h>...               
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
checking for kernel linux/latency.h... no         
Creating <linux/latency.h>...                     
checking for kernel asm/irq_regs.h... no          
Creating a dummy <asm/irq_regs.h>...              
checking for kernel module symbol versions... yes 
checking for PCI support in kernel... yes         
checking for I2C driver in kernel... yes          
checking for I2C_POWERMAC in kernel... unknown    
checking for firmware loader... yes               
checking for input subsystem in kernel... yes     
checking for directory to store kernel modules... /lib/modules/2.6.31-14-generic/kernel/sound
checking for verbose procfs... on                                                            
checking for verbose printk... on                                                            
checking for debug level... none                                                             
checking for ISA support in kernel... yes                                                    
checking for processor type... i586                                                          
checking for ISA DMA API... yes                                                              
checking for SMP... yes                                                                      
checking for Video device support in kernel... yes                                           
checking for ISA PnP driver in kernel... yes                                                 
checking for PnP driver in kernel... yes                                                     
checking for Kernel ISA-PnP support... yes                                                   
checking for strlcpy... no                                                                   
checking for snprintf... no                                                                  
checking for vsnprintf... no                                                                 
checking for scnprintf... no                                                                 
checking for sscanf... no                                                                    
checking for vmalloc_to_page... no                                                           
checking for old kmod... yes                                                                 
checking for PDE... no                                                                       
checking for pci_set_consistent_dma_mask... no                                               
checking for pci_dev_present... no                                                           
checking for msleep... no                                                                    
checking for msecs_to_jiffies... no                                                          
checking for tty->count is the atomic type... no                                             
checking for video_get_drvdata... no                                                         
checking for V4L1 layer... yes                                                               
checking for io_remap_pfn_range... no                                                        
checking for new io_remap_page_range... no                                                   
checking for kcalloc... no                                                                   
checking for kstrdup... no                                                                   
checking for kzalloc... no                                                                   
checking for create_workqueue with flags... no                                               
checking for saved_config_space in pci_dev... no                                             
checking for register_sound_special_device... no                                             
checking for driver version... 1.0.14                                                        
checking for sequencer support... yes                                                        
checking for OSS/Free emulation... yes                                                       
checking for OSS PCM plugin system inclusion... yes                                          
checking for RTC callback support in kernel... no                                            
checking for HPET support... yes                                                             
checking for dynamic minor numbers... no                                                     
checking for support of old API... yes                                                       
checking for Procfs support... yes                                                           
checking for USB support... yes                                                              
checking for class_simple... no                                                              
checking for old driver suspend/resume callbacks... no                                       
checking for removal of page-reservation for nopage/mmap... no                               
checking for nested class_device... no                                                       
checking for new IRQ handler... no                                                           
checking for gfp_t... no                                                                     
checking for PnP suspend/resume... no                                                        
checking for new unlocked/compat_ioctl... no                                                 
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
Hacking autoconf.h...                                                                        
make dep                                                                                     
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a'
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore'
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore/ioctl32'
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore/ioctl32' 
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore/oss'    
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore/oss'     
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore/seq'    
make[4]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore/seq/instr'
make[4]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore/seq/instr' 
make[4]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore/seq/oss'  
make[4]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore/seq/oss'   
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore/seq'       
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore'           
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/i2c'            
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/i2c'             
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/drivers'        
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/drivers/mpu401' 
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/drivers/mpu401'  
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/drivers/opl3'   
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/drivers/opl3'    
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/drivers/opl4'   
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/drivers/opl4'    
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/drivers/pcsp'   
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/drivers/pcsp'    
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/drivers/vx'     
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/drivers/vx'      
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/drivers'         
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/isa'            
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/isa'             
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/synth'          
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/synth/emux'     
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/synth/emux'      
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/synth'           
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci'            
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/ac97'       
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/ac97'        
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/ali5451'    
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/ali5451'     
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/asihpi'     
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/asihpi'      
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/au88x0'     
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/au88x0'      
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/ca0106'     
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/ca0106'      
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/cs46xx'     
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/cs46xx'      
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/cs5535audio'
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/cs5535audio' 
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/echoaudio'  
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/echoaudio'   
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/emu10k1'    
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/emu10k1'     
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/hda'        
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/hda'         
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/ice1712'    
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/ice1712'     
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/korg1212'   
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/korg1212'    
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/mixart'     
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/mixart'      
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/nm256'      
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/nm256'       
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/pcxhr'      
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/pcxhr'       
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/pdplus'     
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/pdplus'      
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/riptide'    
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/riptide'     
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/rme9652'    
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/rme9652'     
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/trident'    
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/trident'     
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/vx222'      
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/vx222'       
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/ymfpci'     
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/ymfpci'      
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci'             
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/aoa'            
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/aoa/codecs'     
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/aoa/codecs'      
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/aoa/core'       
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/aoa/core'        
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/aoa/fabrics'    
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/aoa/fabrics'     
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/aoa/soundbus'   
make[4]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/aoa/soundbus/i2sbus'
make[4]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/aoa/soundbus/i2sbus' 
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/aoa/soundbus'        
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/aoa'                 
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/soc'                
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/soc/at91'           
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/soc/at91'            
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/soc/codecs'         
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/soc/codecs'          
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/soc/pxa'            
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/soc/pxa'             
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/soc/s3c24xx'        
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/soc/s3c24xx'         
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/soc/sh'             
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/soc/sh'              
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/soc'                 
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/usb'                
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/usb'                 
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pcmcia'             
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pcmcia'              
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/misc'               
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/misc'                
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a'                     
make -C /lib/modules/2.6.31-14-generic/build SUBDIRS=/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a  CPP="gcc -E" CC="gcc" modules                                                                                               
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'                                                          
scripts/Makefile.build:49: *** CFLAGS was changed in "/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.                                                                         
make[2]: *** [/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore] Error 2                      
make[1]: *** [_module_/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a] Error 2                    
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'                                                           
make: *** [compile] Error 2                                                                                                     
if [ -L /usr/include/sound ]; then \                                                                                            
                rm -f /usr/include/sound; \                                                                                     
                ln -sf /home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/include/sound /usr/include/sound; \                                                                                                                        
        else \                                                                                                                  
                rm -rf /usr/include/sound; \                                                                                    
                install -d -m 755 -g root -o root /usr/include/sound; \                                                         
                for f in include/sound/*.h; do \                                                                                
                        install -m 644 -g root -o root $f /usr/include/sound; \                                                 
                done \                                                                                                          
        fi                                                                                                                      
find /lib/modules/2.6.31-14-generic/kernel/sound -name 'snd*.*o' | xargs rm -f                                                  
find /lib/modules/2.6.31-14-generic/kernel/sound -name 'ac97_bus.*o' | xargs rm -f                                              
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore'               
mkdir -p /lib/modules/2.6.31-14-generic/kernel/sound/acore                                                                      
cp snd-hwdep.ko snd-page-alloc.ko snd-pcm.ko snd-rawmidi.ko snd-timer.ko snd.ko /lib/modules/2.6.31-14-generic/kernel/sound/acore                                                                                                                               
cp: cannot stat `snd-hwdep.ko': No such file or directory                                                                       
cp: cannot stat `snd-page-alloc.ko': No such file or directory                                                                  
cp: cannot stat `snd-pcm.ko': No such file or directory                                                                         
cp: cannot stat `snd-rawmidi.ko': No such file or directory                                                                     
cp: cannot stat `snd-timer.ko': No such file or directory                                                                       
cp: cannot stat `snd.ko': No such file or directory                                                                             
make[1]: *** [modules_install] Error 1                                                                                          
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore'                
make: *** [install-modules] Error 1                                                                                             
Creating mixer?...done.                                                                                                         
Creating sequencer...done.                                                                                                      
Creating midi0?...done.                                                                                                         
Creating dsp?...done.                                                                                                           
Creating audio?...done.                                                                                                         
Creating sndstat...done.                                                                                                        
Creating music...done.                                                                                                          
Creating dmmidi?...done.                                                                                                        
Creating dmfm?...done.                                                                                                          
Creating amixer?...done.                                                                                                        
Creating adsp?...done.                                                                                                          
Creating amidi?...done.                                                                                                         
Creating admmidi?...done.                                                                                                       
Creating snd/control?...done.                                                                                                   
Creating snd/seq...done.                                                                                                        
Creating snd/timer...done.                                                                                                      
Creating snd/hw??...done.                                                                                                       
Creating snd/midi??...done.                                                                                                     
Creating snd/pcm??p...done.                                                                                                     
Creating snd/pcm??c...done.                                                                                                     
Creating aload?...done.                                                                                                         
Creating aloadSEQ...done.                                                                                                       
Remove old alsa library                                                                                                         
Compile ALSA Library.....                                                                                                       
checking build system type... i686-pc-linux-gnu                                                                                 
checking host system type... i686-pc-linux-gnu                                                                                  
checking target system type... i686-pc-linux-gnu                                                                                
checking for a BSD-compatible install... /usr/bin/install -c                                                                    
checking whether build environment is sane... yes                                                                               
checking for gawk... no                                                                                                         
checking for mawk... mawk                                                                                                       
checking whether make sets $(MAKE)... yes                                                                                       
checking for gcc... gcc                                                                                                         
checking for C compiler default output file name... a.out                                                                       
checking whether the C compiler works... yes                                                                                    
checking whether we are cross compiling... no                                                                                   
checking for suffix of executables...                                                                                           
checking for suffix of object files... o                                                                                        
checking whether we are using the GNU C compiler... yes                                                                         
checking whether gcc accepts -g... yes                                                                                          
checking for gcc option to accept ISO C89... none needed                                                                        
checking for style of include used by make... GNU                                                                               
checking dependency style of gcc... gcc3                                                                                        
checking how to run the C preprocessor... gcc -E                                                                                
checking for a BSD-compatible install... /usr/bin/install -c                                                                    
checking whether ln -s works... yes                                                                                             
checking for a sed that does not truncate output... /bin/sed                                                                    
checking for grep that handles long lines and -e... /bin/grep                                                                   
checking for egrep... /bin/grep -E                                                                                              
checking for ld used by gcc... /usr/bin/ld                                                                                      
checking if the linker (/usr/bin/ld) is GNU ld... yes                                                                           
checking for /usr/bin/ld option to reload object files... -r                                                                    
checking for BSD-compatible nm... /usr/bin/nm -B                                                                                
checking how to recognise dependent libraries... pass_all                                                                       
checking for ANSI C header files... yes                                                                                         
checking for sys/types.h... yes                                                                                                 
checking for sys/stat.h... yes                                                                                                  
checking for stdlib.h... yes                                                                                                    
checking for string.h... yes                                                                                                    
checking for memory.h... yes                                                                                                    
checking for strings.h... yes                                                                                                   
checking for inttypes.h... yes                                                                                                  
checking for stdint.h... yes                                                                                                    
checking for unistd.h... yes                                                                                                    
checking dlfcn.h usability... yes                                                                                               
checking dlfcn.h presence... yes                                                                                                
checking for dlfcn.h... yes                                                                                                     
checking for g++... g++                                                                                                         
checking whether we are using the GNU C++ compiler... yes                                                                       
checking whether g++ accepts -g... yes                                                                                          
checking dependency style of g++... gcc3                                                                                        
checking how to run the C++ preprocessor... g++ -E                                                                              
checking for g77... no                                                                                                          
checking for f77... no                                                                                                          
checking for xlf... no                                                                                                          
checking for frt... no                                                                                                          
checking for pgf77... no                                                                                                        
checking for cf77... no                                                                                                         
checking for fort77... no                                                                                                       
checking for fl32... no                                                                                                         
checking for af77... no                                                                                                         
checking for f90... no                                                                                                          
checking for xlf90... no                                                                                                        
checking for pgf90... no                                                                                                        
checking for pghpf... no                                                                                                        
checking for epcf90... no                                                                                                       
checking for gfortran... no                                                                                                     
checking for g95... no                                                                                                          
checking for f95... no                                                                                                          
checking for fort... no                                                                                                         
checking for xlf95... no                                                                                                        
checking for ifort... no                                                                                                        
checking for ifc... no                                                                                                          
checking for efc... no                                                                                                          
checking for pgf95... no                                                                                                        
checking for lf95... no                                                                                                         
checking for ftn... no                                                                                                          
checking whether we are using the GNU Fortran 77 compiler... no                                                                 
checking whether  accepts -g... no                                                                                              
checking the maximum length of command line arguments... 32768                                                                  
checking command to parse /usr/bin/nm -B output from gcc object... ok                                                           
checking for objdir... .libs                                                                                                    
checking for ar... ar                                                                                                           
checking for ranlib... ranlib                                                                                                   
checking for strip... strip                                                                                                     
checking if gcc supports -fno-rtti -fno-exceptions... no                                                                        
checking for gcc option to produce PIC... -fPIC                                                                                 
checking if gcc PIC flag -fPIC works... yes                                                                                     
checking if gcc static flag -static works... yes                                                                                
checking if gcc supports -c -o file.o... yes                                                                                    
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes                                                  
checking whether -lc should be explicitly linked in... no                                                                       
checking dynamic linker characteristics... GNU/Linux ld.so                                                                      
checking how to hardcode library paths into programs... immediate                                                               
checking whether stripping libraries is possible... yes                                                                         
checking for shl_load... no                                                                                                     
checking for shl_load in -ldld... no                                                                                            
checking for dlopen... no                                                                                                       
checking for dlopen in -ldl... yes                                                                                              
checking whether a program can dlopen itself... yes                                                                             
checking whether a statically linked program can dlopen itself... no                                                            
checking if libtool supports shared libraries... yes                                                                            
checking whether to build shared libraries... yes                                                                               
checking whether to build static libraries... no                                                                                
configure: creating libtool                                                                                                     
appending configuration tag "CXX" to libtool                                                                                    
checking for ld used by g++... /usr/bin/ld                                                                                      
checking if the linker (/usr/bin/ld) is GNU ld... yes                                                                           
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes                                                  
checking for g++ option to produce PIC... -fPIC                                                                                 
checking if g++ PIC flag -fPIC works... yes                                                                                     
checking if g++ static flag -static works... yes                                                                                
checking if g++ supports -c -o file.o... yes                                                                                    
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes                                                  
checking dynamic linker characteristics... GNU/Linux ld.so                                                                      
checking how to hardcode library paths into programs... immediate                                                               
appending configuration tag "F77" to libtool                                                                                    
checking for ANSI C header files... (cached) yes                                                                                
checking for an ANSI C-conforming const... yes                                                                                  
checking for inline... inline                                                                                                   
checking whether time.h and sys/time.h may both be included... yes                                                              
checking whether gcc needs -traditional... no                                                                                   
checking for hsearch_r... yes                                                                                                   
checking for library version... major 1 minor 0 subminor 14 extrastr  extraver 1000000                                          
checking for versioned symbols... yes                                                                                           
checking for symbolic-functions... no                                                                                           
checking for custom symbol prefixes...                                                                                          
checking for debug... yes                                                                                                       
checking for tmpdir... /tmp                                                                                                     
checking for softfloat... no                                                                                                    
checking for libdl... checking for dlsym in -ldl... yes                                                                         
checking for pthread... checking for pthread_join in -lpthread... yes                                                           
checking for architecture... x86                                                                                                
checking wordexp.h usability... yes                                                                                             
checking wordexp.h presence... yes                                                                                              
checking for wordexp.h... yes                                                                                                   
checking for resmgr support... no                                                                                               
checking for aload* support... yes                                                                                              
checking for ALSA device file directory... /dev/snd/                                                                            
checking for aload* device file directory... /dev/                                                                              
configure: creating ./config.status                                                                                             
config.status: creating Makefile                                                                                                
config.status: creating doc/Makefile                                                                                            
config.status: creating doc/pictures/Makefile                                                                                   
config.status: creating include/Makefile                                                                                        
config.status: creating include/sound/Makefile                                                                                  
config.status: creating src/Versions                                                                                            
config.status: creating src/Makefile                                                                                            
config.status: creating src/control/Makefile                                                                                    
config.status: creating src/mixer/Makefile                                                                                      
config.status: creating src/pcm/Makefile                                                                                        
config.status: creating src/pcm/scopes/Makefile                                                                                 
config.status: creating src/rawmidi/Makefile                                                                                    
config.status: creating src/timer/Makefile                                                                                      
config.status: creating src/hwdep/Makefile                                                                                      
config.status: creating src/seq/Makefile                                                                                        
config.status: creating src/instr/Makefile                                                                                      
config.status: creating src/compat/Makefile                                                                                     
config.status: creating src/alisp/Makefile                                                                                      
config.status: creating src/conf/Makefile                                                                                       
config.status: creating src/conf/cards/Makefile                                                                                 
config.status: creating src/conf/pcm/Makefile                                                                                   
config.status: creating modules/Makefile                                                                                        
config.status: creating modules/mixer/Makefile                                                                                  
config.status: creating modules/mixer/simple/Makefile                                                                           
config.status: creating alsalisp/Makefile                                                                                       
config.status: creating aserver/Makefile                                                                                        
config.status: creating test/Makefile                                                                                           
config.status: creating utils/Makefile                                                                                          
config.status: creating utils/alsa-lib.spec                                                                                     
config.status: creating utils/alsa.pc                                                                                           
config.status: creating include/config.h                                                                                        
config.status: executing depfiles commands                                                                                      
Making all in doc                                                                                                               
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/doc'                          
Making all in pictures                                                                                                          
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/doc/pictures'                 
make[2]: Nothing to be done for `all'.                                                                                          
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/doc/pictures'                  
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/doc'                          
make[2]: Nothing to be done for `all-am'.                                                                                       
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/doc'                           
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/doc'                           
Making all in include                                                                                                           
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/include'                      
make  all-recursive                                                                                                             
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/include'                      
Making all in sound                                                                                                             
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/include/sound'                
make[3]: Nothing to be done for `all'.                                                                                          
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/include/sound'                 
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/include'                      
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/include'                       
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/include'                       
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/include'                       
Making all in src                                                                                                               
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src'                          
Making all in control                                                                                                           
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/control'                  
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT cards.lo -MD -MP -MF ".deps/cards.Tpo" -c -o cards.lo cards.c; \                                                                     
        then mv -f ".deps/cards.Tpo" ".deps/cards.Plo"; else rm -f ".deps/cards.Tpo"; exit 1; fi                                
mkdir .libs                                                                                                                     
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT cards.lo -MD -MP -MF .deps/cards.Tpo -c cards.c  -fPIC -DPIC -o .libs/cards.o                                                                                                           
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT namehint.lo -MD -MP -MF ".deps/namehint.Tpo" -c -o namehint.lo namehint.c; \                                                         
        then mv -f ".deps/namehint.Tpo" ".deps/namehint.Plo"; else rm -f ".deps/namehint.Tpo"; exit 1; fi                       
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT namehint.lo -MD -MP -MF .deps/namehint.Tpo -c namehint.c  -fPIC -DPIC -o .libs/namehint.o                                                                                               
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT hcontrol.lo -MD -MP -MF ".deps/hcontrol.Tpo" -c -o hcontrol.lo hcontrol.c; \                                                         
        then mv -f ".deps/hcontrol.Tpo" ".deps/hcontrol.Plo"; else rm -f ".deps/hcontrol.Tpo"; exit 1; fi                       
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT hcontrol.lo -MD -MP -MF .deps/hcontrol.Tpo -c hcontrol.c  -fPIC -DPIC -o .libs/hcontrol.o                                                                                               
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT control.lo -MD -MP -MF ".deps/control.Tpo" -c -o control.lo control.c; \                                                             
        then mv -f ".deps/control.Tpo" ".deps/control.Plo"; else rm -f ".deps/control.Tpo"; exit 1; fi                          
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT control.lo -MD -MP -MF .deps/control.Tpo -c control.c  -fPIC -DPIC -o .libs/control.o                                                                                                   
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT control_hw.lo -MD -MP -MF ".deps/control_hw.Tpo" -c -o control_hw.lo control_hw.c; \                                                 
        then mv -f ".deps/control_hw.Tpo" ".deps/control_hw.Plo"; else rm -f ".deps/control_hw.Tpo"; exit 1; fi                 
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT control_hw.lo -MD -MP -MF .deps/control_hw.Tpo -c control_hw.c  -fPIC -DPIC -o .libs/control_hw.o                                                                                       
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT setup.lo -MD -MP -MF ".deps/setup.Tpo" -c -o setup.lo setup.c; \                                                                     
        then mv -f ".deps/setup.Tpo" ".deps/setup.Plo"; else rm -f ".deps/setup.Tpo"; exit 1; fi                                
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT setup.lo -MD -MP -MF .deps/setup.Tpo -c setup.c  -fPIC -DPIC -o .libs/setup.o                                                                                                           
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT control_symbols.lo -MD -MP -MF ".deps/control_symbols.Tpo" -c -o control_symbols.lo control_symbols.c; \                             
        then mv -f ".deps/control_symbols.Tpo" ".deps/control_symbols.Plo"; else rm -f ".deps/control_symbols.Tpo"; exit 1; fi  
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT control_symbols.lo -MD -MP -MF .deps/control_symbols.Tpo -c control_symbols.c  -fPIC -DPIC -o .libs/control_symbols.o                                                                   
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT control_shm.lo -MD -MP -MF ".deps/control_shm.Tpo" -c -o control_shm.lo control_shm.c; \                                             
        then mv -f ".deps/control_shm.Tpo" ".deps/control_shm.Plo"; else rm -f ".deps/control_shm.Tpo"; exit 1; fi              
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT control_shm.lo -MD -MP -MF .deps/control_shm.Tpo -c control_shm.c  -fPIC -DPIC -o .libs/control_shm.o                                                                                   
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT control_ext.lo -MD -MP -MF ".deps/control_ext.Tpo" -c -o control_ext.lo control_ext.c; \                                             
        then mv -f ".deps/control_ext.Tpo" ".deps/control_ext.Plo"; else rm -f ".deps/control_ext.Tpo"; exit 1; fi              
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT control_ext.lo -MD -MP -MF .deps/control_ext.Tpo -c control_ext.c  -fPIC -DPIC -o .libs/control_ext.o                                                                                   
/bin/sh ../../libtool --tag=CC --mode=link gcc  -g -O2   -o libcontrol.la   cards.lo namehint.lo hcontrol.lo control.lo control_hw.lo setup.lo control_symbols.lo control_shm.lo control_ext.lo                                                                 
ar cru .libs/libcontrol.a .libs/cards.o .libs/namehint.o .libs/hcontrol.o .libs/control.o .libs/control_hw.o .libs/setup.o .libs/control_symbols.o .libs/control_shm.o .libs/control_ext.o                                                                      
ranlib .libs/libcontrol.a                                                                                                       
creating libcontrol.la                                                                                                          
(cd .libs && rm -f libcontrol.la && ln -s ../libcontrol.la libcontrol.la)                                                       
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/control'                   
Making all in mixer                                                                                                             
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/mixer'                    
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT bag.lo -MD -MP -MF ".deps/bag.Tpo" -c -o bag.lo bag.c; \                                                                             
        then mv -f ".deps/bag.Tpo" ".deps/bag.Plo"; else rm -f ".deps/bag.Tpo"; exit 1; fi                                      
mkdir .libs                                                                                                                     
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT bag.lo -MD -MP -MF .deps/bag.Tpo -c bag.c  -fPIC -DPIC -o .libs/bag.o                                                                                                                   
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT mixer.lo -MD -MP -MF ".deps/mixer.Tpo" -c -o mixer.lo mixer.c; \                                                                     
        then mv -f ".deps/mixer.Tpo" ".deps/mixer.Plo"; else rm -f ".deps/mixer.Tpo"; exit 1; fi                                
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT mixer.lo -MD -MP -MF .deps/mixer.Tpo -c mixer.c  -fPIC -DPIC -o .libs/mixer.o                                                                                                           
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT simple.lo -MD -MP -MF ".deps/simple.Tpo" -c -o simple.lo simple.c; \                                                                 
        then mv -f ".deps/simple.Tpo" ".deps/simple.Plo"; else rm -f ".deps/simple.Tpo"; exit 1; fi                             
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT simple.lo -MD -MP -MF .deps/simple.Tpo -c simple.c  -fPIC -DPIC -o .libs/simple.o                                                                                                       
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT simple_none.lo -MD -MP -MF ".deps/simple_none.Tpo" -c -o simple_none.lo simple_none.c; \                                             
        then mv -f ".deps/simple_none.Tpo" ".deps/simple_none.Plo"; else rm -f ".deps/simple_none.Tpo"; exit 1; fi              
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT simple_none.lo -MD -MP -MF .deps/simple_none.Tpo -c simple_none.c  -fPIC -DPIC -o .libs/simple_none.o                                                                                   
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT simple_abst.lo -MD -MP -MF ".deps/simple_abst.Tpo" -c -o simple_abst.lo simple_abst.c; \                                             
        then mv -f ".deps/simple_abst.Tpo" ".deps/simple_abst.Plo"; else rm -f ".deps/simple_abst.Tpo"; exit 1; fi              
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT simple_abst.lo -MD -MP -MF .deps/simple_abst.Tpo -c simple_abst.c  -fPIC -DPIC -o .libs/simple_abst.o                                                                                   
/bin/sh ../../libtool --tag=CC --mode=link gcc  -g -O2   -o libmixer.la   bag.lo mixer.lo simple.lo simple_none.lo simple_abst.lo                                                                                                                               
ar cru .libs/libmixer.a .libs/bag.o .libs/mixer.o .libs/simple.o .libs/simple_none.o .libs/simple_abst.o                        
ranlib .libs/libmixer.a                                                                                                         
creating libmixer.la                                                                                                            
(cd .libs && rm -f libmixer.la && ln -s ../libmixer.la libmixer.la)                                                             
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/mixer'                     
Making all in pcm                                                                                                               
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/pcm'                      
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/pcm'                      
make[3]: Nothing to be done for `all-am'.                                                                                       
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/pcm'                       
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT atomic.lo -MD -MP -MF ".deps/atomic.Tpo" -c -o atomic.lo atomic.c; \                                                                 
        then mv -f ".deps/atomic.Tpo" ".deps/atomic.Plo"; else rm -f ".deps/atomic.Tpo"; exit 1; fi                             
mkdir .libs                                                                                                                     
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT atomic.lo -MD -MP -MF .deps/atomic.Tpo -c atomic.c  -fPIC -DPIC -o .libs/atomic.o                                                                                                       
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT mask.lo -MD -MP -MF ".deps/mask.Tpo" -c -o mask.lo mask.c; \                                                                         
        then mv -f ".deps/mask.Tpo" ".deps/mask.Plo"; else rm -f ".deps/mask.Tpo"; exit 1; fi                                   
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT mask.lo -MD -MP -MF .deps/mask.Tpo -c mask.c  -fPIC -DPIC -o .libs/mask.o                                                                                                               
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT interval.lo -MD -MP -MF ".deps/interval.Tpo" -c -o interval.lo interval.c; \                                                         
        then mv -f ".deps/interval.Tpo" ".deps/interval.Plo"; else rm -f ".deps/interval.Tpo"; exit 1; fi                       
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT interval.lo -MD -MP -MF .deps/interval.Tpo -c interval.c  -fPIC -DPIC -o .libs/interval.o                                                                                               
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm.lo -MD -MP -MF ".deps/pcm.Tpo" -c -o pcm.lo pcm.c; \                                                                             
        then mv -f ".deps/pcm.Tpo" ".deps/pcm.Plo"; else rm -f ".deps/pcm.Tpo"; exit 1; fi                                      
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm.lo -MD -MP -MF .deps/pcm.Tpo -c pcm.c  -fPIC -DPIC -o .libs/pcm.o                                                                                                                   
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_params.lo -MD -MP -MF ".deps/pcm_params.Tpo" -c -o pcm_params.lo pcm_params.c; \                                                 
        then mv -f ".deps/pcm_params.Tpo" ".deps/pcm_params.Plo"; else rm -f ".deps/pcm_params.Tpo"; exit 1; fi                 
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_params.lo -MD -MP -MF .deps/pcm_params.Tpo -c pcm_params.c  -fPIC -DPIC -o .libs/pcm_params.o                                                                                       
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_simple.lo -MD -MP -MF ".deps/pcm_simple.Tpo" -c -o pcm_simple.lo pcm_simple.c; \                                                 
        then mv -f ".deps/pcm_simple.Tpo" ".deps/pcm_simple.Plo"; else rm -f ".deps/pcm_simple.Tpo"; exit 1; fi                 
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_simple.lo -MD -MP -MF .deps/pcm_simple.Tpo -c pcm_simple.c  -fPIC -DPIC -o .libs/pcm_simple.o                                                                                       
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_hw.lo -MD -MP -MF ".deps/pcm_hw.Tpo" -c -o pcm_hw.lo pcm_hw.c; \                                                                 
        then mv -f ".deps/pcm_hw.Tpo" ".deps/pcm_hw.Plo"; else rm -f ".deps/pcm_hw.Tpo"; exit 1; fi                             
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_hw.lo -MD -MP -MF .deps/pcm_hw.Tpo -c pcm_hw.c  -fPIC -DPIC -o .libs/pcm_hw.o                                                                                                       
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_misc.lo -MD -MP -MF ".deps/pcm_misc.Tpo" -c -o pcm_misc.lo pcm_misc.c; \                                                         
        then mv -f ".deps/pcm_misc.Tpo" ".deps/pcm_misc.Plo"; else rm -f ".deps/pcm_misc.Tpo"; exit 1; fi                       
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_misc.lo -MD -MP -MF .deps/pcm_misc.Tpo -c pcm_misc.c  -fPIC -DPIC -o .libs/pcm_misc.o                                                                                               
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_mmap.lo -MD -MP -MF ".deps/pcm_mmap.Tpo" -c -o pcm_mmap.lo pcm_mmap.c; \                                                         
        then mv -f ".deps/pcm_mmap.Tpo" ".deps/pcm_mmap.Plo"; else rm -f ".deps/pcm_mmap.Tpo"; exit 1; fi                       
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_mmap.lo -MD -MP -MF .deps/pcm_mmap.Tpo -c pcm_mmap.c  -fPIC -DPIC -o .libs/pcm_mmap.o                                                                                               
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_symbols.lo -MD -MP -MF ".deps/pcm_symbols.Tpo" -c -o pcm_symbols.lo pcm_symbols.c; \                                             
        then mv -f ".deps/pcm_symbols.Tpo" ".deps/pcm_symbols.Plo"; else rm -f ".deps/pcm_symbols.Tpo"; exit 1; fi              
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_symbols.lo -MD -MP -MF .deps/pcm_symbols.Tpo -c pcm_symbols.c  -fPIC -DPIC -o .libs/pcm_symbols.o                                                                                   
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_generic.lo -MD -MP -MF ".deps/pcm_generic.Tpo" -c -o pcm_generic.lo pcm_generic.c; \                                             
        then mv -f ".deps/pcm_generic.Tpo" ".deps/pcm_generic.Plo"; else rm -f ".deps/pcm_generic.Tpo"; exit 1; fi              
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_generic.lo -MD -MP -MF .deps/pcm_generic.Tpo -c pcm_generic.c  -fPIC -DPIC -o .libs/pcm_generic.o                                                                                   
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_plugin.lo -MD -MP -MF ".deps/pcm_plugin.Tpo" -c -o pcm_plugin.lo pcm_plugin.c; \                                                 
        then mv -f ".deps/pcm_plugin.Tpo" ".deps/pcm_plugin.Plo"; else rm -f ".deps/pcm_plugin.Tpo"; exit 1; fi                 
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_plugin.lo -MD -MP -MF .deps/pcm_plugin.Tpo -c pcm_plugin.c  -fPIC -DPIC -o .libs/pcm_plugin.o                                                                                       
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_copy.lo -MD -MP -MF ".deps/pcm_copy.Tpo" -c -o pcm_copy.lo pcm_copy.c; \                                                         
        then mv -f ".deps/pcm_copy.Tpo" ".deps/pcm_copy.Plo"; else rm -f ".deps/pcm_copy.Tpo"; exit 1; fi                       
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_copy.lo -MD -MP -MF .deps/pcm_copy.Tpo -c pcm_copy.c  -fPIC -DPIC -o .libs/pcm_copy.o                                                                                               
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_linear.lo -MD -MP -MF ".deps/pcm_linear.Tpo" -c -o pcm_linear.lo pcm_linear.c; \                                                 
        then mv -f ".deps/pcm_linear.Tpo" ".deps/pcm_linear.Plo"; else rm -f ".deps/pcm_linear.Tpo"; exit 1; fi                 
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_linear.lo -MD -MP -MF .deps/pcm_linear.Tpo -c pcm_linear.c  -fPIC -DPIC -o .libs/pcm_linear.o                                                                                       
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_route.lo -MD -MP -MF ".deps/pcm_route.Tpo" -c -o pcm_route.lo pcm_route.c; \                                                     
        then mv -f ".deps/pcm_route.Tpo" ".deps/pcm_route.Plo"; else rm -f ".deps/pcm_route.Tpo"; exit 1; fi                    
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_route.lo -MD -MP -MF .deps/pcm_route.Tpo -c pcm_route.c  -fPIC -DPIC -o .libs/pcm_route.o                                                                                           
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_mulaw.lo -MD -MP -MF ".deps/pcm_mulaw.Tpo" -c -o pcm_mulaw.lo pcm_mulaw.c; \                                                     
        then mv -f ".deps/pcm_mulaw.Tpo" ".deps/pcm_mulaw.Plo"; else rm -f ".deps/pcm_mulaw.Tpo"; exit 1; fi                    
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_mulaw.lo -MD -MP -MF .deps/pcm_mulaw.Tpo -c pcm_mulaw.c  -fPIC -DPIC -o .libs/pcm_mulaw.o                                                                                           
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_alaw.lo -MD -MP -MF ".deps/pcm_alaw.Tpo" -c -o pcm_alaw.lo pcm_alaw.c; \                                                         
        then mv -f ".deps/pcm_alaw.Tpo" ".deps/pcm_alaw.Plo"; else rm -f ".deps/pcm_alaw.Tpo"; exit 1; fi                       
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_alaw.lo -MD -MP -MF .deps/pcm_alaw.Tpo -c pcm_alaw.c  -fPIC -DPIC -o .libs/pcm_alaw.o                                                                                               
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_adpcm.lo -MD -MP -MF ".deps/pcm_adpcm.Tpo" -c -o pcm_adpcm.lo pcm_adpcm.c; \                                                     
        then mv -f ".deps/pcm_adpcm.Tpo" ".deps/pcm_adpcm.Plo"; else rm -f ".deps/pcm_adpcm.Tpo"; exit 1; fi                    
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_adpcm.lo -MD -MP -MF .deps/pcm_adpcm.Tpo -c pcm_adpcm.c  -fPIC -DPIC -o .libs/pcm_adpcm.o                                                                                           
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_rate.lo -MD -MP -MF ".deps/pcm_rate.Tpo" -c -o pcm_rate.lo pcm_rate.c; \                                                         
        then mv -f ".deps/pcm_rate.Tpo" ".deps/pcm_rate.Plo"; else rm -f ".deps/pcm_rate.Tpo"; exit 1; fi                       
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_rate.lo -MD -MP -MF .deps/pcm_rate.Tpo -c pcm_rate.c  -fPIC -DPIC -o .libs/pcm_rate.o                                                                                               
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_rate_linear.lo -MD -MP -MF ".deps/pcm_rate_linear.Tpo" -c -o pcm_rate_linear.lo pcm_rate_linear.c; \                             
        then mv -f ".deps/pcm_rate_linear.Tpo" ".deps/pcm_rate_linear.Plo"; else rm -f ".deps/pcm_rate_linear.Tpo"; exit 1; fi  
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_rate_linear.lo -MD -MP -MF .deps/pcm_rate_linear.Tpo -c pcm_rate_linear.c  -fPIC -DPIC -o .libs/pcm_rate_linear.o                                                                   
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_plug.lo -MD -MP -MF ".deps/pcm_plug.Tpo" -c -o pcm_plug.lo pcm_plug.c; \                                                         
        then mv -f ".deps/pcm_plug.Tpo" ".deps/pcm_plug.Plo"; else rm -f ".deps/pcm_plug.Tpo"; exit 1; fi                       
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_plug.lo -MD -MP -MF .deps/pcm_plug.Tpo -c pcm_plug.c  -fPIC -DPIC -o .libs/pcm_plug.o                                                                                               
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_multi.lo -MD -MP -MF ".deps/pcm_multi.Tpo" -c -o pcm_multi.lo pcm_multi.c; \                                                     
        then mv -f ".deps/pcm_multi.Tpo" ".deps/pcm_multi.Plo"; else rm -f ".deps/pcm_multi.Tpo"; exit 1; fi                    
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_multi.lo -MD -MP -MF .deps/pcm_multi.Tpo -c pcm_multi.c  -fPIC -DPIC -o .libs/pcm_multi.o                                                                                           
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_shm.lo -MD -MP -MF ".deps/pcm_shm.Tpo" -c -o pcm_shm.lo pcm_shm.c; \                                                             
        then mv -f ".deps/pcm_shm.Tpo" ".deps/pcm_shm.Plo"; else rm -f ".deps/pcm_shm.Tpo"; exit 1; fi                          
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_shm.lo -MD -MP -MF .deps/pcm_shm.Tpo -c pcm_shm.c  -fPIC -DPIC -o .libs/pcm_shm.o                                                                                                   
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_file.lo -MD -MP -MF ".deps/pcm_file.Tpo" -c -o pcm_file.lo pcm_file.c; \                                                         
        then mv -f ".deps/pcm_file.Tpo" ".deps/pcm_file.Plo"; else rm -f ".deps/pcm_file.Tpo"; exit 1; fi                       
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_file.lo -MD -MP -MF .deps/pcm_file.Tpo -c pcm_file.c  -fPIC -DPIC -o .libs/pcm_file.o                                                                                               
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_null.lo -MD -MP -MF ".deps/pcm_null.Tpo" -c -o pcm_null.lo pcm_null.c; \                                                         
        then mv -f ".deps/pcm_null.Tpo" ".deps/pcm_null.Plo"; else rm -f ".deps/pcm_null.Tpo"; exit 1; fi                       
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_null.lo -MD -MP -MF .deps/pcm_null.Tpo -c pcm_null.c  -fPIC -DPIC -o .libs/pcm_null.o                                                                                               
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_empty.lo -MD -MP -MF ".deps/pcm_empty.Tpo" -c -o pcm_empty.lo pcm_empty.c; \                                                     
        then mv -f ".deps/pcm_empty.Tpo" ".deps/pcm_empty.Plo"; else rm -f ".deps/pcm_empty.Tpo"; exit 1; fi                    
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_empty.lo -MD -MP -MF .deps/pcm_empty.Tpo -c pcm_empty.c  -fPIC -DPIC -o .libs/pcm_empty.o                                                                                           
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_share.lo -MD -MP -MF ".deps/pcm_share.Tpo" -c -o pcm_share.lo pcm_share.c; \                                                     
        then mv -f ".deps/pcm_share.Tpo" ".deps/pcm_share.Plo"; else rm -f ".deps/pcm_share.Tpo"; exit 1; fi                    
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_share.lo -MD -MP -MF .deps/pcm_share.Tpo -c pcm_share.c  -fPIC -DPIC -o .libs/pcm_share.o                                                                                           
pcm_share.c: In function '_snd_pcm_share_missing':                                                                              
pcm_share.c:295: warning: ignoring return value of 'read', declared with attribute warn_unused_result                           
pcm_share.c:297: warning: ignoring return value of 'write', declared with attribute warn_unused_result                          
pcm_share.c:300: warning: ignoring return value of 'write', declared with attribute warn_unused_result                          
pcm_share.c:302: warning: ignoring return value of 'read', declared with attribute warn_unused_result                           
pcm_share.c: In function 'snd_pcm_share_thread':                                                                                
pcm_share.c:408: warning: ignoring return value of 'read', declared with attribute warn_unused_result                           
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_meter.lo -MD -MP -MF ".deps/pcm_meter.Tpo" -c -o pcm_meter.lo pcm_meter.c; \                                                     
        then mv -f ".deps/pcm_meter.Tpo" ".deps/pcm_meter.Plo"; else rm -f ".deps/pcm_meter.Tpo"; exit 1; fi                    
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_meter.lo -MD -MP -MF .deps/pcm_meter.Tpo -c pcm_meter.c  -fPIC -DPIC -o .libs/pcm_meter.o                                                                                           
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_hooks.lo -MD -MP -MF ".deps/pcm_hooks.Tpo" -c -o pcm_hooks.lo pcm_hooks.c; \                                                     
        then mv -f ".deps/pcm_hooks.Tpo" ".deps/pcm_hooks.Plo"; else rm -f ".deps/pcm_hooks.Tpo"; exit 1; fi                    
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_hooks.lo -MD -MP -MF .deps/pcm_hooks.Tpo -c pcm_hooks.c  -fPIC -DPIC -o .libs/pcm_hooks.o                                                                                           
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_ladspa.lo -MD -MP -MF ".deps/pcm_ladspa.Tpo" -c -o pcm_ladspa.lo pcm_ladspa.c; \                                                 
        then mv -f ".deps/pcm_ladspa.Tpo" ".deps/pcm_ladspa.Plo"; else rm -f ".deps/pcm_ladspa.Tpo"; exit 1; fi                 
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_ladspa.lo -MD -MP -MF .deps/pcm_ladspa.Tpo -c pcm_ladspa.c  -fPIC -DPIC -o .libs/pcm_ladspa.o                                                                                       
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_dmix.lo -MD -MP -MF ".deps/pcm_dmix.Tpo" -c -o pcm_dmix.lo pcm_dmix.c; \                                                         
        then mv -f ".deps/pcm_dmix.Tpo" ".deps/pcm_dmix.Plo"; else rm -f ".deps/pcm_dmix.Tpo"; exit 1; fi                       
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_dmix.lo -MD -MP -MF .deps/pcm_dmix.Tpo -c pcm_dmix.c  -fPIC -DPIC -o .libs/pcm_dmix.o                                                                                               
In file included from pcm_dmix.c:143:                                                                                           
pcm_dmix_i386.c: In function 'mix_select_callbacks':                                                                            
pcm_dmix_i386.c:48: warning: ignoring return value of 'fgets', declared with attribute warn_unused_result                       
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_dshare.lo -MD -MP -MF ".deps/pcm_dshare.Tpo" -c -o pcm_dshare.lo pcm_dshare.c; \                                                 
        then mv -f ".deps/pcm_dshare.Tpo" ".deps/pcm_dshare.Plo"; else rm -f ".deps/pcm_dshare.Tpo"; exit 1; fi                 
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_dshare.lo -MD -MP -MF .deps/pcm_dshare.Tpo -c pcm_dshare.c  -fPIC -DPIC -o .libs/pcm_dshare.o                                                                                       
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_dsnoop.lo -MD -MP -MF ".deps/pcm_dsnoop.Tpo" -c -o pcm_dsnoop.lo pcm_dsnoop.c; \                                                 
        then mv -f ".deps/pcm_dsnoop.Tpo" ".deps/pcm_dsnoop.Plo"; else rm -f ".deps/pcm_dsnoop.Tpo"; exit 1; fi                 
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_dsnoop.lo -MD -MP -MF .deps/pcm_dsnoop.Tpo -c pcm_dsnoop.c  -fPIC -DPIC -o .libs/pcm_dsnoop.o                                                                                       
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_direct.lo -MD -MP -MF ".deps/pcm_direct.Tpo" -c -o pcm_direct.lo pcm_direct.c; \                                                 
        then mv -f ".deps/pcm_direct.Tpo" ".deps/pcm_direct.Plo"; else rm -f ".deps/pcm_direct.Tpo"; exit 1; fi                 
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_direct.lo -MD -MP -MF .deps/pcm_direct.Tpo -c pcm_direct.c  -fPIC -DPIC -o .libs/pcm_direct.o                                                                                       
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_asym.lo -MD -MP -MF ".deps/pcm_asym.Tpo" -c -o pcm_asym.lo pcm_asym.c; \                                                         
        then mv -f ".deps/pcm_asym.Tpo" ".deps/pcm_asym.Plo"; else rm -f ".deps/pcm_asym.Tpo"; exit 1; fi                       
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_asym.lo -MD -MP -MF .deps/pcm_asym.Tpo -c pcm_asym.c  -fPIC -DPIC -o .libs/pcm_asym.o                                                                                               
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_iec958.lo -MD -MP -MF ".deps/pcm_iec958.Tpo" -c -o pcm_iec958.lo pcm_iec958.c; \                                                 
        then mv -f ".deps/pcm_iec958.Tpo" ".deps/pcm_iec958.Plo"; else rm -f ".deps/pcm_iec958.Tpo"; exit 1; fi                 
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_iec958.lo -MD -MP -MF .deps/pcm_iec958.Tpo -c pcm_iec958.c  -fPIC -DPIC -o .libs/pcm_iec958.o                                                                                       
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_softvol.lo -MD -MP -MF ".deps/pcm_softvol.Tpo" -c -o pcm_softvol.lo pcm_softvol.c; \                                             
        then mv -f ".deps/pcm_softvol.Tpo" ".deps/pcm_softvol.Plo"; else rm -f ".deps/pcm_softvol.Tpo"; exit 1; fi              
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_softvol.lo -MD -MP -MF .deps/pcm_softvol.Tpo -c pcm_softvol.c  -fPIC -DPIC -o .libs/pcm_softvol.o                                                                                   
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_extplug.lo -MD -MP -MF ".deps/pcm_extplug.Tpo" -c -o pcm_extplug.lo pcm_extplug.c; \                                             
        then mv -f ".deps/pcm_extplug.Tpo" ".deps/pcm_extplug.Plo"; else rm -f ".deps/pcm_extplug.Tpo"; exit 1; fi              
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_extplug.lo -MD -MP -MF .deps/pcm_extplug.Tpo -c pcm_extplug.c  -fPIC -DPIC -o .libs/pcm_extplug.o                                                                                   
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT pcm_ioplug.lo -MD -MP -MF ".deps/pcm_ioplug.Tpo" -c -o pcm_ioplug.lo pcm_ioplug.c; \                                                 
        then mv -f ".deps/pcm_ioplug.Tpo" ".deps/pcm_ioplug.Plo"; else rm -f ".deps/pcm_ioplug.Tpo"; exit 1; fi                 
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT pcm_ioplug.lo -MD -MP -MF .deps/pcm_ioplug.Tpo -c pcm_ioplug.c  -fPIC -DPIC -o .libs/pcm_ioplug.o                                                                                       
/bin/sh ../../libtool --tag=CC --mode=link gcc  -g -O2   -o libpcm.la   atomic.lo mask.lo interval.lo pcm.lo pcm_params.lo pcm_simple.lo pcm_hw.lo pcm_misc.lo pcm_mmap.lo pcm_symbols.lo pcm_generic.lo pcm_plugin.lo pcm_copy.lo pcm_linear.lo pcm_route.lo pcm_mulaw.lo pcm_alaw.lo pcm_adpcm.lo pcm_rate.lo pcm_rate_linear.lo pcm_plug.lo pcm_multi.lo pcm_shm.lo pcm_file.lo pcm_null.lo pcm_empty.lo pcm_share.lo pcm_meter.lo pcm_hooks.lo  pcm_ladspa.lo pcm_dmix.lo pcm_dshare.lo pcm_dsnoop.lo pcm_direct.lo   pcm_asym.lo pcm_iec958.lo pcm_softvol.lo pcm_extplug.lo pcm_ioplug.lo                                                                 
ar cru .libs/libpcm.a .libs/atomic.o .libs/mask.o .libs/interval.o .libs/pcm.o .libs/pcm_params.o .libs/pcm_simple.o .libs/pcm_hw.o .libs/pcm_misc.o .libs/pcm_mmap.o .libs/pcm_symbols.o .libs/pcm_generic.o .libs/pcm_plugin.o .libs/pcm_copy.o .libs/pcm_linear.o .libs/pcm_route.o .libs/pcm_mulaw.o .libs/pcm_alaw.o .libs/pcm_adpcm.o .libs/pcm_rate.o .libs/pcm_rate_linear.o .libs/pcm_plug.o .libs/pcm_multi.o .libs/pcm_shm.o .libs/pcm_file.o .libs/pcm_null.o .libs/pcm_empty.o .libs/pcm_share.o .libs/pcm_meter.o .libs/pcm_hooks.o .libs/pcm_ladspa.o .libs/pcm_dmix.o .libs/pcm_dshare.o .libs/pcm_dsnoop.o .libs/pcm_direct.o .libs/pcm_asym.o .libs/pcm_iec958.o .libs/pcm_softvol.o .libs/pcm_extplug.o .libs/pcm_ioplug.o                                                   
ranlib .libs/libpcm.a                                                                                                           
creating libpcm.la                                                                                                              
(cd .libs && rm -f libpcm.la && ln -s ../libpcm.la libpcm.la)                                                                   
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/pcm'                       
Making all in timer                                                                                                             
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/timer'                    
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT timer.lo -MD -MP -MF ".deps/timer.Tpo" -c -o timer.lo timer.c; \                                                                     
        then mv -f ".deps/timer.Tpo" ".deps/timer.Plo"; else rm -f ".deps/timer.Tpo"; exit 1; fi                                
mkdir .libs                                                                                                                     
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT timer.lo -MD -MP -MF .deps/timer.Tpo -c timer.c  -fPIC -DPIC -o .libs/timer.o                                                                                                           
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT timer_hw.lo -MD -MP -MF ".deps/timer_hw.Tpo" -c -o timer_hw.lo timer_hw.c; \                                                         
        then mv -f ".deps/timer_hw.Tpo" ".deps/timer_hw.Plo"; else rm -f ".deps/timer_hw.Tpo"; exit 1; fi                       
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT timer_hw.lo -MD -MP -MF .deps/timer_hw.Tpo -c timer_hw.c  -fPIC -DPIC -o .libs/timer_hw.o                                                                                               
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT timer_query.lo -MD -MP -MF ".deps/timer_query.Tpo" -c -o timer_query.lo timer_query.c; \                                             
        then mv -f ".deps/timer_query.Tpo" ".deps/timer_query.Plo"; else rm -f ".deps/timer_query.Tpo"; exit 1; fi              
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT timer_query.lo -MD -MP -MF .deps/timer_query.Tpo -c timer_query.c  -fPIC -DPIC -o .libs/timer_query.o                                                                                   
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT timer_query_hw.lo -MD -MP -MF ".deps/timer_query_hw.Tpo" -c -o timer_query_hw.lo timer_query_hw.c; \                                 
        then mv -f ".deps/timer_query_hw.Tpo" ".deps/timer_query_hw.Plo"; else rm -f ".deps/timer_query_hw.Tpo"; exit 1; fi     
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT timer_query_hw.lo -MD -MP -MF .deps/timer_query_hw.Tpo -c timer_query_hw.c  -fPIC -DPIC -o .libs/timer_query_hw.o                                                                       
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT timer_symbols.lo -MD -MP -MF ".deps/timer_symbols.Tpo" -c -o timer_symbols.lo timer_symbols.c; \                                     
        then mv -f ".deps/timer_symbols.Tpo" ".deps/timer_symbols.Plo"; else rm -f ".deps/timer_symbols.Tpo"; exit 1; fi        
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT timer_symbols.lo -MD -MP -MF .deps/timer_symbols.Tpo -c timer_symbols.c  -fPIC -DPIC -o .libs/timer_symbols.o                                                                           
/bin/sh ../../libtool --tag=CC --mode=link gcc  -g -O2   -o libtimer.la   timer.lo timer_hw.lo timer_query.lo timer_query_hw.lo timer_symbols.lo                                                                                                                
ar cru .libs/libtimer.a .libs/timer.o .libs/timer_hw.o .libs/timer_query.o .libs/timer_query_hw.o .libs/timer_symbols.o         
ranlib .libs/libtimer.a                                                                                                         
creating libtimer.la                                                                                                            
(cd .libs && rm -f libtimer.la && ln -s ../libtimer.la libtimer.la)                                                             
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/timer'                     
Making all in rawmidi                                                                                                           
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/rawmidi'                  
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT rawmidi.lo -MD -MP -MF ".deps/rawmidi.Tpo" -c -o rawmidi.lo rawmidi.c; \                                                             
        then mv -f ".deps/rawmidi.Tpo" ".deps/rawmidi.Plo"; else rm -f ".deps/rawmidi.Tpo"; exit 1; fi                          
mkdir .libs                                                                                                                     
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT rawmidi.lo -MD -MP -MF .deps/rawmidi.Tpo -c rawmidi.c  -fPIC -DPIC -o .libs/rawmidi.o                                                                                                   
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT rawmidi_hw.lo -MD -MP -MF ".deps/rawmidi_hw.Tpo" -c -o rawmidi_hw.lo rawmidi_hw.c; \                                                 
        then mv -f ".deps/rawmidi_hw.Tpo" ".deps/rawmidi_hw.Plo"; else rm -f ".deps/rawmidi_hw.Tpo"; exit 1; fi                 
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT rawmidi_hw.lo -MD -MP -MF .deps/rawmidi_hw.Tpo -c rawmidi_hw.c  -fPIC -DPIC -o .libs/rawmidi_hw.o                                                                                       
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT rawmidi_symbols.lo -MD -MP -MF ".deps/rawmidi_symbols.Tpo" -c -o rawmidi_symbols.lo rawmidi_symbols.c; \                             
        then mv -f ".deps/rawmidi_symbols.Tpo" ".deps/rawmidi_symbols.Plo"; else rm -f ".deps/rawmidi_symbols.Tpo"; exit 1; fi  
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT rawmidi_symbols.lo -MD -MP -MF .deps/rawmidi_symbols.Tpo -c rawmidi_symbols.c  -fPIC -DPIC -o .libs/rawmidi_symbols.o                                                                   
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT rawmidi_virt.lo -MD -MP -MF ".deps/rawmidi_virt.Tpo" -c -o rawmidi_virt.lo rawmidi_virt.c; \                                         
        then mv -f ".deps/rawmidi_virt.Tpo" ".deps/rawmidi_virt.Plo"; else rm -f ".deps/rawmidi_virt.Tpo"; exit 1; fi           
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT rawmidi_virt.lo -MD -MP -MF .deps/rawmidi_virt.Tpo -c rawmidi_virt.c  -fPIC -DPIC -o .libs/rawmidi_virt.o                                                                               
/bin/sh ../../libtool --tag=CC --mode=link gcc  -g -O2   -o librawmidi.la   rawmidi.lo rawmidi_hw.lo rawmidi_symbols.lo rawmidi_virt.lo                                                                                                                         
ar cru .libs/librawmidi.a .libs/rawmidi.o .libs/rawmidi_hw.o .libs/rawmidi_symbols.o .libs/rawmidi_virt.o                       
ranlib .libs/librawmidi.a                                                                                                       
creating librawmidi.la                                                                                                          
(cd .libs && rm -f librawmidi.la && ln -s ../librawmidi.la librawmidi.la)                                                       
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/rawmidi'                   
Making all in hwdep                                                                                                             
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/hwdep'                    
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT hwdep.lo -MD -MP -MF ".deps/hwdep.Tpo" -c -o hwdep.lo hwdep.c; \                                                                     
        then mv -f ".deps/hwdep.Tpo" ".deps/hwdep.Plo"; else rm -f ".deps/hwdep.Tpo"; exit 1; fi                                
mkdir .libs                                                                                                                     
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT hwdep.lo -MD -MP -MF .deps/hwdep.Tpo -c hwdep.c  -fPIC -DPIC -o .libs/hwdep.o                                                                                                           
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT hwdep_hw.lo -MD -MP -MF ".deps/hwdep_hw.Tpo" -c -o hwdep_hw.lo hwdep_hw.c; \                                                         
        then mv -f ".deps/hwdep_hw.Tpo" ".deps/hwdep_hw.Plo"; else rm -f ".deps/hwdep_hw.Tpo"; exit 1; fi                       
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT hwdep_hw.lo -MD -MP -MF .deps/hwdep_hw.Tpo -c hwdep_hw.c  -fPIC -DPIC -o .libs/hwdep_hw.o                                                                                               
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT hwdep_symbols.lo -MD -MP -MF ".deps/hwdep_symbols.Tpo" -c -o hwdep_symbols.lo hwdep_symbols.c; \                                     
        then mv -f ".deps/hwdep_symbols.Tpo" ".deps/hwdep_symbols.Plo"; else rm -f ".deps/hwdep_symbols.Tpo"; exit 1; fi        
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT hwdep_symbols.lo -MD -MP -MF .deps/hwdep_symbols.Tpo -c hwdep_symbols.c  -fPIC -DPIC -o .libs/hwdep_symbols.o                                                                           
/bin/sh ../../libtool --tag=CC --mode=link gcc  -g -O2   -o libhwdep.la   hwdep.lo hwdep_hw.lo hwdep_symbols.lo                 
ar cru .libs/libhwdep.a .libs/hwdep.o .libs/hwdep_hw.o .libs/hwdep_symbols.o                                                    
ranlib .libs/libhwdep.a                                                                                                         
creating libhwdep.la                                                                                                            
(cd .libs && rm -f libhwdep.la && ln -s ../libhwdep.la libhwdep.la)                                                             
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/hwdep'                     
Making all in seq                                                                                                               
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/seq'                      
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT seq_hw.lo -MD -MP -MF ".deps/seq_hw.Tpo" -c -o seq_hw.lo seq_hw.c; \                                                                 
        then mv -f ".deps/seq_hw.Tpo" ".deps/seq_hw.Plo"; else rm -f ".deps/seq_hw.Tpo"; exit 1; fi                             
mkdir .libs                                                                                                                     
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT seq_hw.lo -MD -MP -MF .deps/seq_hw.Tpo -c seq_hw.c  -fPIC -DPIC -o .libs/seq_hw.o                                                                                                       
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT seq.lo -MD -MP -MF ".deps/seq.Tpo" -c -o seq.lo seq.c; \                                                                             
        then mv -f ".deps/seq.Tpo" ".deps/seq.Plo"; else rm -f ".deps/seq.Tpo"; exit 1; fi                                      
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT seq.lo -MD -MP -MF .deps/seq.Tpo -c seq.c  -fPIC -DPIC -o .libs/seq.o                                                                                                                   
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT seq_event.lo -MD -MP -MF ".deps/seq_event.Tpo" -c -o seq_event.lo seq_event.c; \                                                     
        then mv -f ".deps/seq_event.Tpo" ".deps/seq_event.Plo"; else rm -f ".deps/seq_event.Tpo"; exit 1; fi                    
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT seq_event.lo -MD -MP -MF .deps/seq_event.Tpo -c seq_event.c  -fPIC -DPIC -o .libs/seq_event.o                                                                                           
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT seqmid.lo -MD -MP -MF ".deps/seqmid.Tpo" -c -o seqmid.lo seqmid.c; \                                                                 
        then mv -f ".deps/seqmid.Tpo" ".deps/seqmid.Plo"; else rm -f ".deps/seqmid.Tpo"; exit 1; fi                             
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT seqmid.lo -MD -MP -MF .deps/seqmid.Tpo -c seqmid.c  -fPIC -DPIC -o .libs/seqmid.o                                                                                                       
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT seq_midi_event.lo -MD -MP -MF ".deps/seq_midi_event.Tpo" -c -o seq_midi_event.lo seq_midi_event.c; \                                 
        then mv -f ".deps/seq_midi_event.Tpo" ".deps/seq_midi_event.Plo"; else rm -f ".deps/seq_midi_event.Tpo"; exit 1; fi     
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT seq_midi_event.lo -MD -MP -MF .deps/seq_midi_event.Tpo -c seq_midi_event.c  -fPIC -DPIC -o .libs/seq_midi_event.o                                                                       
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT seq_symbols.lo -MD -MP -MF ".deps/seq_symbols.Tpo" -c -o seq_symbols.lo seq_symbols.c; \                                             
        then mv -f ".deps/seq_symbols.Tpo" ".deps/seq_symbols.Plo"; else rm -f ".deps/seq_symbols.Tpo"; exit 1; fi              
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT seq_symbols.lo -MD -MP -MF .deps/seq_symbols.Tpo -c seq_symbols.c  -fPIC -DPIC -o .libs/seq_symbols.o                                                                                   
/bin/sh ../../libtool --tag=CC --mode=link gcc  -g -O2   -o libseq.la   seq_hw.lo seq.lo seq_event.lo seqmid.lo seq_midi_event.lo seq_symbols.lo                                                                                                                
ar cru .libs/libseq.a .libs/seq_hw.o .libs/seq.o .libs/seq_event.o .libs/seqmid.o .libs/seq_midi_event.o .libs/seq_symbols.o    
ranlib .libs/libseq.a                                                                                                           
creating libseq.la                                                                                                              
(cd .libs && rm -f libseq.la && ln -s ../libseq.la libseq.la)                                                                   
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/seq'                       
Making all in instr                                                                                                             
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/instr'                    
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT fm.lo -MD -MP -MF ".deps/fm.Tpo" -c -o fm.lo fm.c; \                                                                                 
        then mv -f ".deps/fm.Tpo" ".deps/fm.Plo"; else rm -f ".deps/fm.Tpo"; exit 1; fi                                         
mkdir .libs                                                                                                                     
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT fm.lo -MD -MP -MF .deps/fm.Tpo -c fm.c  -fPIC -DPIC -o .libs/fm.o                                                                                                                       
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT simple.lo -MD -MP -MF ".deps/simple.Tpo" -c -o simple.lo simple.c; \                                                                 
        then mv -f ".deps/simple.Tpo" ".deps/simple.Plo"; else rm -f ".deps/simple.Tpo"; exit 1; fi                             
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT simple.lo -MD -MP -MF .deps/simple.Tpo -c simple.c  -fPIC -DPIC -o .libs/simple.o                                                                                                       
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT iwffff.lo -MD -MP -MF ".deps/iwffff.Tpo" -c -o iwffff.lo iwffff.c; \                                                                 
        then mv -f ".deps/iwffff.Tpo" ".deps/iwffff.Plo"; else rm -f ".deps/iwffff.Tpo"; exit 1; fi                             
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT iwffff.lo -MD -MP -MF .deps/iwffff.Tpo -c iwffff.c  -fPIC -DPIC -o .libs/iwffff.o                                                                                                       
/bin/sh ../../libtool --tag=CC --mode=link gcc  -g -O2   -o libinstr.la   fm.lo simple.lo iwffff.lo                             
ar cru .libs/libinstr.a .libs/fm.o .libs/simple.o .libs/iwffff.o                                                                
ranlib .libs/libinstr.a                                                                                                         
creating libinstr.la                                                                                                            
(cd .libs && rm -f libinstr.la && ln -s ../libinstr.la libinstr.la)                                                             
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/instr'                     
Making all in alisp                                                                                                             
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/alisp'                    
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT alisp.lo -MD -MP -MF ".deps/alisp.Tpo" -c -o alisp.lo alisp.c; \                                                                     
        then mv -f ".deps/alisp.Tpo" ".deps/alisp.Plo"; else rm -f ".deps/alisp.Tpo"; exit 1; fi                                
mkdir .libs                                                                                                                     
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT alisp.lo -MD -MP -MF .deps/alisp.Tpo -c alisp.c  -fPIC -DPIC -o .libs/alisp.o                                                                                                           
alisp.c: In function 'F_princ':                                                                                                 
alisp.c:1711: warning: format not a string literal and no format arguments                                                      
/bin/sh ../../libtool --tag=CC --mode=link gcc  -g -O2   -o libalisp.la   alisp.lo                                              
ar cru .libs/libalisp.a .libs/alisp.o                                                                                           
ranlib .libs/libalisp.a                                                                                                         
creating libalisp.la                                                                                                            
(cd .libs && rm -f libalisp.la && ln -s ../libalisp.la libalisp.la)                                                             
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/alisp'                     
Making all in compat                                                                                                            
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/compat'                   
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include     -g -O2 -MT empty.lo -MD -MP -MF ".deps/empty.Tpo" -c -o empty.lo empty.c; \                                                                                    
        then mv -f ".deps/empty.Tpo" ".deps/empty.Plo"; else rm -f ".deps/empty.Tpo"; exit 1; fi                                
mkdir .libs                                                                                                                     
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -g -O2 -MT empty.lo -MD -MP -MF .deps/empty.Tpo -c empty.c  -fPIC -DPIC -o .libs/empty.o                                                                                                                           
/bin/sh ../../libtool --tag=CC --mode=link gcc  -g -O2   -o libcompat.la   empty.lo                                             
ar cru .libs/libcompat.a .libs/empty.o                                                                                          
ranlib .libs/libcompat.a                                                                                                        
creating libcompat.la                                                                                                           
(cd .libs && rm -f libcompat.la && ln -s ../libcompat.la libcompat.la)                                                          
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/compat'                    
Making all in conf                                                                                                              
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/conf'                     
Making all in cards                                                                                                             
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/conf/cards'               
make[3]: Nothing to be done for `all'.                                                                                          
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/conf/cards'                
Making all in pcm                                                                                                               
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/conf/pcm'                 
make[3]: Nothing to be done for `all'.                                                                                          
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/conf/pcm'                  
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/conf'                     
make[3]: Nothing to be done for `all-am'.                                                                                       
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/conf'                      
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/conf'                      
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src'                          
if /bin/sh ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT conf.lo -MD -MP -MF ".deps/conf.Tpo" -c -o conf.lo conf.c; \                                                                                  
        then mv -f ".deps/conf.Tpo" ".deps/conf.Plo"; else rm -f ".deps/conf.Tpo"; exit 1; fi                                   
mkdir .libs                                                                                                                     
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT conf.lo -MD -MP -MF .deps/conf.Tpo -c conf.c  -fPIC -DPIC -o .libs/conf.o                                                                                                                     
if /bin/sh ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT confmisc.lo -MD -MP -MF ".deps/confmisc.Tpo" -c -o confmisc.lo confmisc.c; \                                                                  
        then mv -f ".deps/confmisc.Tpo" ".deps/confmisc.Plo"; else rm -f ".deps/confmisc.Tpo"; exit 1; fi                       
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT confmisc.lo -MD -MP -MF .deps/confmisc.Tpo -c confmisc.c  -fPIC -DPIC -o .libs/confmisc.o                                                                                                     
if /bin/sh ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT input.lo -MD -MP -MF ".deps/input.Tpo" -c -o input.lo input.c; \                                                                              
        then mv -f ".deps/input.Tpo" ".deps/input.Plo"; else rm -f ".deps/input.Tpo"; exit 1; fi                                
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT input.lo -MD -MP -MF .deps/input.Tpo -c input.c  -fPIC -DPIC -o .libs/input.o                                                                                                                 
if /bin/sh ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT output.lo -MD -MP -MF ".deps/output.Tpo" -c -o output.lo output.c; \                                                                          
        then mv -f ".deps/output.Tpo" ".deps/output.Plo"; else rm -f ".deps/output.Tpo"; exit 1; fi                             
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT output.lo -MD -MP -MF .deps/output.Tpo -c output.c  -fPIC -DPIC -o .libs/output.o                                                                                                             
if /bin/sh ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT async.lo -MD -MP -MF ".deps/async.Tpo" -c -o async.lo async.c; \                                                                              
        then mv -f ".deps/async.Tpo" ".deps/async.Plo"; else rm -f ".deps/async.Tpo"; exit 1; fi                                
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT async.lo -MD -MP -MF .deps/async.Tpo -c async.c  -fPIC -DPIC -o .libs/async.o                                                                                                                 
if /bin/sh ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT error.lo -MD -MP -MF ".deps/error.Tpo" -c -o error.lo error.c; \                                                                              
        then mv -f ".deps/error.Tpo" ".deps/error.Plo"; else rm -f ".deps/error.Tpo"; exit 1; fi                                
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT error.lo -MD -MP -MF .deps/error.Tpo -c error.c  -fPIC -DPIC -o .libs/error.o                                                                                                                 
if /bin/sh ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT dlmisc.lo -MD -MP -MF ".deps/dlmisc.Tpo" -c -o dlmisc.lo dlmisc.c; \                                                                          
        then mv -f ".deps/dlmisc.Tpo" ".deps/dlmisc.Plo"; else rm -f ".deps/dlmisc.Tpo"; exit 1; fi                             
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT dlmisc.lo -MD -MP -MF .deps/dlmisc.Tpo -c dlmisc.c  -fPIC -DPIC -o .libs/dlmisc.o                                                                                                             
if /bin/sh ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT socket.lo -MD -MP -MF ".deps/socket.Tpo" -c -o socket.lo socket.c; \                                                                          
        then mv -f ".deps/socket.Tpo" ".deps/socket.Plo"; else rm -f ".deps/socket.Tpo"; exit 1; fi                             
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT socket.lo -MD -MP -MF .deps/socket.Tpo -c socket.c  -fPIC -DPIC -o .libs/socket.o                                                                                                             
if /bin/sh ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT shmarea.lo -MD -MP -MF ".deps/shmarea.Tpo" -c -o shmarea.lo shmarea.c; \                                                                      
        then mv -f ".deps/shmarea.Tpo" ".deps/shmarea.Plo"; else rm -f ".deps/shmarea.Tpo"; exit 1; fi                          
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT shmarea.lo -MD -MP -MF .deps/shmarea.Tpo -c shmarea.c  -fPIC -DPIC -o .libs/shmarea.o                                                                                                         
if /bin/sh ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT userfile.lo -MD -MP -MF ".deps/userfile.Tpo" -c -o userfile.lo userfile.c; \                                                                  
        then mv -f ".deps/userfile.Tpo" ".deps/userfile.Plo"; else rm -f ".deps/userfile.Tpo"; exit 1; fi                       
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT userfile.lo -MD -MP -MF .deps/userfile.Tpo -c userfile.c  -fPIC -DPIC -o .libs/userfile.o                                                                                                     
if /bin/sh ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT names.lo -MD -MP -MF ".deps/names.Tpo" -c -o names.lo names.c; \                                                                              
        then mv -f ".deps/names.Tpo" ".deps/names.Plo"; else rm -f ".deps/names.Tpo"; exit 1; fi                                
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT names.lo -MD -MP -MF .deps/names.Tpo -c names.c  -fPIC -DPIC -o .libs/names.o                                                                                                                 
/bin/sh ../libtool --tag=CC --mode=link gcc  -g -O2   -o libasound.la -rpath /usr/lib -version-info 2:0:0 -Wl,--version-script=Versions  conf.lo confmisc.lo input.lo output.lo async.lo error.lo dlmisc.lo socket.lo shmarea.lo userfile.lo names.lo control/libcontrol.la mixer/libmixer.la pcm/libpcm.la timer/libtimer.la rawmidi/librawmidi.la hwdep/libhwdep.la seq/libseq.la instr/libinstr.la alisp/libalisp.la compat/libcompat.la -lm -ldl -lpthread                                                                  
gcc -shared  .libs/conf.o .libs/confmisc.o .libs/input.o .libs/output.o .libs/async.o .libs/error.o .libs/dlmisc.o .libs/socket.o .libs/shmarea.o .libs/userfile.o .libs/names.o -Wl,--whole-archive control/.libs/libcontrol.a mixer/.libs/libmixer.a pcm/.libs/libpcm.a timer/.libs/libtimer.a rawmidi/.libs/librawmidi.a hwdep/.libs/libhwdep.a seq/.libs/libseq.a instr/.libs/libinstr.a alisp/.libs/libalisp.a compat/.libs/libcompat.a -Wl,--no-whole-archive  -lm -ldl -lpthread  -Wl,--version-script=Versions -Wl,-soname -Wl,libasound.so.2 -o .libs/libasound.so.2.0.0                                                                               
(cd .libs && rm -f libasound.so.2 && ln -s libasound.so.2.0.0 libasound.so.2)                                                   
(cd .libs && rm -f libasound.so && ln -s libasound.so.2.0.0 libasound.so)                                                       
creating libasound.la                                                                                                           
(cd .libs && rm -f libasound.la && ln -s ../libasound.la libasound.la)                                                          
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src'                           
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src'                           
Making all in modules                                                                                                           
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/modules'                      
Making all in mixer                                                                                                             
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/modules/mixer'                
Making all in simple                                                                                                            
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/modules/mixer/simple'         
if /bin/sh ../../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../../include -I../../../include   -g -O2 -W -Wall -g -O2 -MT sbase.lo -MD -MP -MF ".deps/sbase.Tpo" -c -o sbase.lo sbase.c; \                                             
        then mv -f ".deps/sbase.Tpo" ".deps/sbase.Plo"; else rm -f ".deps/sbase.Tpo"; exit 1; fi                                
mkdir .libs                                                                                                                     
 gcc -DHAVE_CONFIG_H -I. -I. -I../../../include -I../../../include -g -O2 -W -Wall -g -O2 -MT sbase.lo -MD -MP -MF .deps/sbase.Tpo -c sbase.c  -fPIC -DPIC -o .libs/sbase.o                                                                                     
sbase.c: In function 'simple_event_add1':                                                                                       
sbase.c:347: warning: the address of 'info' will always evaluate as 'true'                                                      
/bin/sh ../../../libtool --tag=CC --mode=link gcc -g -O2 -W -Wall -g -O2   -o smixer-sbase.la -rpath /usr/lib/alsa-lib/smixer -module -avoid-version sbase.lo ../../../src/libasound.la                                                                         
gcc -shared  .libs/sbase.o  -Wl,--rpath -Wl,/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/.libs ../../../src/.libs/libasound.so  -Wl,-soname -Wl,smixer-sbase.so -o .libs/smixer-sbase.so                                            
creating smixer-sbase.la                                                                                                        
(cd .libs && rm -f smixer-sbase.la && ln -s ../smixer-sbase.la smixer-sbase.la)                                                 
if /bin/sh ../../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../../include -I../../../include   -g -O2 -W -Wall -g -O2 -MT ac97.lo -MD -MP -MF ".deps/ac97.Tpo" -c -o ac97.lo ac97.c; \                                                 
        then mv -f ".deps/ac97.Tpo" ".deps/ac97.Plo"; else rm -f ".deps/ac97.Tpo"; exit 1; fi                                   
 gcc -DHAVE_CONFIG_H -I. -I. -I../../../include -I../../../include -g -O2 -W -Wall -g -O2 -MT ac97.lo -MD -MP -MF .deps/ac97.Tpo -c ac97.c  -fPIC -DPIC -o .libs/ac97.o                                                                                         
if /bin/sh ../../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../../include -I../../../include   -g -O2 -W -Wall -g -O2 -MT sbasedl.lo -MD -MP -MF ".deps/sbasedl.Tpo" -c -o sbasedl.lo sbasedl.c; \                                     
        then mv -f ".deps/sbasedl.Tpo" ".deps/sbasedl.Plo"; else rm -f ".deps/sbasedl.Tpo"; exit 1; fi                          
 gcc -DHAVE_CONFIG_H -I. -I. -I../../../include -I../../../include -g -O2 -W -Wall -g -O2 -MT sbasedl.lo -MD -MP -MF .deps/sbasedl.Tpo -c sbasedl.c  -fPIC -DPIC -o .libs/sbasedl.o                                                                             
/bin/sh ../../../libtool --tag=CC --mode=link gcc -g -O2 -W -Wall -g -O2   -o smixer-ac97.la -rpath /usr/lib/alsa-lib/smixer -module -avoid-version ac97.lo sbasedl.lo ../../../src/libasound.la                                                                
gcc -shared  .libs/ac97.o .libs/sbasedl.o  -Wl,--rpath -Wl,/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/.libs ../../../src/.libs/libasound.so  -Wl,-soname -Wl,smixer-ac97.so -o .libs/smixer-ac97.so                               
creating smixer-ac97.la                                                                                                         
(cd .libs && rm -f smixer-ac97.la && ln -s ../smixer-ac97.la smixer-ac97.la)                                                    
if /bin/sh ../../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../../include -I../../../include   -g -O2 -W -Wall -g -O2 -MT hda.lo -MD -MP -MF ".deps/hda.Tpo" -c -o hda.lo hda.c; \                                                     
        then mv -f ".deps/hda.Tpo" ".deps/hda.Plo"; else rm -f ".deps/hda.Tpo"; exit 1; fi                                      
 gcc -DHAVE_CONFIG_H -I. -I. -I../../../include -I../../../include -g -O2 -W -Wall -g -O2 -MT hda.lo -MD -MP -MF .deps/hda.Tpo -c hda.c  -fPIC -DPIC -o .libs/hda.o                                                                                             
/bin/sh ../../../libtool --tag=CC --mode=link gcc -g -O2 -W -Wall -g -O2   -o smixer-hda.la -rpath /usr/lib/alsa-lib/smixer -module -avoid-version hda.lo sbasedl.lo ../../../src/libasound.la                                                                  
gcc -shared  .libs/hda.o .libs/sbasedl.o  -Wl,--rpath -Wl,/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/.libs ../../../src/.libs/libasound.so  -Wl,-soname -Wl,smixer-hda.so -o .libs/smixer-hda.so                                  
creating smixer-hda.la                                                                                                          
(cd .libs && rm -f smixer-hda.la && ln -s ../smixer-hda.la smixer-hda.la)                                                       
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/modules/mixer/simple'          
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/modules/mixer'                
make[3]: Nothing to be done for `all-am'.                                                                                       
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/modules/mixer'                 
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/modules/mixer'                 
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/modules'                      
make[2]: Nothing to be done for `all-am'.                                                                                       
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/modules'                       
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/modules'                       
Making all in aserver                                                                                                           
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/aserver'                      
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -I../src/pcm    -g -O2 -MT aserver.o -MD -MP -MF ".deps/aserver.Tpo" -c -o aserver.o aserver.c; \                                                                                                      
        then mv -f ".deps/aserver.Tpo" ".deps/aserver.Po"; else rm -f ".deps/aserver.Tpo"; exit 1; fi                           
/bin/sh ../libtool --tag=CC --mode=link gcc  -g -O2   -o aserver  aserver.o ../src/libasound.la                                 
mkdir .libs                                                                                                                     
gcc -g -O2 -o .libs/aserver aserver.o  ../src/.libs/libasound.so -lm -ldl -lpthread                                             
creating aserver                                                                                                                
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/aserver'                       
Making all in alsalisp                                                                                                          
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/alsalisp'                     
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -I../src/alisp    -g -O2 -MT alsalisp.o -MD -MP -MF ".deps/alsalisp.Tpo" -c -o alsalisp.o alsalisp.c; \                                                                                                
        then mv -f ".deps/alsalisp.Tpo" ".deps/alsalisp.Po"; else rm -f ".deps/alsalisp.Tpo"; exit 1; fi                        
/bin/sh ../libtool --tag=CC --mode=link gcc  -g -O2   -o alsalisp  alsalisp.o ../src/libasound.la                               
mkdir .libs                                                                                                                     
gcc -g -O2 -o .libs/alsalisp alsalisp.o  ../src/.libs/libasound.so -lm -ldl -lpthread                                           
creating alsalisp                                                                                                               
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/alsalisp'                      
Making all in test                                                                                                              
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/test'                         
make[1]: Nothing to be done for `all'.                                                                                          
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/test'                          
Making all in utils                                                                                                             
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/utils'                        
make[1]: Nothing to be done for `all'.                                                                                          
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/utils'                         
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14'                              
make[1]: Nothing to be done for `all-am'.                                                                                       
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14'                               
Making install in doc                                                                                                           
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/doc'                          
Making install in pictures                                                                                                      
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/doc/pictures'                 
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/doc/pictures'                 
make[3]: Nothing to be done for `install-exec-am'.                                                                              
make[3]: Nothing to be done for `install-data-am'.                                                                              
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/doc/pictures'                  
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/doc/pictures'                  
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/doc'                          
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/doc'                          
make[3]: Nothing to be done for `install-exec-am'.                                                                              
make[3]: Nothing to be done for `install-data-am'.                                                                              
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/doc'                           
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/doc'                           
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/doc'                           
Making install in include                                                                                                       
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/include'                      
Making install in sound                                                                                                         
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/include/sound'                
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/include/sound'                
make[3]: Nothing to be done for `install-exec-am'.                                                                              
test -z "/usr/include/alsa/sound" || mkdir -p -- "/usr/include/alsa/sound"                                                      
 /usr/bin/install -c -m 644 'ainstr_fm.h' '/usr/include/alsa/sound/ainstr_fm.h'                                                 
 /usr/bin/install -c -m 644 'ainstr_gf1.h' '/usr/include/alsa/sound/ainstr_gf1.h'                                               
 /usr/bin/install -c -m 644 'ainstr_simple.h' '/usr/include/alsa/sound/ainstr_simple.h'                                         
 /usr/bin/install -c -m 644 'ainstr_iw.h' '/usr/include/alsa/sound/ainstr_iw.h'                                                 
 /usr/bin/install -c -m 644 'asound_fm.h' '/usr/include/alsa/sound/asound_fm.h'                                                 
 /usr/bin/install -c -m 644 'hdsp.h' '/usr/include/alsa/sound/hdsp.h'                                                           
 /usr/bin/install -c -m 644 'sb16_csp.h' '/usr/include/alsa/sound/sb16_csp.h'                                                   
 /usr/bin/install -c -m 644 'sscape_ioctl.h' '/usr/include/alsa/sound/sscape_ioctl.h'                                           
 /usr/bin/install -c -m 644 'emu10k1.h' '/usr/include/alsa/sound/emu10k1.h'                                                     
 /usr/bin/install -c -m 644 'type_compat.h' '/usr/include/alsa/sound/type_compat.h'                                             
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/include/sound'                 
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/include/sound'                 
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/include'                      
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/include'                      
make[3]: Nothing to be done for `install-exec-am'.                                                                              
test -z "/usr/include/alsa" || mkdir -p -- "/usr/include/alsa"                                                                  
 /usr/bin/install -c -m 644 'asoundlib.h' '/usr/include/alsa/asoundlib.h'                                                       
 /usr/bin/install -c -m 644 'asoundef.h' '/usr/include/alsa/asoundef.h'                                                         
 /usr/bin/install -c -m 644 'version.h' '/usr/include/alsa/version.h'                                                           
 /usr/bin/install -c -m 644 'global.h' '/usr/include/alsa/global.h'                                                             
 /usr/bin/install -c -m 644 'input.h' '/usr/include/alsa/input.h'                                                               
 /usr/bin/install -c -m 644 'output.h' '/usr/include/alsa/output.h'                                                             
 /usr/bin/install -c -m 644 'error.h' '/usr/include/alsa/error.h'                                                               
 /usr/bin/install -c -m 644 'conf.h' '/usr/include/alsa/conf.h'                                                                 
 /usr/bin/install -c -m 644 'pcm.h' '/usr/include/alsa/pcm.h'                                                                   
 /usr/bin/install -c -m 644 'pcm_old.h' '/usr/include/alsa/pcm_old.h'                                                           
 /usr/bin/install -c -m 644 'pcm_plugin.h' '/usr/include/alsa/pcm_plugin.h'                                                     
 /usr/bin/install -c -m 644 'rawmidi.h' '/usr/include/alsa/rawmidi.h'                                                           
 /usr/bin/install -c -m 644 'timer.h' '/usr/include/alsa/timer.h'                                                               
 /usr/bin/install -c -m 644 'hwdep.h' '/usr/include/alsa/hwdep.h'                                                               
 /usr/bin/install -c -m 644 'control.h' '/usr/include/alsa/control.h'                                                           
 /usr/bin/install -c -m 644 'mixer.h' '/usr/include/alsa/mixer.h'                                                               
 /usr/bin/install -c -m 644 'mixer_abst.h' '/usr/include/alsa/mixer_abst.h'                                                     
 /usr/bin/install -c -m 644 'seq_event.h' '/usr/include/alsa/seq_event.h'                                                       
 /usr/bin/install -c -m 644 'seq.h' '/usr/include/alsa/seq.h'                                                                   
 /usr/bin/install -c -m 644 'seqmid.h' '/usr/include/alsa/seqmid.h'                                                             
 /usr/bin/install -c -m 644 'seq_midi_event.h' '/usr/include/alsa/seq_midi_event.h'                                             
 /usr/bin/install -c -m 644 'conv.h' '/usr/include/alsa/conv.h'                                                                 
 /usr/bin/install -c -m 644 'instr.h' '/usr/include/alsa/instr.h'                                                               
 /usr/bin/install -c -m 644 'iatomic.h' '/usr/include/alsa/iatomic.h'                                                           
 /usr/bin/install -c -m 644 'alisp.h' '/usr/include/alsa/alisp.h'                                                               
 /usr/bin/install -c -m 644 'pcm_external.h' '/usr/include/alsa/pcm_external.h'                                                 
 /usr/bin/install -c -m 644 'pcm_ioplug.h' '/usr/include/alsa/pcm_ioplug.h'                                                     
 /usr/bin/install -c -m 644 'pcm_extplug.h' '/usr/include/alsa/pcm_extplug.h'                                                   
 /usr/bin/install -c -m 644 'pcm_rate.h' '/usr/include/alsa/pcm_rate.h'                                                         
 /usr/bin/install -c -m 644 'control_external.h' '/usr/include/alsa/control_external.h'                                         
make  install-data-hook                                                                                                         
make[4]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/include'                      
test -d /usr/include/sys || mkdir -p /usr/include/sys                                                                           
/usr/bin/install -c -m 644 ./sys.h /usr/include/sys/asoundlib.h                                                                 
make[4]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/include'                       
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/include'                       
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/include'                       
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/include'                       
Making install in src                                                                                                           
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src'                          
Making install in control                                                                                                       
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/control'                  
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/control'                  
make[3]: Nothing to be done for `install-exec-am'.                                                                              
make[3]: Nothing to be done for `install-data-am'.                                                                              
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/control'                   
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/control'                   
Making install in mixer                                                                                                         
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/mixer'                    
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/mixer'                    
make[3]: Nothing to be done for `install-exec-am'.                                                                              
make[3]: Nothing to be done for `install-data-am'.                                                                              
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/mixer'                     
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/mixer'                     
Making install in pcm                                                                                                           
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/pcm'                      
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/pcm'                      
make[4]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/pcm'                      
make[4]: Nothing to be done for `install-exec-am'.                                                                              
make[4]: Nothing to be done for `install-data-am'.                                                                              
make[4]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/pcm'                       
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/pcm'                       
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/pcm'                       
Making install in timer                                                                                                         
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/timer'                    
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/timer'                    
make[3]: Nothing to be done for `install-exec-am'.                                                                              
make[3]: Nothing to be done for `install-data-am'.                                                                              
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/timer'                     
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/timer'                     
Making install in rawmidi                                                                                                       
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/rawmidi'                  
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/rawmidi'                  
make[3]: Nothing to be done for `install-exec-am'.                                                                              
make[3]: Nothing to be done for `install-data-am'.                                                                              
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/rawmidi'                   
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/rawmidi'                   
Making install in hwdep                                                                                                         
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/hwdep'                    
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/hwdep'                    
make[3]: Nothing to be done for `install-exec-am'.                                                                              
make[3]: Nothing to be done for `install-data-am'.                                                                              
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/hwdep'                     
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/hwdep'                     
Making install in seq                                                                                                           
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/seq'                      
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/seq'                      
make[3]: Nothing to be done for `install-exec-am'.                                                                              
make[3]: Nothing to be done for `install-data-am'.                                                                              
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/seq'                       
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/seq'                       
Making install in instr                                                                                                         
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/instr'                    
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/instr'                    
make[3]: Nothing to be done for `install-exec-am'.                                                                              
make[3]: Nothing to be done for `install-data-am'.                                                                              
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/instr'                     
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/instr'                     
Making install in alisp                                                                                                         
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/alisp'                    
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/alisp'                    
make[3]: Nothing to be done for `install-exec-am'.                                                                              
make[3]: Nothing to be done for `install-data-am'.                                                                              
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/alisp'                     
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/alisp'                     
Making install in compat                                                                                                        
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/compat'                   
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/compat'                   
make[3]: Nothing to be done for `install-exec-am'.                                                                              
make[3]: Nothing to be done for `install-data-am'.                                                                              
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/compat'                    
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/compat'                    
Making install in conf                                                                                                          
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/conf'                     
Making install in cards                                                                                                         
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/conf/cards'               
make[4]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/conf/cards'               
make[4]: Nothing to be done for `install-exec-am'.                                                                              
test -z "/usr/share/alsa/cards/SI7018" || mkdir -p -- "/usr/share/alsa/cards/SI7018"                                            
 /usr/bin/install -c -m 644 'SI7018/sndoc-mixer.alisp' '/usr/share/alsa/cards/SI7018/sndoc-mixer.alisp'                         
 /usr/bin/install -c -m 644 'SI7018/sndop-mixer.alisp' '/usr/share/alsa/cards/SI7018/sndop-mixer.alisp'                         
test -z "/usr/share/alsa/cards" || mkdir -p -- "/usr/share/alsa/cards"                                                          
 /usr/bin/install -c -m 644 'aliases.conf' '/usr/share/alsa/cards/aliases.conf'                                                 
 /usr/bin/install -c -m 644 'AACI.conf' '/usr/share/alsa/cards/AACI.conf'                                                       
 /usr/bin/install -c -m 644 'ATIIXP.conf' '/usr/share/alsa/cards/ATIIXP.conf'                                                   
 /usr/bin/install -c -m 644 'ATIIXP-SPDMA.conf' '/usr/share/alsa/cards/ATIIXP-SPDMA.conf'                                       
 /usr/bin/install -c -m 644 'ATIIXP-MODEM.conf' '/usr/share/alsa/cards/ATIIXP-MODEM.conf'                                       
 /usr/bin/install -c -m 644 'AU8810.conf' '/usr/share/alsa/cards/AU8810.conf'                                                   
 /usr/bin/install -c -m 644 'AU8820.conf' '/usr/share/alsa/cards/AU8820.conf'                                                   
 /usr/bin/install -c -m 644 'AU8830.conf' '/usr/share/alsa/cards/AU8830.conf'                                                   
 /usr/bin/install -c -m 644 'Audigy.conf' '/usr/share/alsa/cards/Audigy.conf'                                                   
 /usr/bin/install -c -m 644 'Audigy2.conf' '/usr/share/alsa/cards/Audigy2.conf'                                                 
 /usr/bin/install -c -m 644 'Aureon51.conf' '/usr/share/alsa/cards/Aureon51.conf'                                               
 /usr/bin/install -c -m 644 'Aureon71.conf' '/usr/share/alsa/cards/Aureon71.conf'                                               
 /usr/bin/install -c -m 644 'CA0106.conf' '/usr/share/alsa/cards/CA0106.conf'                                                   
 /usr/bin/install -c -m 644 'CMI8338.conf' '/usr/share/alsa/cards/CMI8338.conf'                                                 
 /usr/bin/install -c -m 644 'CMI8338-SWIEC.conf' '/usr/share/alsa/cards/CMI8338-SWIEC.conf'                                     
 /usr/bin/install -c -m 644 'CMI8738-MC6.conf' '/usr/share/alsa/cards/CMI8738-MC6.conf'                                         
 /usr/bin/install -c -m 644 'CMI8738-MC8.conf' '/usr/share/alsa/cards/CMI8738-MC8.conf'                                         
 /usr/bin/install -c -m 644 'CS46xx.conf' '/usr/share/alsa/cards/CS46xx.conf'                                                   
 /usr/bin/install -c -m 644 'EMU10K1.conf' '/usr/share/alsa/cards/EMU10K1.conf'                                                 
 /usr/bin/install -c -m 644 'EMU10K1X.conf' '/usr/share/alsa/cards/EMU10K1X.conf'                                               
 /usr/bin/install -c -m 644 'ENS1370.conf' '/usr/share/alsa/cards/ENS1370.conf'                                                 
 /usr/bin/install -c -m 644 'ENS1371.conf' '/usr/share/alsa/cards/ENS1371.conf'                                                 
 /usr/bin/install -c -m 644 'ES1968.conf' '/usr/share/alsa/cards/ES1968.conf'                                                   
 /usr/bin/install -c -m 644 'FM801.conf' '/usr/share/alsa/cards/FM801.conf'                                                     
 /usr/bin/install -c -m 644 'GUS.conf' '/usr/share/alsa/cards/GUS.conf'                                                         
 /usr/bin/install -c -m 644 'HDA-Intel.conf' '/usr/share/alsa/cards/HDA-Intel.conf'                                             
 /usr/bin/install -c -m 644 'ICE1712.conf' '/usr/share/alsa/cards/ICE1712.conf'                                                 
 /usr/bin/install -c -m 644 'ICE1724.conf' '/usr/share/alsa/cards/ICE1724.conf'                                                 
 /usr/bin/install -c -m 644 'ICH.conf' '/usr/share/alsa/cards/ICH.conf'                                                         
 /usr/bin/install -c -m 644 'ICH4.conf' '/usr/share/alsa/cards/ICH4.conf'                                                       
 /usr/bin/install -c -m 644 'ICH-MODEM.conf' '/usr/share/alsa/cards/ICH-MODEM.conf'                                             
 /usr/bin/install -c -m 644 'Maestro3.conf' '/usr/share/alsa/cards/Maestro3.conf'                                               
 /usr/bin/install -c -m 644 'NFORCE.conf' '/usr/share/alsa/cards/NFORCE.conf'                                                   
 /usr/bin/install -c -m 644 'PC-Speaker.conf' '/usr/share/alsa/cards/PC-Speaker.conf'                                           
 /usr/bin/install -c -m 644 'PMac.conf' '/usr/share/alsa/cards/PMac.conf'                                                       
 /usr/bin/install -c -m 644 'PMacToonie.conf' '/usr/share/alsa/cards/PMacToonie.conf'                                           
 /usr/bin/install -c -m 644 'RME9636.conf' '/usr/share/alsa/cards/RME9636.conf'                                                 
 /usr/bin/install -c -m 644 'RME9652.conf' '/usr/share/alsa/cards/RME9652.conf'                                                 
 /usr/bin/install -c -m 644 'SI7018.conf' '/usr/share/alsa/cards/SI7018.conf'                                                   
 /usr/bin/install -c -m 644 'TRID4DWAVENX.conf' '/usr/share/alsa/cards/TRID4DWAVENX.conf'                                       
 /usr/bin/install -c -m 644 'USB-Audio.conf' '/usr/share/alsa/cards/USB-Audio.conf'                                             
 /usr/bin/install -c -m 644 'YMF744.conf' '/usr/share/alsa/cards/YMF744.conf'                                                   
 /usr/bin/install -c -m 644 'VIA686A.conf' '/usr/share/alsa/cards/VIA686A.conf'                                                 
 /usr/bin/install -c -m 644 'VIA8233.conf' '/usr/share/alsa/cards/VIA8233.conf'                                                 
 /usr/bin/install -c -m 644 'VIA8233A.conf' '/usr/share/alsa/cards/VIA8233A.conf'                                               
 /usr/bin/install -c -m 644 'VIA8237.conf' '/usr/share/alsa/cards/VIA8237.conf'                                                 
 /usr/bin/install -c -m 644 'VX222.conf' '/usr/share/alsa/cards/VX222.conf'                                                     
 /usr/bin/install -c -m 644 'VXPocket.conf' '/usr/share/alsa/cards/VXPocket.conf'                                               
 /usr/bin/install -c -m 644 'VXPocket440.conf' '/usr/share/alsa/cards/VXPocket440.conf'                                         
 /usr/bin/install -c -m 644 'aliases.alisp' '/usr/share/alsa/cards/aliases.alisp'                                               
make[4]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/conf/cards'                
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/conf/cards'                
Making install in pcm                                                                                                           
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/conf/pcm'                 
make[4]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/conf/pcm'                 
make[4]: Nothing to be done for `install-exec-am'.                                                                              
test -z "/usr/share/alsa/pcm" || mkdir -p -- "/usr/share/alsa/pcm"                                                              
 /usr/bin/install -c -m 644 'default.conf' '/usr/share/alsa/pcm/default.conf'                                                   
 /usr/bin/install -c -m 644 'front.conf' '/usr/share/alsa/pcm/front.conf'                                                       
 /usr/bin/install -c -m 644 'rear.conf' '/usr/share/alsa/pcm/rear.conf'                                                         
 /usr/bin/install -c -m 644 'center_lfe.conf' '/usr/share/alsa/pcm/center_lfe.conf'                                             
 /usr/bin/install -c -m 644 'side.conf' '/usr/share/alsa/pcm/side.conf'                                                         
 /usr/bin/install -c -m 644 'surround40.conf' '/usr/share/alsa/pcm/surround40.conf'                                             
 /usr/bin/install -c -m 644 'surround41.conf' '/usr/share/alsa/pcm/surround41.conf'                                             
 /usr/bin/install -c -m 644 'surround50.conf' '/usr/share/alsa/pcm/surround50.conf'                                             
 /usr/bin/install -c -m 644 'surround51.conf' '/usr/share/alsa/pcm/surround51.conf'                                             
 /usr/bin/install -c -m 644 'surround71.conf' '/usr/share/alsa/pcm/surround71.conf'                                             
 /usr/bin/install -c -m 644 'iec958.conf' '/usr/share/alsa/pcm/iec958.conf'                                                     
 /usr/bin/install -c -m 644 'modem.conf' '/usr/share/alsa/pcm/modem.conf'                                                       
 /usr/bin/install -c -m 644 'dmix.conf' '/usr/share/alsa/pcm/dmix.conf'                                                         
 /usr/bin/install -c -m 644 'dsnoop.conf' '/usr/share/alsa/pcm/dsnoop.conf'                                                     
 /usr/bin/install -c -m 644 'dpl.conf' '/usr/share/alsa/pcm/dpl.conf'                                                           
make[4]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/conf/pcm'                  
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/conf/pcm'                  
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/conf'                     
make[4]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/conf'                     
make[4]: Nothing to be done for `install-exec-am'.                                                                              
test -z "/usr/share/alsa" || mkdir -p -- "/usr/share/alsa"                                                                      
 /usr/bin/install -c -m 644 'alsa.conf' '/usr/share/alsa/alsa.conf'                                                             
 /usr/bin/install -c -m 644 'sndo-mixer.alisp' '/usr/share/alsa/sndo-mixer.alisp'                                               
 /usr/bin/install -c -m 644 'smixer.conf' '/usr/share/alsa/smixer.conf'                                                         
make[4]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/conf'                      
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/conf'                      
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src/conf'                      
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src'                          
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src'                          
test -z "/usr/lib" || mkdir -p -- "/usr/lib"                                                                                    
 /bin/sh ../libtool --mode=install /usr/bin/install -c  'libasound.la' '/usr/lib/libasound.la'                                  
/usr/bin/install -c .libs/libasound.so.2.0.0 /usr/lib/libasound.so.2.0.0                                                        
(cd /usr/lib && { ln -s -f libasound.so.2.0.0 libasound.so.2 || { rm -f libasound.so.2 && ln -s libasound.so.2.0.0 libasound.so.2; }; })                                                                                                                        
(cd /usr/lib && { ln -s -f libasound.so.2.0.0 libasound.so || { rm -f libasound.so && ln -s libasound.so.2.0.0 libasound.so; }; })                                                                                                                              
/usr/bin/install -c .libs/libasound.lai /usr/lib/libasound.la                                                                   
PATH="$PATH:/sbin" ldconfig -n /usr/lib                                                                                         
----------------------------------------------------------------------                                                          
Libraries have been installed in:                                                                                               
   /usr/lib                                                                                                                     

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:      
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable  
     during execution                                          
   - add LIBDIR to the `LD_RUN_PATH' environment variable      
     during linking                                            
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag              
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.   
----------------------------------------------------------------------
make[3]: Nothing to be done for `install-data-am'.                    
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src'
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src'
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/src'
Making install in modules                                                                            
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/modules'
Making install in mixer                                                                                   
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/modules/mixer'
Making install in simple                                                                                        
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/modules/mixer/simple'
make[4]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/modules/mixer/simple'
test -z "/usr/lib/alsa-lib/smixer" || mkdir -p -- "/usr/lib/alsa-lib/smixer"                                           
 /bin/sh ../../../libtool --mode=install /usr/bin/install -c  'smixer-sbase.la' '/usr/lib/alsa-lib/smixer/smixer-sbase.la'
libtool: install: warning: relinking `smixer-sbase.la'                                                                    
(cd /home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/modules/mixer/simple; /bin/sh ../../../libtool  --tag=CC --mode=relink gcc -g -O2 -W -Wall -g -O2 -o smixer-sbase.la -rpath /usr/lib/alsa-lib/smixer -module -avoid-version sbase.lo ../../../src/libasound.la )                                                                                                       
gcc -shared  .libs/sbase.o  -L/usr/lib -lasound  -Wl,-soname -Wl,smixer-sbase.so -o .libs/smixer-sbase.so                       
/usr/bin/install -c .libs/smixer-sbase.soT /usr/lib/alsa-lib/smixer/smixer-sbase.so                                             
/usr/bin/install -c .libs/smixer-sbase.lai /usr/lib/alsa-lib/smixer/smixer-sbase.la                                             
PATH="$PATH:/sbin" ldconfig -n /usr/lib/alsa-lib/smixer                                                                         
----------------------------------------------------------------------                                                          
Libraries have been installed in:                                                                                               
   /usr/lib/alsa-lib/smixer                                                                                                     

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:      
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable  
     during execution                                          
   - add LIBDIR to the `LD_RUN_PATH' environment variable      
     during linking                                            
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag              
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.   
----------------------------------------------------------------------
 /bin/sh ../../../libtool --mode=install /usr/bin/install -c  'smixer-ac97.la' '/usr/lib/alsa-lib/smixer/smixer-ac97.la'
libtool: install: warning: relinking `smixer-ac97.la'                                                                   
(cd /home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/modules/mixer/simple; /bin/sh ../../../libtool  --tag=CC --mode=relink gcc -g -O2 -W -Wall -g -O2 -o smixer-ac97.la -rpath /usr/lib/alsa-lib/smixer -module -avoid-version ac97.lo sbasedl.lo ../../../src/libasound.la )                                                                                              
gcc -shared  .libs/ac97.o .libs/sbasedl.o  -L/usr/lib -lasound  -Wl,-soname -Wl,smixer-ac97.so -o .libs/smixer-ac97.so          
/usr/bin/install -c .libs/smixer-ac97.soT /usr/lib/alsa-lib/smixer/smixer-ac97.so                                               
/usr/bin/install -c .libs/smixer-ac97.lai /usr/lib/alsa-lib/smixer/smixer-ac97.la                                               
PATH="$PATH:/sbin" ldconfig -n /usr/lib/alsa-lib/smixer                                                                         
----------------------------------------------------------------------                                                          
Libraries have been installed in:                                                                                               
   /usr/lib/alsa-lib/smixer                                                                                                     

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:      
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable  
     during execution                                          
   - add LIBDIR to the `LD_RUN_PATH' environment variable      
     during linking                                            
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag              
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.   
----------------------------------------------------------------------
 /bin/sh ../../../libtool --mode=install /usr/bin/install -c  'smixer-hda.la' '/usr/lib/alsa-lib/smixer/smixer-hda.la'
libtool: install: warning: relinking `smixer-hda.la'                                                                  
(cd /home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/modules/mixer/simple; /bin/sh ../../../libtool  --tag=CC --mode=relink gcc -g -O2 -W -Wall -g -O2 -o smixer-hda.la -rpath /usr/lib/alsa-lib/smixer -module -avoid-version hda.lo sbasedl.lo ../../../src/libasound.la )                                                                                                
gcc -shared  .libs/hda.o .libs/sbasedl.o  -L/usr/lib -lasound  -Wl,-soname -Wl,smixer-hda.so -o .libs/smixer-hda.so             
/usr/bin/install -c .libs/smixer-hda.soT /usr/lib/alsa-lib/smixer/smixer-hda.so                                                 
/usr/bin/install -c .libs/smixer-hda.lai /usr/lib/alsa-lib/smixer/smixer-hda.la                                                 
PATH="$PATH:/sbin" ldconfig -n /usr/lib/alsa-lib/smixer                                                                         
----------------------------------------------------------------------                                                          
Libraries have been installed in:                                                                                               
   /usr/lib/alsa-lib/smixer                                                                                                     

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:      
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable  
     during execution                                          
   - add LIBDIR to the `LD_RUN_PATH' environment variable      
     during linking                                            
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag              
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.   
----------------------------------------------------------------------
make[4]: Nothing to be done for `install-data-am'.                    
make[4]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/modules/mixer/simple'
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/modules/mixer/simple'
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/modules/mixer'      
make[4]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/modules/mixer'      
make[4]: Nothing to be done for `install-exec-am'.                                                                    
make[4]: Nothing to be done for `install-data-am'.                                                                    
make[4]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/modules/mixer'       
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/modules/mixer'       
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/modules/mixer'       
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/modules'            
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/modules'            
make[3]: Nothing to be done for `install-exec-am'.                                                                    
make[3]: Nothing to be done for `install-data-am'.                                                                    
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/modules'             
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/modules'             
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/modules'             
Making install in aserver                                                                                             
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/aserver'            
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/aserver'            
test -z "/usr/bin" || mkdir -p -- "/usr/bin"                                                                          
  /bin/sh ../libtool --mode=install /usr/bin/install -c 'aserver' '/usr/bin/aserver'                                  
/usr/bin/install -c .libs/aserver /usr/bin/aserver                                                                    
make[2]: Nothing to be done for `install-data-am'.                                                                    
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/aserver'             
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/aserver'             
Making install in alsalisp                                                                                            
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/alsalisp'           
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/alsalisp'           
make[2]: Nothing to be done for `install-exec-am'.                                                                    
make[2]: Nothing to be done for `install-data-am'.                                                                    
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/alsalisp'            
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/alsalisp'            
Making install in test                                                                                                
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/test'               
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/test'               
make[2]: Nothing to be done for `install-exec-am'.                                                                    
make[2]: Nothing to be done for `install-data-am'.                                                                    
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/test'                
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/test'                
Making install in utils                                                                                               
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/utils'              
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/utils'              
make[2]: Nothing to be done for `install-exec-am'.                                                                    
test -z "/usr/share/aclocal" || mkdir -p -- "/usr/share/aclocal"                                                      
 /usr/bin/install -c -m 644 'alsa.m4' '/usr/share/aclocal/alsa.m4'                                                    
test -z "/usr/lib/pkgconfig" || mkdir -p -- "/usr/lib/pkgconfig"                                                      
 /usr/bin/install -c -m 644 'alsa.pc' '/usr/lib/pkgconfig/alsa.pc'                                                    
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/utils'               
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/utils'               
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14'                    
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14'                    
make[2]: Nothing to be done for `install-exec-am'.                                                                    
make[2]: Nothing to be done for `install-data-am'.                                                                    
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14'                     
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14'                     
Compile ALSA Utility......                                                                                            
checking for a BSD-compatible install... /usr/bin/install -c                                                          
checking whether build environment is sane... yes                                                                     
checking for gawk... no                                                                                               
checking for mawk... mawk                                                                                             
checking whether make sets $(MAKE)... yes                                                                             
checking whether NLS is requested... yes                                                                              
checking for msgfmt... /usr/bin/msgfmt                                                                                
checking for gmsgfmt... /usr/bin/msgfmt                                                                               
checking for xgettext... /usr/bin/xgettext                                                                            
checking for msgmerge... /usr/bin/msgmerge                                                                            
checking for style of include used by make... GNU                                                                     
checking for gcc... gcc                                                                                               
checking for C compiler default output file name... a.out                                                             
checking whether the C compiler works... yes                                                                          
checking whether we are cross compiling... no                                                                         
checking for suffix of executables...                                                                                 
checking for suffix of object files... o                                                                              
checking whether we are using the GNU C compiler... yes                                                               
checking whether gcc accepts -g... yes                                                                                
checking for gcc option to accept ISO C89... none needed                                                              
checking dependency style of gcc... gcc3                                                                              
checking build system type... i686-pc-linux-gnu                                                                       
checking host system type... i686-pc-linux-gnu                                                                        
checking for ld used by GCC... /usr/bin/ld                                                                            
checking if the linker (/usr/bin/ld) is GNU ld... yes                                                                 
checking for shared library run path origin... done                                                                   
checking for CFPreferencesCopyAppValue... no                                                                          
checking for CFLocaleCopyCurrent... no                                                                                
checking for GNU gettext in libc... yes                                                                               
checking whether to use NLS... yes                                                                                    
checking where the gettext function comes from... libc                                                                
checking for cross-compiler... gcc                                                                                    
checking for gcc... (cached) gcc                                                                                      
checking whether we are using the GNU C compiler... (cached) yes                                                      
checking whether gcc accepts -g... (cached) yes                                                                       
checking for gcc option to accept ISO C89... (cached) none needed                                                     
checking dependency style of gcc... (cached) gcc3                                                                     
checking for a BSD-compatible install... /usr/bin/install -c                                                          
checking whether ln -s works... yes                                                                                   
checking for ALSA CFLAGS...                                                                                           
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread                                                             
checking for libasound headers version >= 1.0.12... found.                                                            
checking for snd_ctl_open in -lasound... yes                                                                          
checking how to run the C preprocessor... gcc -E                                                                      
checking for grep that handles long lines and -e... /bin/grep                                                         
checking for egrep... /bin/grep -E                                                                                    
checking for ANSI C header files... yes                                                                               
checking for initscr in -lncurses... yes                                                                              
checking for an ANSI C-conforming const... yes                                                                        
checking for inline... inline                                                                                         
checking whether time.h and sys/time.h may both be included... yes                                                    
checking whether gcc needs -traditional... no                                                                         
checking for special C compiler options needed for large files... no                                                  
checking for _FILE_OFFSET_BITS value needed for large files... 64                                                     
checking for _LARGE_FILES value needed for large files... no                                                          
configure: creating ./config.status                                                                                   
config.status: creating Makefile                                                                                      
config.status: creating alsactl/Makefile                                                                              
config.status: creating alsamixer/Makefile                                                                            
config.status: creating amidi/Makefile                                                                                
config.status: creating amixer/Makefile                                                                               
config.status: creating m4/Makefile                                                                                   
config.status: creating po/Makefile.in                                                                                
config.status: creating alsaconf/alsaconf                                                                             
config.status: creating alsaconf/Makefile                                                                             
config.status: creating alsaconf/po/Makefile                                                                          
config.status: WARNING:  alsaconf/po/Makefile.in seems to ignore the --datarootdir setting                            
config.status: creating aplay/Makefile                                                                                
config.status: creating include/Makefile                                                                              
config.status: creating iecset/Makefile                                                                               
config.status: creating utils/Makefile                                                                                
config.status: creating utils/alsa-utils.spec                                                                         
config.status: creating seq/Makefile                                                                                  
config.status: creating seq/aconnect/Makefile                                                                         
config.status: creating seq/aplaymidi/Makefile                                                                        
config.status: creating seq/aseqdump/Makefile                                                                         
config.status: creating seq/aseqnet/Makefile                                                                          
config.status: creating speaker-test/Makefile                                                                         
config.status: creating speaker-test/samples/Makefile                                                                 
config.status: creating include/aconfig.h                                                                             
config.status: executing po-directories commands                                                                      
config.status: creating po/POTFILES                                                                                   
config.status: creating po/Makefile                                                                                   
config.status: executing depfiles commands                                                                            
Making all in include                                                                                                 
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/include'          
make  all-am                                                                                                          
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/include'          
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/include'           
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/include'           
Making all in alsactl                                                                                                 
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/alsactl'          
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT alsactl.o -MD -MP -MF ".deps/alsactl.Tpo" -c -o alsactl.o alsactl.c; \                                                                                                                               
        then mv -f ".deps/alsactl.Tpo" ".deps/alsactl.Po"; else rm -f ".deps/alsactl.Tpo"; exit 1; fi                           
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT state.o -MD -MP -MF ".deps/state.Tpo" -c -o state.o state.c; \       
        then mv -f ".deps/state.Tpo" ".deps/state.Po"; else rm -f ".deps/state.Tpo"; exit 1; fi                                 
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT names.o -MD -MP -MF ".deps/names.Tpo" -c -o names.o names.c; \       
        then mv -f ".deps/names.Tpo" ".deps/names.Po"; else rm -f ".deps/names.Tpo"; exit 1; fi                                 
gcc  -g -O2   -o alsactl  alsactl.o state.o names.o  -lasound -lm -ldl -lpthread                                                
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/alsactl'                     
Making all in alsaconf                                                                                                          
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/alsaconf'                   
Making all in po                                                                                                                
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/alsaconf/po'                
35 translated messages, 1 untranslated message.                                                                                 
34 translated messages, 1 fuzzy translation, 1 untranslated message.                                                            
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/alsaconf/po'                 
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/alsaconf'                   
make[2]: Nothing to be done for `all-am'.                                                                                       
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/alsaconf'                    
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/alsaconf'                    
Making all in alsamixer                                                                                                         
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/alsamixer'                  
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT alsamixer.o -MD -MP -MF ".deps/alsamixer.Tpo" -c -o alsamixer.o alsamixer.c; \                                                                                                                       
        then mv -f ".deps/alsamixer.Tpo" ".deps/alsamixer.Po"; else rm -f ".deps/alsamixer.Tpo"; exit 1; fi                     
gcc  -g -O2   -o alsamixer  alsamixer.o -lncurses -lasound -lm -ldl -lpthread                                                   
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/alsamixer'                   
Making all in amidi                                                                                                             
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/amidi'                      
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amidi.o -MD -MP -MF ".deps/amidi.Tpo" -c -o amidi.o amidi.c; \                                                                                                                           
        then mv -f ".deps/amidi.Tpo" ".deps/amidi.Po"; else rm -f ".deps/amidi.Tpo"; exit 1; fi                                 
amidi.c: In function ‘main’:                                                                                                    
amidi.c:658: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result                              
gcc  -g -O2   -o amidi  amidi.o  -lasound -lm -ldl -lpthread                                                                    
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/amidi'                       
Making all in amixer                                                                                                            
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/amixer'                     
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amixer.o -MD -MP -MF ".deps/amixer.Tpo" -c -o amixer.o amixer.c; \                                                                                                                       
        then mv -f ".deps/amixer.Tpo" ".deps/amixer.Po"; else rm -f ".deps/amixer.Tpo"; exit 1; fi                              
amixer.c: In function ‘get_integer’:                                                                                            
amixer.c:244: warning: ignoring return value of ‘strtol’, declared with attribute warn_unused_result                            
amixer.c: In function ‘get_integer64’:                                                                                          
amixer.c:272: warning: ignoring return value of ‘strtol’, declared with attribute warn_unused_result                            
amixer.c: In function ‘set_volume_simple’:                                                                                      
amixer.c:358: warning: ignoring return value of ‘strtol’, declared with attribute warn_unused_result                            
gcc  -g -O2   -o amixer  amixer.o -lm -lasound -lm -ldl -lpthread                                                               
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/amixer'                      
Making all in aplay                                                                                                             
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/aplay'                      
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT aplay.o -MD -MP -MF ".deps/aplay.Tpo" -c -o aplay.o aplay.c; \                                                                                                                           
        then mv -f ".deps/aplay.Tpo" ".deps/aplay.Po"; else rm -f ".deps/aplay.Tpo"; exit 1; fi                                 
aplay.c: In function ‘end_voc’:                                                                                                 
aplay.c:1881: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result                             
aplay.c: In function ‘end_wave’:                                                                                                
aplay.c:1901: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result                             
aplay.c:1903: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result                             
aplay.c: In function ‘end_au’:                                                                                                  
aplay.c:1916: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result                             
gcc  -g -O2   -o aplay  aplay.o -lasound  -lasound -lm -ldl -lpthread                                                           
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/aplay'                       
Making all in iecset                                                                                                            
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/iecset'                     
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecset.o -MD -MP -MF ".deps/iecset.Tpo" -c -o iecset.o iecset.c; \                                                                                                                       
        then mv -f ".deps/iecset.Tpo" ".deps/iecset.Po"; else rm -f ".deps/iecset.Tpo"; exit 1; fi                              
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecbits.o -MD -MP -MF ".deps/iecbits.Tpo" -c -o iecbits.o iecbits.c; \                                                                                                                   
        then mv -f ".deps/iecbits.Tpo" ".deps/iecbits.Po"; else rm -f ".deps/iecbits.Tpo"; exit 1; fi                           
gcc  -g -O2   -o iecset  iecset.o iecbits.o -lm -lasound -lm -ldl -lpthread                                                     
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/iecset'                      
Making all in seq                                                                                                               
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq'                        
Making all in aconnect                                                                                                          
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq/aconnect'               
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aconnect.o -MD -MP -MF ".deps/aconnect.Tpo" -c -o aconnect.o aconnect.c; \                                                                                                         
        then mv -f ".deps/aconnect.Tpo" ".deps/aconnect.Po"; else rm -f ".deps/aconnect.Tpo"; exit 1; fi                        
gcc  -g -O2   -o aconnect  aconnect.o  -lasound -lm -ldl -lpthread                                                              
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq/aconnect'                
Making all in aplaymidi                                                                                                         
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq/aplaymidi'              
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aplaymidi.o -MD -MP -MF ".deps/aplaymidi.Tpo" -c -o aplaymidi.o aplaymidi.c; \                                                                                                     
        then mv -f ".deps/aplaymidi.Tpo" ".deps/aplaymidi.Po"; else rm -f ".deps/aplaymidi.Tpo"; exit 1; fi                     
gcc  -g -O2   -o aplaymidi  aplaymidi.o  -lasound -lm -ldl -lpthread                                                            
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT arecordmidi.o -MD -MP -MF ".deps/arecordmidi.Tpo" -c -o arecordmidi.o arecordmidi.c; \                                                                                             
        then mv -f ".deps/arecordmidi.Tpo" ".deps/arecordmidi.Po"; else rm -f ".deps/arecordmidi.Tpo"; exit 1; fi               
gcc  -g -O2   -o arecordmidi  arecordmidi.o  -lasound -lm -ldl -lpthread                                                        
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq/aplaymidi'               
Making all in aseqdump                                                                                                          
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq/aseqdump'               
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqdump.o -MD -MP -MF ".deps/aseqdump.Tpo" -c -o aseqdump.o aseqdump.c; \                                                                                                         
        then mv -f ".deps/aseqdump.Tpo" ".deps/aseqdump.Po"; else rm -f ".deps/aseqdump.Tpo"; exit 1; fi                        
gcc  -g -O2   -o aseqdump  aseqdump.o  -lasound -lm -ldl -lpthread                                                              
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq/aseqdump'                
Making all in aseqnet                                                                                                           
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq/aseqnet'                
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqnet.o -MD -MP -MF ".deps/aseqnet.Tpo" -c -o aseqnet.o aseqnet.c; \                                                                                                             
        then mv -f ".deps/aseqnet.Tpo" ".deps/aseqnet.Po"; else rm -f ".deps/aseqnet.Tpo"; exit 1; fi                           
aseqnet.c: In function ‘flush_writebuf’:                                                                                        
aseqnet.c:494: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result                            
gcc  -g -O2   -o aseqnet  aseqnet.o  -lasound -lm -ldl -lpthread                                                                
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq/aseqnet'                 
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq'                        
make[2]: Nothing to be done for `all-am'.                                                                                       
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq'                         
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq'                         
Making all in speaker-test                                                                                                      
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/speaker-test'               
Making all in samples                                                                                                           
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/speaker-test/samples'       
make[2]: Nothing to be done for `all'.                                                                                          
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/speaker-test/samples'        
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/speaker-test'               
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT speaker-test.o -MD -MP -MF ".deps/speaker-test.Tpo" -c -o speaker-test.o speaker-test.c; \                                                                                               
        then mv -f ".deps/speaker-test.Tpo" ".deps/speaker-test.Po"; else rm -f ".deps/speaker-test.Tpo"; exit 1; fi            
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT pink.o -MD -MP -MF ".deps/pink.Tpo" -c -o pink.o pink.c; \                                                                                                                               
        then mv -f ".deps/pink.Tpo" ".deps/pink.Po"; else rm -f ".deps/pink.Tpo"; exit 1; fi                                    
gcc  -g -O2   -o speaker-test  speaker-test.o pink.o  -lasound -lm -ldl -lpthread                                               
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/speaker-test'                
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/speaker-test'                
Making all in utils                                                                                                             
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/utils'                      
make[1]: Nothing to be done for `all'.                                                                                          
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/utils'                       
Making all in m4                                                                                                                
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/m4'                         
make[1]: Nothing to be done for `all'.                                                                                          
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/m4'                          
Making all in po                                                                                                                
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/po'                         
make[1]: Nothing to be done for `all'.                                                                                          
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/po'                          
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14'                            
make[1]: Nothing to be done for `all-am'.                                                                                       
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14'                             
Making install in include                                                                                                       
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/include'                    
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/include'                    
make[2]: Nothing to be done for `install-exec-am'.                                                                              
make[2]: Nothing to be done for `install-data-am'.                                                                              
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/include'                     
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/include'                     
Making install in alsactl                                                                                                       
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/alsactl'                    
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/alsactl'                    
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"                                                                                  
  /usr/bin/install -c 'alsactl' '/usr/sbin/alsactl'                                                                             
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"                                                              
 /usr/bin/install -c -m 644 './alsactl.1' '/usr/share/man/man1/alsactl.1'                                                       
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/alsactl'                     
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/alsactl'                     
Making install in alsaconf                                                                                                      
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/alsaconf'                   
Making install in po                                                                                                            
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/alsaconf/po'                
mkdir -p -- /usr/share                                                                                                          
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/alsaconf/po'                 
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/alsaconf'                   
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/alsaconf'                   
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"                                                                                  
 /usr/bin/install -c 'alsaconf' '/usr/sbin/alsaconf'                                                                            
 /usr/bin/install -c -m 644 alsaconf.8 /usr/share/man/man8/alsaconf.8                                                           
 /usr/bin/install -c -m 644 alsaconf.fr.8 /usr/share/man/fr/man8/alsaconf.8                                                     
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/alsaconf'                    
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/alsaconf'                    
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/alsaconf'                    
Making install in alsamixer                                                                                                     
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/alsamixer'                  
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/alsamixer'                  
test -z "/usr/bin" || mkdir -p -- "/usr/bin"                                                                                    
  /usr/bin/install -c 'alsamixer' '/usr/bin/alsamixer'                                                                          
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"                                                              
 /usr/bin/install -c -m 644 './alsamixer.1' '/usr/share/man/man1/alsamixer.1'                                                   
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/alsamixer'                   
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/alsamixer'                   
Making install in amidi                                                                                                         
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/amidi'                      
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/amidi'                      
test -z "/usr/bin" || mkdir -p -- "/usr/bin"                                                                                    
  /usr/bin/install -c 'amidi' '/usr/bin/amidi'                                                                                  
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"                                                              
 /usr/bin/install -c -m 644 './amidi.1' '/usr/share/man/man1/amidi.1'                                                           
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/amidi'                       
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/amidi'                       
Making install in amixer                                                                                                        
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/amixer'                     
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/amixer'                     
test -z "/usr/bin" || mkdir -p -- "/usr/bin"                                                                                    
  /usr/bin/install -c 'amixer' '/usr/bin/amixer'                                                                                
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"                                                              
 /usr/bin/install -c -m 644 './amixer.1' '/usr/share/man/man1/amixer.1'                                                         
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/amixer'                      
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/amixer'                      
Making install in aplay                                                                                                         
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/aplay'                      
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/aplay'                      
test -z "/usr/bin" || mkdir -p -- "/usr/bin"                                                                                    
  /usr/bin/install -c 'aplay' '/usr/bin/aplay'                                                                                  
make  install-exec-hook                                                                                                         
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/aplay'                      
rm -f arecord                                                                                                                   
ln -s aplay arecord                                                                                                             
rm -f /usr/bin/arecord                                                                                                          
(cd /usr/bin && ln -s aplay arecord)                                                                                            
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/aplay'                       
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"                                                              
 /usr/bin/install -c -m 644 './aplay.1' '/usr/share/man/man1/aplay.1'                                                           
 /usr/bin/install -c -m 644 './arecord.1' '/usr/share/man/man1/arecord.1'                                                       
make  install-data-hook                                                                                                         
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/aplay'                      
rm -f /usr/share/man/man1/arecord.1                                                                                             
(cd /usr/share/man/man1 && ln -s aplay.1 arecord.1)                                                                             
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/aplay'                       
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/aplay'                       
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/aplay'                       
Making install in iecset                                                                                                        
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/iecset'                     
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/iecset'                     
test -z "/usr/bin" || mkdir -p -- "/usr/bin"                                                                                    
  /usr/bin/install -c 'iecset' '/usr/bin/iecset'                                                                                
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"                                                              
 /usr/bin/install -c -m 644 './iecset.1' '/usr/share/man/man1/iecset.1'                                                         
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/iecset'                      
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/iecset'                      
Making install in seq                                                                                                           
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq'                        
Making install in aconnect                                                                                                      
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq/aconnect'               
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq/aconnect'               
test -z "/usr/bin" || mkdir -p -- "/usr/bin"                                                                                    
  /usr/bin/install -c 'aconnect' '/usr/bin/aconnect'                                                                            
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"                                                              
 /usr/bin/install -c -m 644 './aconnect.1' '/usr/share/man/man1/aconnect.1'                                                     
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq/aconnect'                
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq/aconnect'                
Making install in aplaymidi                                                                                                     
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq/aplaymidi'              
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq/aplaymidi'              
test -z "/usr/bin" || mkdir -p -- "/usr/bin"                                                                                    
  /usr/bin/install -c 'aplaymidi' '/usr/bin/aplaymidi'                                                                          
  /usr/bin/install -c 'arecordmidi' '/usr/bin/arecordmidi'                                                                      
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"                                                              
 /usr/bin/install -c -m 644 './aplaymidi.1' '/usr/share/man/man1/aplaymidi.1'                                                   
 /usr/bin/install -c -m 644 './arecordmidi.1' '/usr/share/man/man1/arecordmidi.1'                                               
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq/aplaymidi'               
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq/aplaymidi'               
Making install in aseqdump                                                                                                      
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq/aseqdump'               
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq/aseqdump'               
test -z "/usr/bin" || mkdir -p -- "/usr/bin"                                                                                    
  /usr/bin/install -c 'aseqdump' '/usr/bin/aseqdump'                                                                            
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"                                                              
 /usr/bin/install -c -m 644 './aseqdump.1' '/usr/share/man/man1/aseqdump.1'                                                     
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq/aseqdump'                
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq/aseqdump'                
Making install in aseqnet                                                                                                       
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq/aseqnet'                
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq/aseqnet'                
test -z "/usr/bin" || mkdir -p -- "/usr/bin"                                                                                    
  /usr/bin/install -c 'aseqnet' '/usr/bin/aseqnet'                                                                              
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"                                                              
 /usr/bin/install -c -m 644 './aseqnet.1' '/usr/share/man/man1/aseqnet.1'                                                       
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq/aseqnet'                 
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq/aseqnet'                 
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq'                        
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq'                        
make[3]: Nothing to be done for `install-exec-am'.                                                                              
make[3]: Nothing to be done for `install-data-am'.                                                                              
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq'                         
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq'                         
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/seq'                         
Making install in speaker-test                                                                                                  
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/speaker-test'               
Making install in samples                                                                                                       
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/speaker-test/samples'       
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/speaker-test/samples'       
make[3]: Nothing to be done for `install-exec-am'.                                                                              
test -z "/usr/share/alsa/speaker-test" || mkdir -p -- "/usr/share/alsa/speaker-test"                                            
 /usr/bin/install -c -m 644 'sample_map.csv' '/usr/share/alsa/speaker-test/sample_map.csv'                                      
test -z "/usr/share/sounds/alsa" || mkdir -p -- "/usr/share/sounds/alsa"                                                        
 /usr/bin/install -c -m 644 'Front_Left.wav' '/usr/share/sounds/alsa/Front_Left.wav'                                            
 /usr/bin/install -c -m 644 'Rear_Center.wav' '/usr/share/sounds/alsa/Rear_Center.wav'                                          
 /usr/bin/install -c -m 644 'Rear_Right.wav' '/usr/share/sounds/alsa/Rear_Right.wav'                                            
 /usr/bin/install -c -m 644 'Side_Right.wav' '/usr/share/sounds/alsa/Side_Right.wav'                                            
 /usr/bin/install -c -m 644 'Front_Center.wav' '/usr/share/sounds/alsa/Front_Center.wav'                                        
 /usr/bin/install -c -m 644 'Front_Right.wav' '/usr/share/sounds/alsa/Front_Right.wav'                                          
 /usr/bin/install -c -m 644 'Noise.wav' '/usr/share/sounds/alsa/Noise.wav'                                                      
 /usr/bin/install -c -m 644 'Rear_Left.wav' '/usr/share/sounds/alsa/Rear_Left.wav'                                              
 /usr/bin/install -c -m 644 'Side_Left.wav' '/usr/share/sounds/alsa/Side_Left.wav'                                              
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/speaker-test/samples'        
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/speaker-test/samples'        
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/speaker-test'               
make[3]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/speaker-test'               
test -z "/usr/bin" || mkdir -p -- "/usr/bin"                                                                                    
  /usr/bin/install -c 'speaker-test' '/usr/bin/speaker-test'                                                                    
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"                                                              
 /usr/bin/install -c -m 644 './speaker-test.1' '/usr/share/man/man1/speaker-test.1'                                             
make[3]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/speaker-test'                
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/speaker-test'                
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/speaker-test'                
Making install in utils                                                                                                         
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/utils'                      
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/utils'                      
make[2]: Nothing to be done for `install-exec-am'.                                                                              
make[2]: Nothing to be done for `install-data-am'.                                                                              
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/utils'                       
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/utils'                       
Making install in m4                                                                                                            
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/m4'                         
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/m4'                         
make[2]: Nothing to be done for `install-exec-am'.                                                                              
make[2]: Nothing to be done for `install-data-am'.                                                                              
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/m4'                          
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/m4'                          
Making install in po                                                                                                            
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/po'                         
mkdir -p -- /usr/share                                                                                                          
installing ja.gmo as /usr/share/locale/ja/LC_MESSAGES/alsa-utils.mo                                                             
if test "alsa-utils" = "gettext-tools"; then \                                                                                  
          mkdir -p -- /usr/share/gettext/po; \                                                                                  
          for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed en@quot.header en@boldquot.header insert-header.sin Rules-quot   Makevars.template; do \                                                                                         
            /usr/bin/install -c -m 644 ./$file \                                                                                
                            /usr/share/gettext/po/$file; \                                                                      
          done; \                                                                                                               
          for file in Makevars; do \                                                                                            
            rm -f /usr/share/gettext/po/$file; \                                                                                
          done; \                                                                                                               
        else \                                                                                                                  
          : ; \                                                                                                                 
        fi                                                                                                                      
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14/po'
make[1]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14'
make[2]: Entering directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14'
make[1]: Leaving directory `/home/XXX/Desktop/realtek-linux-audiopack-4.06a/alsa-utils-1.0.14'
Remove Folder.....
ERROR: modinfo: could not find module snd-cs4232
```

I hope I don't have to reinstall ubuntu again, waiting for help.

---

### Post by Yellow Pasque on 2009-12-21
[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

### Post by PHaLaNX on 2009-12-22
I did what is told in that thread, and it broke my system so badly that I'm only trying to save the data now. It downloaded tons of files which I already had. It even deleted grub, I reinstalled it from the cd but now it doesn't let me login. Now what does a sound upgrade have to do with grub?? 

Anyway, hopefully I will find another distro soon, because I think I wasted enough time fiddling with all these bugs. 

Thanks for trying to help...

---

