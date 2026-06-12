---
title: "[SOLVED] HDMI sound via NVidia geforce 8200M"
date: 2009-02-22
forum: Multimedia Software
---

### Post by knlgSeekr on 2009-02-22
well, first off i'd like to start by saying.. i absolutely love linux and ubuntu :)

i am a noob by all means, i installed ubuntu 6.10 a few years ago on my old laptop but it was so slow, had a crappy graphics card & not enough HD space to share with windoze so i reverted to windoze and all but forgot about linux till i purchased my new laptop 2 days ago - HP G60-249WM.. pretty decent for $600 just in case you're in the market.. 2GHz processor, AMD Athlon X2 dual core processor.. and of course, the NVidia geForce 8200M to make things look pretty on its 16" screen.. anyway, i digress..

after great success getting my USBConnect Mercury aircard and TwinView set up.. i was ready to get some hdmi digital audio going to my HDtv / surround sound system..

i am running a dual boot with Ubuntu 8.10 / vista premium & had no issues getting sound via hdmi in windoze so i knew it worked

many, many hours later.. i finally got it to work.. 
for starters, i upgraded to the latest recommended NVidia driver (173) from system / administration / hardware drivers
unlike a lot of posts that i read regarding this issue, when i ran aplay -l, i would get:

[COLOR="Navy"]**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/COLOR]
so i figured that meant it was seeing my hdmi & just identifying it as conexant digital..

after going through the "PulseAudio - Connection Failed: Connection Refused" nightmare & trying every listed fix with no success.. i finally removed it using:

