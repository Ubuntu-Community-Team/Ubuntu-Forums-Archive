---
title: "Can't install drivers for Nvidia on board video"
date: 2009-03-25
forum: Multimedia Software
---

### Post by Twig E. Pottox on 2009-03-25
Still Trying to load n-Vidia  (on board video chip) video drivers repeatedly and having no luck.  I've invested many hours, going from 64 bit to 32 downloading various drivers etc. and generally doing nothing that works. From the forums I cannot tell for sure if there  is a work around that works for this particular set up. I don't need gamer video, but would like to have decent resolution  1024/768 and refresh rate above 60.  If this set up doesn't work or have drivers          for Linux what low / medium end cards would easily install in ubuntu.  

my machine is: ECS Mobo GF7050VT-M V1.0, Intel core 2 duo E73004,  Gb ram,  430 W HDD, Dual boot W/XP (dual maxtor ATA HDD) on board Geforce 7050/nForce610i video.

I followed what had seemed to work for others on the forums:

Removed nVidia drivers in synaptic  - downloaded  NVIDIA-Linux-x86-180.29-pkg1.run -  
killed  gdm  - ran the nvidia file and  after agreeing to terms got  ( from my  - /var/log/nvidia-installer.log) : 

> quote:

 “Using: nvidia-installer ncurses user interface 
-> License accepted. 
-> Installing NVIDIA driver version 180.29. 
-> No precompiled kernel interface was found to match your kernel; would you li 
   ke the installer to attempt to download a kernel interface for your kernel f 
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes) 
-> No matching precompiled kernel interface was found on the NVIDIA ftp site; 
   this means that the installer will need to compile a kernel interface for 
   your kernel. 
-> Performing CC sanity check with CC="cc". 
-> Performing CC version check with CC="cc". 
-> Kernel source path: '/lib/modules/2.6.27-11-generic/build' 
-> Kernel output path: '/lib/modules/2.6.27-11-generic/build' 
-> Performing rivafb check. 
-> Performing nvidiafb check. 
-> Performing Xen check. 
-> Cleaning kernel module build directory. 
   executing: 'cd ./usr/src/nv; make clean'... 
