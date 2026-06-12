---
title: "[SOLVED] NVIDIA driver kernel problem"
date: 2007-12-24
forum: Multimedia &amp; Video
---

### Post by al_sh on 2007-12-24
[Driver version]: 100.14.19

After system reboot X fails to start: "
```
Error: API mismatch: this NVIDIA driver component has version 100.14.11, but the NVIDIA kernel module's version does not match.
```
Reinstallation - helps & nothing more. Pls help to fix it.

Btw:
```
 Linux NSA 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux
```

---

### Post by tgilber1 on 2007-12-24
> **al_sh said:**
> [Driver version]: 100.14.19

After system reboot X fails to start: "
```
Error: API mismatch: this NVIDIA driver component has version 100.14.11, but the NVIDIA kernel module's version does not match.
```
Reinstallation - helps & nothing more. Pls help to fix it.

Btw:
```
 Linux NSA 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux
```


This error message means that the kernel module was compiled under another version than the one that's running.  Hence, you either need to rebuild the kernel module, i.e. you need to rerun the Nvidia installation binary

_Nvidia Driver_
[http://us.download.nvidia.com/XFree86/Linux-x86/169.07/NVIDIA-Linux-x86-169.07-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/169.07/NVIDIA-Linux-x86-169.07-pkg1.run)

_Documentation - Chapter 8_
[http://us.download.nvidia.com/XFree86/Linux-x86/169.07/README/chapter-08.html](http://us.download.nvidia.com/XFree86/Linux-x86/169.07/README/chapter-08.html)

_Excerpt from ch8_
	

I just upgraded my kernel, and now the NVIDIA kernel module will not load.
	

The kernel interface layer of the NVIDIA kernel module must be compiled specifically for the configuration and version of your kernel. If you upgrade your kernel, then the simplest solution is to reinstall the driver.

ADVANCED: You can install the NVIDIA kernel module for a non running kernel (for example: in the situation where you just built and installed a new kernel, but have not rebooted yet) with a command line such as this:

    # sh NVIDIA-Linux-x86-169.07-pkg1.run --kernel-name='KERNEL_NAME'

Where 'KERNEL_NAME' is what uname -r would report if the target kernel were running.
	

My X server fails to start, and my X log file contains the error:

(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!

---

### Post by al_sh on 2007-12-25
I've downloaded & installed version 169.07. Driver has compiled kernel module... successful installation... '/etc/init.d/gdm restart'... X server successful start... But after system reboot X server fails to start.
my X log file contains this error:
```

(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
```
The same problem... As if driver saves compiled kernel module in temporary folder after installation.

P.S. One more problem: "Documentation. Chapter 5. Listing of Installed Components - ...A kernel module (/lib/modules/`uname -r`/video/nvidia.o or /lib/modules/`uname -r`/kernel/drivers/video/nvidia.o)..." But I have : /lib/modules/2.6.20-15-generic/kernel/drivers/video/nvidia  nvidiafb.ko

---

### Post by oscarsfriend on 2007-12-25
Hi,

Take a look at this thread (post #5.): [http://ubuntuforums.org/showthread.php?t=630412](http://ubuntuforums.org/showthread.php?t=630412) it may fix your problem.

---

### Post by tgilber1 on 2007-12-25
> **al_sh said:**
> I've downloaded & installed version 169.07. Driver has compiled kernel module... successful installation... '/etc/init.d/gdm restart'... X server successful start... But after system reboot X server fails to start.
my X log file contains this error:
```

(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
```
The same problem... As if driver saves compiled kernel module in temporary folder after installation.

P.S. One more problem: "Documentation. Chapter 5. Listing of Installed Components - ...A kernel module (/lib/modules/`uname -r`/video/nvidia.o or /lib/modules/`uname -r`/kernel/drivers/video/nvidia.o)..." But I have : /lib/modules/2.6.20-15-generic/kernel/drivers/video/nvidia  nvidiafb.ko


Ok, I remember now.  After running the nvidia setup, I had the same thing happen.  You're right, it was placed in a temporary directory, the name of it escapes me.  What I did is written below.

1.  Run the nvidia setup program.  
2.  After the setup program compile the kernel object, run modprobe -l nvidia to to find the location of the driver.
3.  Copy the nvidia.ko to the correct directory which /lib/modules/`uname -r`/kernel/drivers using the following commmand 

copy exactly as is - need backticks for modprobe and uname commands

sudo cp `modprobe -l nvidia` /lib/modules/`uname -r`/kernel/drivers/video/

4.  Finally restart gdm, using "sudo /etc/init.d/gdm restart"

Have you tried using the nvidia and restricted drivers that come with Ubuntu?

---

### Post by al_sh on 2007-12-27
Thank you all.
Solution : 
```
/etc/default/linux-restricted-modules-common:
DISABLED_MODULES=""
 'modprobe -l | grep "nvidia"
``` 
X server boots normal now.

---

