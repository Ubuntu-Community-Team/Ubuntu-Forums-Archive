---
title: "NVIDIA taints kernel"
date: 2009-01-14
forum: Multimedia Software
---

### Post by oygle on 2009-01-14
Have noticed this in syslog

> Jan 14 10:37:13  kernel: [   14.650109] nvidia: module license **'NVIDIA' taints kernel**.
Jan 14 10:37:13  kernel: [   14.910344] usbcore: registered new interface driver libusual
Jan 14 10:37:13  kernel: [   15.042537] Initializing USB Mass Storage driver...
Jan 14 10:37:13  kernel: [   15.059990] usb-storage: probe of 2-1:1.0 failed with error -5
Jan 14 10:37:13  kernel: [   15.067568] usb-storage: probe of 2-1:1.1 failed with error -5
Jan 14 10:37:13  kernel: [   15.086317] usb-storage: probe of 2-1:1.2 failed with error -5
Jan 14 10:37:13  kernel: [   15.125819] scsi9 : SCSI emulation for USB Mass Storage devices
Jan 14 10:37:13  kernel: [   15.131956] usbcore: registered new interface driver usb-storage
Jan 14 10:37:13  kernel: [   15.132011] USB Mass Storage support registered.
Jan 14 10:37:13  kernel: [   15.333597] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 14 10:37:13  kernel: [   15.451404] nvidia 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 14 10:37:13  kernel: [   15.459866] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.12  Thu Jul 17 18:11:36 PDT 2008

The output of ```
sudo aptitude search nvidia
```

> 
i A nvidia-173-kernel-source        - NVIDIA binary kernel module source        
i A nvidia-173-modaliases           - Modaliases for the NVIDIA binary X.Org dri
p   nvidia-177-kernel-source        - NVIDIA binary kernel module source        
i A nvidia-177-modaliases           - Modaliases for the NVIDIA binary X.Org dri
p   nvidia-180-kernel-source        - NVIDIA binary kernel module source        
p   nvidia-180-modaliases           - Modaliases for the NVIDIA binary X.Org dri
p   nvidia-71-kernel-source         - NVIDIA binary kernel module source        
i A nvidia-71-modaliases            - Modaliases for the NVIDIA binary X.Org dri
p   nvidia-96-kernel-source         - NVIDIA binary kernel module source        
i A nvidia-96-modaliases            - Modaliases for the NVIDIA binary X.Org dri
p   nvidia-cg-toolkit               - NVIDIA Cg Toolkit Installer               
i A nvidia-common                   - Find obsolete NVIDIA drivers              
v   nvidia-glx                      -                                           
i   nvidia-glx-173                  - NVIDIA binary Xorg driver                 
p   nvidia-glx-173-dev              - NVIDIA binary Xorg driver development file
p   nvidia-glx-177                  - NVIDIA binary Xorg driver                 
p   nvidia-glx-177-dev              - NVIDIA binary Xorg driver development file
p   nvidia-glx-180                  - NVIDIA binary Xorg driver                 
p   nvidia-glx-180-dev              - NVIDIA binary Xorg driver development file
p   nvidia-glx-71                   - NVIDIA binary Xorg driver                 
p   nvidia-glx-71-dev               - NVIDIA binary Xorg driver development file
p   nvidia-glx-96                   - NVIDIA binary Xorg driver                 
p   nvidia-glx-96-dev               - NVIDIA binary Xorg driver development file
v   nvidia-glx-dev                  -                                           
c   nvidia-glx-new                  - NVIDIA binary XFree86 4.x/X.Org 'new' driv
v   nvidia-kernel-169.12            -                                           
v   nvidia-kernel-71.86.04          -                                           
v   nvidia-kernel-96.43.05          -                                           
i A nvidia-kernel-common            - NVIDIA binary kernel module common files  
v   nvidia-kernel-source            -                                           
i A nvidia-settings                 - Tool of configuring the NVIDIA graphics dr
p   nvidia-xconfig                  - The NVIDIA X Configuration Tool           
$ 

I have upgraded from Hardy to Intrepid, and saw a post where that caused some conflicts with NVIDIA. Do I have to change anything ?

Oygle

---

### Post by ushimitsudoki on 2009-01-14
No, this is normal when using closed binary drivers.

Basically it's telling you that since you are using closed drivers, don't expect the kernel developers to be interested in any problems you have.

---

### Post by oygle on 2009-01-14
Okay, thanks. :)

---