-> Building kernel module: 
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.27-11-gener 
   ic/build SYSOUT=/lib/modules/2.6.27-11-generic/build'... 
   NVIDIA: calling KBUILD... 
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.27-11-generic/build SUBDIRS 
   =/tmp/selfgz8718/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv modules 
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\ 
   	echo;								\ 
   	echo "  ERROR: Kernel configuration is invalid.";		\ 
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis 
   sing.";	\ 
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it 
   .";	\ 
   	echo;								\ 
   	/bin/false) 
   mkdir -p /tmp/selfgz8718/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv/.tmp_versio 
   ns ; rm -f /tmp/selfgz8718/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv/.tmp_vers 
   ions/*Using: nvidia-installer ncurses user interface 
-> License accepted. 
-> Installing NVIDIA driver version 180.29. 
-> No precompiled kernel interface was found to match your kernel; would you li 
   ke the installer to attempt to download a kernel interface for your kernel f 
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes) 
-> No matching precompiled kernel interface was found on the NVIDIA ftp site; 
   this means that the installer will need to compile a kernel interface for 
   your kernel. 
-> Performing CC sanity check with CC="cc". 
-> Performing CC version check with CC="cc". 
-> Kernel source path: '/lib/modules/2.6.27-11-generic/build' 
-> Kernel output path: '/lib/modules/2.6.27-11-generic/build' 
-> Performing rivafb check. 
-> Performing nvidiafb check. 
-> Performing Xen check. 
-> Cleaning kernel module build directory. 
   executing: 'cd ./usr/src/nv; make clean'... 
-> Building kernel module: 
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.27-11-gener 
   ic/build SYSOUT=/lib/modules/2.6.27-11-generic/build'... 
   NVIDIA: calling KBUILD... 
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.27-11-generic/build SUBDIRS 
   =/tmp/selfgz8718/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv modules 
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\ 
   	echo;								\ 
   	echo "  ERROR: Kernel configuration is invalid.";		\ 
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis 
   sing.";	\ 
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it 
   .";	\ 
   	echo;								\ 
   	/bin/false) 
   mkdir -p /tmp/selfgz8718/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv/.tmp_versio 
   ns ; rm -f /tmp/selfgz8718/NVIDIA-Linux-x86-180.29-pkg1/usr/src/nv/.tmp_vers 
   ions/*


 I removed the middle of the file to keep this thread from getting too huge. let me know if the whole file is needed

after compilation complete I got the following  Ending portion on /var/log/nvidia-installer.log: 



 > ld -r -m elf_i386  --build-id -o /tmp/selfgz8718/NVIDIA-Linux-x86-180.29-p 
   kg1/usr/src/nv/nvidia.ko /tmp/selfgz8718/NVIDIA-Linux-x86-180.29-pkg1/usr/sr 
   c/nv/nvidia.o /tmp/selfgz8718/c/usr/src/nv/nvidia 
   .mod.o 
   NVIDIA: left KBUILD. 
-> done. 
-> Kernel module compilation complete. 
ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most 
       frequently when this kernel module was built against the wrong or 
       improperly configured kernel sources, with a version of gcc that differs 
       from the one used to build the target kernel, or if a driver such as 
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from 
       obtaining ownership of the NVIDIA graphics device(s), or NVIDIA GPU 
       installed in this system is not supported by this NVIDIA Linux graphics 
       driver release. 
       
       Please see the log entries 'Kernel module load error' and 'Kernel 
       messages' at the end of the file '/var/log/nvidia-installer.log' for 
       more information. 
-> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko': 
   -1 No such device 
-> Kernel messages: 
   [   49.967791] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync* 
   [   49.967799] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync* 
   [   49.967808] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync* 
   [   49.967816] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync* 
   [   49.967821] cx88[0]/1: IRQ loop detected, disabling interrupts 
   [   49.970628] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync* 
   [   49.980521] cx88[0]: irq aud [0x1101] dn_risci1* dnf_of dn_sync* 
   [  130.592169] ppdev0: registered pardevice 
   [  130.640120] ppdev0: unregistered pardevice 
   [  130.657704] ppdev0: registered pardevice 
   [  130.704016] ppdev0: unregistered pardevice 
   [  130.728336] ppdev0: registered pardevice 
   [  130.776190] ppdev0: unregistered pardevice 
   [ 1775.793703] NVRM: This PCI I/O region assigned to your NVIDIA device is 
   invalid: 
   [ 1775.793706] NVRM: BAR1 is 0M @ 0x00000000 (PCI:0000:10.0) 
   [ 1775.793711] NVRM: The system BIOS may have misconfigured your graphics 
   card. 
   [ 1775.794920] nvidia: probe of 0000:00:10.0 failed with error -1 
   [ 1775.795266] NVRM: The NVIDIA probe routine failed for 1 device(s). 
   [ 1775.795269] NVRM: None of the NVIDIA graphics adapters were initialized! 
   [ 2430.716637] NVRM: This PCI I/O region assigned to your NVIDIA device is 
   invalid: 
   [ 2430.716639] NVRM: BAR1 is 0M @ 0x00000000 (PCI:0000:10.0) 
   [ 2430.716643] NVRM: The system BIOS may have misconfigured your graphics 
   card. 
   [ 2430.716649] nvidia: probe of 0000:00:10.0 failed with error -1 
   [ 2430.716668] NVRM: The NVIDIA probe routine failed for 1 device(s). 
   [ 2430.716669] NVRM: None of the NVIDIA graphics adapters were initialized! 
ERROR: Installation has failed.  Please see the file 
       'c/var/log/nvidia-installer.log' for details.  You may find suggestions 
       on fixing installation problems in the README available on the Linux 
       driver download page at [www.nvidia.com](www.nvidia.com).
any / all help would be appreciated

---

### Post by wbee on 2009-03-25
Hello,

I would tell you my nvidia driver story,but it would just upset us both more.:-)

Two suggestions:

1.Report it to launchpad. There are a host of bug reports for nvidia stuff,and my guess is they are working on it. Yes,I appreciate the kindness of volunteers.

2. Google "envy+nvidia" and read it.  Evny is in the Synaptic(spelling?) program. Uninstall what you have,and let it take a crack at it.

2a. Fingers crossed for luck. So far,the envy driver is holding. The 8.10 hardware manager offered me three choices. Neither the recommended one nor the two digit one would load,but the third one did,and it led to the same issues you are having,and spread to my tvtime software.

The envy loaded the correct driver,which the hardware manager would not.(Look at the check boxes in Synaptic.) That leads me to believe the bug might originate in the installer function,but that is just a guess.

((Edit. The Envy page says the version that works with 8.10 unloads the old drivers,but I took those out anyway,in case the installer was buggy and his might not remove those.  sudo envy --uninstall-all ))

Good luck.

------------

W

---

### Post by Vadi on 2009-03-25
Hi,

Try using the 173 series - they started dropping support for older cards and only the official nvidia installer will tell you that your gpu is too old (the rest just die / crash. I filed a report about it somewhere).

---

### Post by norwoods on 2009-03-25
i update to the latest nvidia proprietary prereleases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.41 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using System-->Administration-->Synaptic Package Manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev
for a fresh install, you might also want or need:
jockey-common
jockey-gtk or jockey-kde
nvidia-settings
nvidia-xconfig

---

### Post by Twig E. Pottox on 2009-03-25
thanks for the answers unfortunately nothing works.  Ive tried two different video cards geforece 9400 and 9800 and the one built into the motherboard 7050 / 610i.  and i end upu with the same error. there  must be a way, anybody aable to make sense out ogf the installation log in my original post?

wbee;  envy is neat but seems to do the same as I did in the Terminal.  it still hangs and gives me an error. iin the terminaal / nvidias installer it instructs me to look in the nvidia installer log which I copied to my initial post.

vadi; thanks for the advice but I've tried 173, 177, 180, whatever the nvidia site tried to buiild, etc etc etc. they all hang and give an error.

norwoods, thanks but is the 180 driver going to be different than that ive downloaded at the geforce driver  site?  plus I'm not sure how to add that or any repository

---

### Post by norwoods on 2009-03-25
> **Twig E. Pottox said:**
> 

norwoods, thanks but is the 180 driver going to be different than that ive downloaded at the geforce driver  site?  plus I'm not sure how to add that or any repository

the 180.41 driver is newer and different from 180.29

to add the repository, open System-->Administration-->Synaptic Package Manager
open Settings-->Repositories
click tab for Third-Party Software
click +Add button
copy and paste what is inside the double quotes into the APT line: box "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/"
click +Add Source
click Close
click Reload

---

### Post by Twig E. Pottox on 2009-03-26
thanks norwoods but despite your help I think there is something rotten with my install, synaptic failed to load the files needed:
> Failed to fetch [http://www.avenard.org/files/ubuntu-repos/dists/release/deb/http://www.avenard.org/files/ubuntu-repos/binary-i386/Packages.gz](http://www.avenard.org/files/ubuntu-repos/dists/release/deb/http://www.avenard.org/files/ubuntu-repos/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://www.avenard.org/files/ubuntu-repos/dists/release/deb/release/deb/binary-i386/Packages.gz](http://www.avenard.org/files/ubuntu-repos/dists/release/deb/release/deb/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://www.avenard.org/files/ubuntu-repos/dists/release/deb/release//binary-i386/Packages.gz](http://www.avenard.org/files/ubuntu-repos/dists/release/deb/release//binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.[QUOTE][/QUOTE

additionally, in the pursuit of these drivers I have now lost audio, recovery attempts have failed,  the envy program has disapeared and will not reload.  I believe this install has had too much trial and error and is beginning to unrwavel, time to wipe and start over and hope some of these work arounds  will work then.

---