[COLOR="Navy"]killall pulseaudio
sudo apt-get remove pulseaudio
sudo apt-get autoremove pulseaudio
sudo rm /etc/X11/Xsession.d/70pulseaudio (wasn't found)
sudo apt-get install esound
sudo reboot[/COLOR]

after the reboot, pulseaudio was still listed in the drop-downs under sound preferences, so i removed all instances of it from synaptic packet manager as well (i've read you shouldn't do that.. but as this is a fresh install, i figured if i screwed anything up i would just re-install lol)

then i came across this post which turned out to be extremely helpful 
[http://www.mandladventures.com/2008/11/03/ubuntu-810-hdmi-sound-configuration/]("http://www.mandladventures.com/2008/11/03/ubuntu-810-hdmi-sound-configuration/")
in particular the part about enabling the IEC958 switch

then i came across some posts that recommended upgrading to Alsa 1.0.18.. but ironically not the one posted here in the ALSA Upgrade Script thread..
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810") lol 

so i had to figure out how to do it the manual way.. after finding out i had Asa 1.0.17, i downloaded Alsa 1.0.19.tar.bz2 from alsa-project.org & installed it with this script

after extracting it to my documents, i right clicked on the folder & clicked properties to get it's path.. which in my case was 
/home/MYUSERNAME/Documents/Downloads/alsa-driver-1.0.19

so i ran:

[COLOR="Navy"]cd /home/MYUSERNAME/Documents/Downloads/alsa-driver-1.0.19
sudo ./configure
sudo make
sudo make install
sudo reboot[/COLOR]

after the reboot, i ran alsamixer which interestingly enough still came up as v1.0.17, the difference being that now there was an additional IEC958 graph, labeled IEC958 1.. and underneath it, instead of 00 like the other 2, it was marked MM.. which i remembered means a muted device.

so i went back IEC953 switch menu again by double clicking on the volume control icon & clicking on preferences.. and sure enough, there was a third IEC953 there as well. i put a check in the box next to it, clicked on the swithches tab & put a check mark in it there as well.

then i ran aplay -l & got this!

[COLOR="Navy"]card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0[/COLOR]

i went into system / preferences / sound again and now there was an option for HDA NVidia NVIDIA HDMI (ALSA) which i of course selected for all but sound capture (ALSA - Advanced Linux Sound Architechture) and Device under default mixer tracks (HDA NVidia (Alsa mixer))

i hit test, and sure enough.. a beautiful beep emanated from my surround sound.. success! :) i'm jamming to some Bob Marley as i type this lol.. clear, crisp sound.. no volume issues. just figured i would share my experience & save some poor soul hours of torment & frustration.. lol

LINUX effin Rules!!! i got 1 month before classes for my microsoft certification (mcst) so that gives me plenty of time to play with linux.. haha

---

### Post by Nicodemus83 on 2009-02-28
Hi there!

I've got a Gigabyte GA73PVMS2H Nvidia geforce 7100 and I've just done what you did and now I've got the HDMI displaying but when I hit test I don't have the luck you had, and I don't understand why:(

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC885 Analog [ALC885 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC885 Digital [ALC885 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
francois@francois-desktop:~$

---

### Post by knlgSeekr on 2009-03-02
> **Nicodemus83 said:**
> Hi there!

I've got a Gigabyte GA73PVMS2H Nvidia geforce 7100 and I've just done what you did and now I've got the HDMI displaying but when I hit test I don't have the luck you had, and I don't understand why:(

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC885 Analog [ALC885 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC885 Digital [ALC885 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
francois@francois-desktop:~$
maybe something is still muted.. do your sound settings & volume control look similar to mine from the screenshots i attached?

---

### Post by knlgSeekr on 2009-03-02
and for anyone else trying to get this to work, i was able to replicate the same results a few days ago when i re-formatted my hard drive to give linux a bigger partition. it took less than 5 mins to get it working..

you don't even need to remove pulseaudio, just install the latest ALSA drivers, make sure nothing is muted in alsamixer and enable the switches as per the instructions.. and don't forget to change the settings under sound preferences.

---

### Post by crapple on 2009-03-03
this is what happens when I try and install. (I have geforce 9300ge but the concept should be the same) I follow the steps and this is my output from terminal from when I started until the first error which happens when I run sudo make```
harel@ubuntu:~$ cd /home/harel/Desktop/alsa-driver-1.0.9
harel@ubuntu:~/Desktop/alsa-driver-1.0.9$ sudo ./configure
checking for gcc... gcc
checking for C compiler default output... a.out
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
checking for current directory... /home/harel/Desktop/alsa-driver-1.0.9
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.27-11-generic/build
checking for directory with kernel build... 
checking for kernel version... 0.0.0
checking for GCC version... ./configure: eval: line 3568: syntax error near unexpected token `)'
./configure: eval: line 3568: `my_compiler_version=4.3.2-1ubuntu12)'
Kernel compiler:  Used compiler: gcc (Ubuntu 4.3.2-1ubuntu12) 4.3.2

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

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
checking for kernel linux/devfs_fs_kernel.h... "no"
checking for kernel linux/highmem.h... "yes"
checking for kernel linux/workqueue.h... "yes"
checking for kernel linux/dma-mapping.h... "yes"
checking for kernel asm/hw_irq.h... "yes"
checking for kernel linux/device.h... "yes"
checking for kernel linux/jiffies.h... "yes"
checking for kernel linux/compat.h... "yes"
checking for kernel linux/adb.h... "yes"
checking for kernel linux/cuda.h... "yes"
checking for kernel linux/pmu.h... "yes"
checking for kernel linux/moduleparam.h... "yes"
checking for kernel linux/syscalls.h... "yes"
checking for kernel linux/firmware.h... "yes"
checking for exported symbol dump_stack... grep: /lib/modules/2.6.27-11-generic/build/kernel/ksyms.c: No such file or directory
"no"
checking for kernel module symbol versions... "yes"
checking for PCI support in kernel... "yes"
checking for I2C driver in kernel... module
checking for firmware loader... yes
checking for directory to store kernel modules... /lib/modules/0.0.0/misc
checking for verbose printk... on
checking for debug level... none
checking for processor type... x86_64
checking for SMP... "yes"
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... "no"
checking for Kernel ISA-PnP module support... "no"
checking for strlcpy... "no"
checking for snprintf... "no"
checking for vsnprintf... "no"
checking for scnprintf... "no"
checking for sscanf... "no"
checking for vmalloc_to_page... "no"
checking for old kmod... "yes"
checking for PDE... "no"
checking for pci_set_consistent_dma_mask... "no"
checking for pci_dev_present... "no"
checking for msleep... "no"
checking for tty->count is the atomic type... "no"
checking for io_remap_pfn_range... "no"
checking for new io_remap_page_range... "no"
checking for kcalloc... "no"
checking for saved_config_space in pci_dev... "no"
checking for old kill_fasync... "no"
checking for dma_addr_t... "no"
checking for MUTEX macros... "no"
checking for driver version... 1.0.9
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for RTC callback support in kernel... "no"
checking for HPET support... "yes"
checking for Procfs support... "yes"
checking for USB support... "yes"
checking for PC-Speaker hook... "no"
checking for kernel PCMCIA
checking for PCMCIA support... "yes"
checking for PC9800 support in kernel... "no"
checking for parallel port support... "yes"
checking for which soundcards to compile driver for... all
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/config.h
config.status: include/config.h is unchanged
config.status: creating include/config1.h
config.status: include/config1.h is unchanged
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...
harel@ubuntu:~/Desktop/alsa-driver-1.0.9$ sudo make
make[1]: Entering directory `/home/harel/Desktop/alsa-driver-1.0.9/acore'
gcc -D__KERNEL__ -DMODULE=1 -I/home/harel/Desktop/alsa-driver-1.0.9/include  -I/lib/modules/2.6.27-11-generic/build/include -O2 -mno-red-zone -mcmodel=kernel -fno-reorder-blocks -fno-strength-reduce -finline-limit=2000 -D__SMP__ -DCONFIG_SMP -DLINUX -Wall -Wstrict-prototypes -fomit-frame-pointer -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -pipe -DALSA_BUILD -nostdinc -iwithprefix include -DMODVERSIONS -include /lib/modules/2.6.27-11-generic/build/include/linux/modversions.h  -DKBUILD_BASENAME=hpetimer   -c -o hpetimer.o hpetimer.c
cc1: error: /lib/modules/2.6.27-11-generic/build/include/linux/modversions.h: No such file or directory
In file included from hpetimer.c:22:
/home/harel/Desktop/alsa-driver-1.0.9/include/sound/driver.h:29:26: error: linux/config.h: No such file or directory
In file included from /lib/modules/2.6.27-11-generic/build/include/linux/kernel.h:18,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/cache.h:4,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/pda.h:7,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/current.h:19,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/processor.h:15,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/list.h:6,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:9,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/adriver.h:45,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.27-11-generic/build/include/linux/ratelimit.h: In function ‘ratelimit’:
/lib/modules/2.6.27-11-generic/build/include/linux/ratelimit.h:23: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.27-11-generic/build/include/linux/ratelimit.h:23: error: (Each undeclared identifier is reported only once
/lib/modules/2.6.27-11-generic/build/include/linux/ratelimit.h:23: error: for each function it appears in.)
In file included from /lib/modules/2.6.27-11-generic/build/include/asm/current.h:19,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/processor.h:15,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/list.h:6,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:9,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/adriver.h:45,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.27-11-generic/build/include/asm/pda.h: At top level:
/lib/modules/2.6.27-11-generic/build/include/asm/pda.h:40: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)
/lib/modules/2.6.27-11-generic/build/include/asm/pda.h:40: error: requested alignment is not a constant
In file included from /lib/modules/2.6.27-11-generic/build/include/asm/percpu.h:105,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/processor.h:19,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/list.h:6,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:9,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/adriver.h:45,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.27-11-generic/build/include/asm-generic/percpu.h:22: error: ‘CONFIG_NR_CPUS’ undeclared here (not in a function)
In file included from /lib/modules/2.6.27-11-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/list.h:6,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:9,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/adriver.h:45,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.27-11-generic/build/include/asm/processor.h:112: error: requested alignment is not a constant
In file included from /lib/modules/2.6.27-11-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/list.h:6,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:9,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/adriver.h:45,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.27-11-generic/build/include/asm/processor.h:152:1: warning: "cache_line_size" redefined
In file included from /lib/modules/2.6.27-11-generic/build/include/asm/pda.h:7,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/current.h:19,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/processor.h:15,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/list.h:6,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:9,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/adriver.h:45,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.27-11-generic/build/include/linux/cache.h:64:1: warning: this is the location of the previous definition
/lib/modules/2.6.27-11-generic/build/include/asm/processor.h: In function ‘load_cr3’:
/lib/modules/2.6.27-11-generic/build/include/asm/processor.h:184: error: ‘CONFIG_PAGE_OFFSETUL’ undeclared (first use in this function)
/lib/modules/2.6.27-11-generic/build/include/asm/processor.h: At top level:
/lib/modules/2.6.27-11-generic/build/include/asm/processor.h:233: error: requested alignment is not a constant
/lib/modules/2.6.27-11-generic/build/include/asm/processor.h:270: error: requested alignment is not a constant
/lib/modules/2.6.27-11-generic/build/include/asm/processor.h: In function ‘wbinvd_halt’:
/lib/modules/2.6.27-11-generic/build/include/asm/processor.h:751: warning: implicit declaration of function ‘halt’
In file included from /lib/modules/2.6.27-11-generic/build/include/linux/mmzone.h:16,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/gfp.h:4,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/kmod.h:22,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:13,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/adriver.h:45,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.27-11-generic/build/include/linux/nodemask.h: In function ‘__first_node’:
/lib/modules/2.6.27-11-generic/build/include/linux/nodemask.h:233: warning: implicit declaration of function ‘find_first_bit’
/lib/modules/2.6.27-11-generic/build/include/linux/nodemask.h: In function ‘__next_node’:
/lib/modules/2.6.27-11-generic/build/include/linux/nodemask.h:239: warning: implicit declaration of function ‘find_next_bit’
/lib/modules/2.6.27-11-generic/build/include/linux/nodemask.h: In function ‘__first_unset_node’:
/lib/modules/2.6.27-11-generic/build/include/linux/nodemask.h:257: warning: implicit declaration of function ‘find_first_zero_bit’
In file included from /lib/modules/2.6.27-11-generic/build/include/linux/gfp.h:4,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/kmod.h:22,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:13,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/adriver.h:45,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.27-11-generic/build/include/linux/mmzone.h: At top level:
/lib/modules/2.6.27-11-generic/build/include/linux/mmzone.h:75: error: requested alignment is not a constant
/lib/modules/2.6.27-11-generic/build/include/linux/mmzone.h:126: error: requested alignment is not a constant
/lib/modules/2.6.27-11-generic/build/include/linux/mmzone.h:335: error: requested alignment is not a constant
In file included from /lib/modules/2.6.27-11-generic/build/include/linux/smp.h:28,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/topology.h:33,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/mmzone.h:683,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/gfp.h:4,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/kmod.h:22,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:13,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/adriver.h:45,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.27-11-generic/build/include/asm/smp.h:161:1: warning: "cpu_physical_id" redefined
/lib/modules/2.6.27-11-generic/build/include/asm/smp.h:120:1: warning: this is the location of the previous definition
In file included from /lib/modules/2.6.27-11-generic/build/include/linux/elf.h:7,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:14,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/adriver.h:45,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.27-11-generic/build/include/asm/elf.h: In function ‘start_ia32_thread’:
/lib/modules/2.6.27-11-generic/build/include/asm/elf.h:153: warning: implicit declaration of function ‘load_gs_index’
In file included from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:21,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/adriver.h:45,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.27-11-generic/build/include/asm/module.h:70:2: error: #error unknown processor family
In file included from /lib/modules/2.6.27-11-generic/build/include/asm/hardirq_64.h:5,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/hardirq.h:4,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/hardirq.h:7,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/interrupt.h:11,
                 from hpetimer.c:26:
/lib/modules/2.6.27-11-generic/build/include/linux/irq.h: At top level:
/lib/modules/2.6.27-11-generic/build/include/linux/irq.h:179: error: requested alignment is not a constant
In file included from /lib/modules/2.6.27-11-generic/build/include/linux/sched.h:55,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/interrupt.h:12,
                 from hpetimer.c:26:
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:39:3: error: #error Invalid value of HZ.
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
In file included from /lib/modules/2.6.27-11-generic/build/include/linux/sched.h:77,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/interrupt.h:12,
                 from hpetimer.c:26:
/lib/modules/2.6.27-11-generic/build/include/linux/proportions.h: In function ‘prop_inc_percpu’:
/lib/modules/2.6.27-11-generic/build/include/linux/proportions.h:75: warning: implicit declaration of function ‘local_irq_save’
/lib/modules/2.6.27-11-generic/build/include/linux/proportions.h:77: warning: implicit declaration of function ‘local_irq_restore’
In file included from hpetimer.c:28:
/home/harel/Desktop/alsa-driver-1.0.9/include/sound/core.h:26:51: error: asm/semaphore.h: No such file or directory
hpetimer.c: In function ‘snd_hpet_open’:
hpetimer.c:41: warning: implicit declaration of function ‘hpet_register’
hpetimer.c:44: warning: implicit declaration of function ‘hpet_control’
hpetimer.c: In function ‘snd_hpet_close’:
hpetimer.c:51: warning: implicit declaration of function ‘hpet_unregister’
make[1]: *** [hpetimer.o] Error 1
make[1]: Leaving directory `/home/harel/Desktop/alsa-driver-1.0.9/acore'
make: *** [compile] Error 1
harel@ubuntu:~/Desktop/alsa-driver-1.0.9$ 
harel@ubuntu:~/Desktop/alsa-driver-1.0.9$ 


```

---

### Post by knlgSeekr on 2009-03-04
> **crapple said:**
> this is what happens when I try and install. (I have geforce 9300ge but the concept should be the same) I follow the steps and this is my output from terminal from when I started until the first error which happens when I run sudo make```
harel@ubuntu:~$ cd /home/harel/Desktop/alsa-driver-1.0.9
harel@ubuntu:~/Desktop/alsa-driver-1.0.9$ sudo ./configure
checking for gcc... gcc
checking for C compiler default output... a.out
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
checking for current directory... /home/harel/Desktop/alsa-driver-1.0.9
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.27-11-generic/build
checking for directory with kernel build... 
checking for kernel version... 0.0.0
checking for GCC version... ./configure: eval: line 3568: syntax error near unexpected token `)'
./configure: eval: line 3568: `my_compiler_version=4.3.2-1ubuntu12)'
Kernel compiler:  Used compiler: gcc (Ubuntu 4.3.2-1ubuntu12) 4.3.2

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

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
checking for kernel linux/devfs_fs_kernel.h... "no"
checking for kernel linux/highmem.h... "yes"
checking for kernel linux/workqueue.h... "yes"
checking for kernel linux/dma-mapping.h... "yes"
checking for kernel asm/hw_irq.h... "yes"
checking for kernel linux/device.h... "yes"
checking for kernel linux/jiffies.h... "yes"
checking for kernel linux/compat.h... "yes"
checking for kernel linux/adb.h... "yes"
checking for kernel linux/cuda.h... "yes"
checking for kernel linux/pmu.h... "yes"
checking for kernel linux/moduleparam.h... "yes"
checking for kernel linux/syscalls.h... "yes"
checking for kernel linux/firmware.h... "yes"
checking for exported symbol dump_stack... grep: /lib/modules/2.6.27-11-generic/build/kernel/ksyms.c: No such file or directory
"no"
checking for kernel module symbol versions... "yes"
checking for PCI support in kernel... "yes"
checking for I2C driver in kernel... module
checking for firmware loader... yes
checking for directory to store kernel modules... /lib/modules/0.0.0/misc
checking for verbose printk... on
checking for debug level... none
checking for processor type... x86_64
checking for SMP... "yes"
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... "no"
checking for Kernel ISA-PnP module support... "no"
checking for strlcpy... "no"
checking for snprintf... "no"
checking for vsnprintf... "no"
checking for scnprintf... "no"
checking for sscanf... "no"
checking for vmalloc_to_page... "no"
checking for old kmod... "yes"
checking for PDE... "no"
checking for pci_set_consistent_dma_mask... "no"
checking for pci_dev_present... "no"
checking for msleep... "no"
checking for tty->count is the atomic type... "no"
checking for io_remap_pfn_range... "no"
checking for new io_remap_page_range... "no"
checking for kcalloc... "no"
checking for saved_config_space in pci_dev... "no"
checking for old kill_fasync... "no"
checking for dma_addr_t... "no"
checking for MUTEX macros... "no"
checking for driver version... 1.0.9
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for RTC callback support in kernel... "no"
checking for HPET support... "yes"
checking for Procfs support... "yes"
checking for USB support... "yes"
checking for PC-Speaker hook... "no"
checking for kernel PCMCIA
checking for PCMCIA support... "yes"
checking for PC9800 support in kernel... "no"
checking for parallel port support... "yes"
checking for which soundcards to compile driver for... all
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/config.h
config.status: include/config.h is unchanged
config.status: creating include/config1.h
config.status: include/config1.h is unchanged
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...
harel@ubuntu:~/Desktop/alsa-driver-1.0.9$ sudo make
make[1]: Entering directory `/home/harel/Desktop/alsa-driver-1.0.9/acore'
gcc -D__KERNEL__ -DMODULE=1 -I/home/harel/Desktop/alsa-driver-1.0.9/include  -I/lib/modules/2.6.27-11-generic/build/include -O2 -mno-red-zone -mcmodel=kernel -fno-reorder-blocks -fno-strength-reduce -finline-limit=2000 -D__SMP__ -DCONFIG_SMP -DLINUX -Wall -Wstrict-prototypes -fomit-frame-pointer -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -pipe -DALSA_BUILD -nostdinc -iwithprefix include -DMODVERSIONS -include /lib/modules/2.6.27-11-generic/build/include/linux/modversions.h  -DKBUILD_BASENAME=hpetimer   -c -o hpetimer.o hpetimer.c
cc1: error: /lib/modules/2.6.27-11-generic/build/include/linux/modversions.h: No such file or directory
In file included from hpetimer.c:22:
/home/harel/Desktop/alsa-driver-1.0.9/include/sound/driver.h:29:26: error: linux/config.h: No such file or directory
In file included from /lib/modules/2.6.27-11-generic/build/include/linux/kernel.h:18,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/cache.h:4,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/pda.h:7,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/current.h:19,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/processor.h:15,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/list.h:6,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:9,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/adriver.h:45,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.27-11-generic/build/include/linux/ratelimit.h: In function ‘ratelimit’:
/lib/modules/2.6.27-11-generic/build/include/linux/ratelimit.h:23: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.27-11-generic/build/include/linux/ratelimit.h:23: error: (Each undeclared identifier is reported only once
/lib/modules/2.6.27-11-generic/build/include/linux/ratelimit.h:23: error: for each function it appears in.)
In file included from /lib/modules/2.6.27-11-generic/build/include/asm/current.h:19,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/processor.h:15,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/list.h:6,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:9,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/adriver.h:45,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.27-11-generic/build/include/asm/pda.h: At top level:
/lib/modules/2.6.27-11-generic/build/include/asm/pda.h:40: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)
/lib/modules/2.6.27-11-generic/build/include/asm/pda.h:40: error: requested alignment is not a constant
In file included from /lib/modules/2.6.27-11-generic/build/include/asm/percpu.h:105,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/processor.h:19,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/list.h:6,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:9,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/adriver.h:45,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.27-11-generic/build/include/asm-generic/percpu.h:22: error: ‘CONFIG_NR_CPUS’ undeclared here (not in a function)
In file included from /lib/modules/2.6.27-11-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/list.h:6,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:9,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/adriver.h:45,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.27-11-generic/build/include/asm/processor.h:112: error: requested alignment is not a constant
In file included from /lib/modules/2.6.27-11-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/list.h:6,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:9,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/adriver.h:45,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.27-11-generic/build/include/asm/processor.h:152:1: warning: "cache_line_size" redefined
In file included from /lib/modules/2.6.27-11-generic/build/include/asm/pda.h:7,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/current.h:19,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/processor.h:15,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/list.h:6,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:9,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/adriver.h:45,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.27-11-generic/build/include/linux/cache.h:64:1: warning: this is the location of the previous definition
/lib/modules/2.6.27-11-generic/build/include/asm/processor.h: In function ‘load_cr3’:
/lib/modules/2.6.27-11-generic/build/include/asm/processor.h:184: error: ‘CONFIG_PAGE_OFFSETUL’ undeclared (first use in this function)
/lib/modules/2.6.27-11-generic/build/include/asm/processor.h: At top level:
/lib/modules/2.6.27-11-generic/build/include/asm/processor.h:233: error: requested alignment is not a constant
/lib/modules/2.6.27-11-generic/build/include/asm/processor.h:270: error: requested alignment is not a constant
/lib/modules/2.6.27-11-generic/build/include/asm/processor.h: In function ‘wbinvd_halt’:
/lib/modules/2.6.27-11-generic/build/include/asm/processor.h:751: warning: implicit declaration of function ‘halt’
In file included from /lib/modules/2.6.27-11-generic/build/include/linux/mmzone.h:16,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/gfp.h:4,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/kmod.h:22,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:13,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/adriver.h:45,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.27-11-generic/build/include/linux/nodemask.h: In function ‘__first_node’:
/lib/modules/2.6.27-11-generic/build/include/linux/nodemask.h:233: warning: implicit declaration of function ‘find_first_bit’
/lib/modules/2.6.27-11-generic/build/include/linux/nodemask.h: In function ‘__next_node’:
/lib/modules/2.6.27-11-generic/build/include/linux/nodemask.h:239: warning: implicit declaration of function ‘find_next_bit’
/lib/modules/2.6.27-11-generic/build/include/linux/nodemask.h: In function ‘__first_unset_node’:
/lib/modules/2.6.27-11-generic/build/include/linux/nodemask.h:257: warning: implicit declaration of function ‘find_first_zero_bit’
In file included from /lib/modules/2.6.27-11-generic/build/include/linux/gfp.h:4,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/kmod.h:22,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:13,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/adriver.h:45,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.27-11-generic/build/include/linux/mmzone.h: At top level:
/lib/modules/2.6.27-11-generic/build/include/linux/mmzone.h:75: error: requested alignment is not a constant
/lib/modules/2.6.27-11-generic/build/include/linux/mmzone.h:126: error: requested alignment is not a constant
/lib/modules/2.6.27-11-generic/build/include/linux/mmzone.h:335: error: requested alignment is not a constant
In file included from /lib/modules/2.6.27-11-generic/build/include/linux/smp.h:28,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/topology.h:33,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/mmzone.h:683,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/gfp.h:4,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/kmod.h:22,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:13,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/adriver.h:45,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.27-11-generic/build/include/asm/smp.h:161:1: warning: "cpu_physical_id" redefined
/lib/modules/2.6.27-11-generic/build/include/asm/smp.h:120:1: warning: this is the location of the previous definition
In file included from /lib/modules/2.6.27-11-generic/build/include/linux/elf.h:7,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:14,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/adriver.h:45,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.27-11-generic/build/include/asm/elf.h: In function ‘start_ia32_thread’:
/lib/modules/2.6.27-11-generic/build/include/asm/elf.h:153: warning: implicit declaration of function ‘load_gs_index’
In file included from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:21,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/adriver.h:45,
                 from /home/harel/Desktop/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.27-11-generic/build/include/asm/module.h:70:2: error: #error unknown processor family
In file included from /lib/modules/2.6.27-11-generic/build/include/asm/hardirq_64.h:5,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/hardirq.h:4,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/hardirq.h:7,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/interrupt.h:11,
                 from hpetimer.c:26:
/lib/modules/2.6.27-11-generic/build/include/linux/irq.h: At top level:
/lib/modules/2.6.27-11-generic/build/include/linux/irq.h:179: error: requested alignment is not a constant
In file included from /lib/modules/2.6.27-11-generic/build/include/linux/sched.h:55,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/interrupt.h:12,
                 from hpetimer.c:26:
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:39:3: error: #error Invalid value of HZ.
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
In file included from /lib/modules/2.6.27-11-generic/build/include/linux/sched.h:77,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/interrupt.h:12,
                 from hpetimer.c:26:
/lib/modules/2.6.27-11-generic/build/include/linux/proportions.h: In function ‘prop_inc_percpu’:
/lib/modules/2.6.27-11-generic/build/include/linux/proportions.h:75: warning: implicit declaration of function ‘local_irq_save’
/lib/modules/2.6.27-11-generic/build/include/linux/proportions.h:77: warning: implicit declaration of function ‘local_irq_restore’
In file included from hpetimer.c:28:
/home/harel/Desktop/alsa-driver-1.0.9/include/sound/core.h:26:51: error: asm/semaphore.h: No such file or directory
hpetimer.c: In function ‘snd_hpet_open’:
hpetimer.c:41: warning: implicit declaration of function ‘hpet_register’
hpetimer.c:44: warning: implicit declaration of function ‘hpet_control’
hpetimer.c: In function ‘snd_hpet_close’:
hpetimer.c:51: warning: implicit declaration of function ‘hpet_unregister’
make[1]: *** [hpetimer.o] Error 1
make[1]: Leaving directory `/home/harel/Desktop/alsa-driver-1.0.9/acore'
make: *** [compile] Error 1
harel@ubuntu:~/Desktop/alsa-driver-1.0.9$ 
harel@ubuntu:~/Desktop/alsa-driver-1.0.9$ 


```

i would try running this script: [http://ubuntuforums.org/showthread.php?p=6589810#post6589810]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810") it should be easier to upgrade ALSA by following these instructions.. i just did it manually because i didn't happen to find that thread until after i had done it

---

### Post by tuvw014 on 2009-03-04
[nike tn](http://www.nike-max-tn.com)
[nike max](http://www.nike-max-tn.com)
[nike chaussures](http://www.nike-max-tn.com)
[http://www.nike-max-tn.com](http://www.nike-max-tn.com) nike tn/nike max/nike chaussures[puma CAT](http://www.pumafr.com)

---

### Post by TNA5000 on 2009-03-07
Wanted to say a big thanks to knlgSeekr for his great tutorial and explanation.

I have an nvidia 8300 with HDMI and using his explanation i was able to get sound working over HDMI.

thanks again.

---

### Post by knlgSeekr on 2009-03-10
> **TNA5000 said:**
> Wanted to say a big thanks to knlgSeekr for his great tutorial and explanation.

I have an nvidia 8300 with HDMI and using his explanation i was able to get sound working over HDMI.

thanks again.
Glad i was able to help :D
I am curious to know if you are getting firefox audio through HDMI as well. for some reason, anything playing through firefox like youtube etc will only play through my pc speakers. i have asked about this annoyance but no one seems to know how to fix it

---

### Post by TNA5000 on 2009-03-11
> **knlgSeekr said:**
> Glad i was able to help :D
I am curious to know if you are getting firefox audio through HDMI as well. for some reason, anything playing through firefox like youtube etc will only play through my pc speakers. i have asked about this annoyance but no one seems to know how to fix it

Yes, now that i have installed flash, i am indeed not getting any sound out of it. I did notice that i have no sound whatsoever from VLC as well. Other media players work just fine, but not VLC... i do like the stability of pulseaudio (back when i had it on my laptop), so i'm thinking that i might go back to it, if there is a way to pass my audio over my regular rca audio outputs (or maybe even spdif if its not too difficult). The last thing i noticed is that when one audio stream is playing, any other audio stream will not play at the same time (like notifications form pidgin).

Let me know if you are finding anything else about this issue, i'd still prefer to use audio over HDMI.

---

### Post by knlgSeekr on 2009-06-19
for anyone else out there running a similar setup.. i have noticed that certain updates will wipe out my HDMI settings so i have narrowed the fix down, and it works for me every time with no issues.

this is all that needs to be done:

i downloaded Alsa 1.0.19.tar.bz2 from alsa-project.org & installed it with this script

after extracting it to my documents, i right clicked on the folder & clicked properties to get it's path.. which in my case was 
/home/MYUSERNAME/Documents/Downloads/alsa-driver-1.0.19

so i ran:

[COLOR="Navy"]cd /home/MYUSERNAME/Documents/Downloads/alsa-driver-1.0.19
sudo ./configure
sudo make
sudo make install
sudo reboot[/COLOR]

*it will work even without rebooting*

after the reboot, i ran alsamixer which interestingly enough still came up as v1.0.17, the difference being that now there was an additional IEC958 graph, labeled IEC958 1.. and underneath it, instead of 00 like the other 2, it was marked MM.. which i remembered means a muted device.

so i went back IEC953 switch menu again by double clicking on the volume control icon & clicking on preferences.. and sure enough, there was a third IEC953 there as well. i put a check in the box next to it, clicked on the swithches tab & put a check mark in it there as well.

then i ran aplay -l & got this!

[COLOR="Navy"]card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0[/COLOR]

i went into system / preferences / sound again and now there was an option for HDA NVidia NVIDIA HDMI (ALSA) which i of course selected for all but sound capture (ALSA - Advanced Linux Sound Architechture) and Device under default mixer tracks (HDA NVidia (Alsa mixer))

follow this procedure and your HDMI should be recognized & working ;)

---

### Post by couzin2000 on 2009-07-09
> **TNA5000 said:**
> Yes, now that i have installed flash, i am indeed not getting any sound out of it. I did notice that i have no sound whatsoever from VLC as well. Other media players work just fine, but not VLC... i do like the stability of pulseaudio (back when i had it on my laptop), so i'm thinking that i might go back to it, if there is a way to pass my audio over my regular rca audio outputs (or maybe even spdif if its not too difficult). The last thing i noticed is that when one audio stream is playing, any other audio stream will not play at the same time (like notifications form pidgin).

Let me know if you are finding anything else about this issue, i'd still prefer to use audio over HDMI.

It's quite possible that some programs route the audio to a specific driver, or over a specific audio path. You should check to see if you find some options for audio in Firefox when you type [FONT="Courier New"]_about:config_[/FONT] in the adress bar. For VLC, there are settings in Audio, you should look at those. Pidgin must have the same kind of settings as well, although I'm not familiar with its setup system. Take a look and post back, I'm real curious about this.

---

### Post by couzin2000 on 2009-08-09
I've looked up one of your posted links, and I was able to add the new repos to my apt-get. Since then, I simply downloaded and installed the upgrades, including the new version of Alsa 1.0.19, and there it is - as expected, the HDMI works. Simple but effective.

Thanks!

---

### Post by nature on 2009-11-13
Well to be honest im totally new to ubuntu. But i tried to follow your steps on how to get sound trough the hdmi port, sadly i werent as sucsessfull as you. As we speak i got no sound at all (not even on the laptop speakers.)

And nothing shows up in the sound prefrences menu either under hardware. Im running Ubuntu 9.10 Karmic Koala Not sure were i stepped wrong so guess its nothing easy for you to help me with. But just posting incase anyone have any idea what might be the cause.

---

