---
title: "Nvidia Riva TNT/TNT2 can i get it working on 9.10 Karmic"
date: 2010-01-27
forum: Multimedia Software
---

### Post by zonemikel on 2010-01-27
I'm setting up this computer for my cousin, she is a little girl who likes snes games and stuff. Anyway the machine has a built in riva tnt card, its running at 1ghz with like 512mb of ram. 

The driver i found on nvidias website was 71.86 thats the one that supports "legacy" cards. When i try to install the new driver it just says it will ignore the legacy gpu and that i should use the 71.86 drivers. 

There is no option in the "restricted drivers" part of ubuntu so i can download and run [NVIDIA-Linux-x86-71.86.11.pkg1.run]("http://us.download.nvidia.com/XFree86/Linux-x86/71.86.11/NVIDIA-Linux-x86-71.86.11-pkg1.run")

I can install the 71.86 driver but it does not update the xorg.conf, so after reading the /usr/doc/share/nvidiasomething/readme i setup the xorg.conf; however, as soon as i change the driver to nvidia instead of nv or visa it crashes, says something about it cant load nvidia_drv.so in a location on the disk. I have navigated to that location and i do see nvidia_drv.so there so i'm not sure why it cant load it. 

I'm just trying to get zsnes to run a little smother for her its really jumpy now. I love linux but it seems time and time again i'm running into these driver problems. I'm tempted to throw microXP on it (10min install) and then i could load the drivers for the card and things would run better.

---

### Post by zonemikel on 2010-01-27
Looking at this [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) i tried to install linux-restricted-modules-XXX for 2.6.31-17-generic but they dont seem to exisit. 

Also looking for the nvidia drivers in synaptic package manager yeilds only the newer drivers. 

However if i search for the restricted modules or the nvidia driver in 9.04 with 2.6.28-17-generic i find both linux-restricted-modules-2.6.28-17-generic and nvidia-71-kernel-source, nvidia-glx-71. 

So can i conclude that i cannot install the legacy drivers for 9.10 but if i downgraded to 9.04 i could ?

---

### Post by LuisGMarine on 2010-01-27
First of all did you try using the Hardware Drivers?

If you go to System > Administration > Hardware Drivers, and open that up are there any drivers for you to activate?  Hopefully you *should* see one for the video card.  If you dont, then open up a terminal and type this command in.  

```
sudo lshw -C video
```

...and we'll take it from there.

---

### Post by zonemikel on 2010-01-27
Ya that whole "hardware drivers" thing has nothing thats why i was trying to install linux-restricted-modules. And even in synaptic package manager the 71. (legacy) driver does not show up for my kernel. 

anyway im gonna pop in another hdd and install 9.04 see if that changes anything. 

```
  *-display               
       description: VGA compatible controller
       product: NV5 [RIVA TNT2/TNT2 Pro]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 15
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 bus_master cap_list rom
       configuration: driver=nvidia latency=64 maxlatency=1 mingnt=5
       resources: irq:18 memory:41000000-41ffffff memory:44000000-45ffffff(prefetchable) memory:42000000-4200ffff(prefetchable)
```

---

### Post by 5010 on 2010-01-28
I am using 9.04 and have the same issue.
I also loaded the nvidia legacy stuff from synaptic.
System>Admin>Nvidia X Server Settings says "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "
nvidia-xconfig doesn't exist
so I followed advice from nvidia from here:
[http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8756/README/chapter-03-section-02.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8756/README/chapter-03-section-02.html)
I added driver "nvidia" to the xorg.conf device section.
man xorg.conf said the load "glx" was automatic so I didn't put that in.

Here is the error in the Xorg.0.log:

(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
**dlopen: /usr/lib/xorg/modules/drivers//nvidia_drv.so: undefined symbol: AllocateScreenPrivateIndex**
(EE) Failed to load /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (loader failed, 7)
(EE) No drivers available.

So... how does one define such a symbol?

---

### Post by PARO on 2010-03-04
I got the same problem with the same card and newest drivers from nvidia.com
It'd be nice if someone knows how to fix this.

---

### Post by real.aussie on 2010-03-09
Hi, 
I read this on [http://www.suse.de/~sndirsch/nvidia-installer-HOWTO.html#13](http://www.suse.de/~sndirsch/nvidia-installer-HOWTO.html#13) 
> **[SIZE="5"]13. Support for very old legacy chipsets (GeForce2 and older)[/SIZE]**

nVidia dropped support for very old legacy chipsets with release 1.0-7664. 
Currently these are the following:

    NVIDIA chip name                   Device PCI ID
    -------------------------------    -------------------------------
    RIVA TNT                           0x0020
    RIVA TNT2/TNT2 Pro                 0x0028
    RIVA TNT2 Ultra                    0x0029
    Vanta/Vanta LT                     0x002C
    RIVA TNT2 Model 64/Model 64 Pro    0x002D
    Aladdin TNT2                       0x00A0
    GeForce 256                        0x0100
    GeForce DDR                        0x0101
    Quadro                             0x0103
    GeForce2 GTS/GeForce2 Pro          0x0150
    GeForce2 Ti                        0x0151
    GeForce2 Ultra                     0x0152
    Quadro2 Pro                        0x0153

If you're affected by this use release **[SIZE="5"]71.86.01[/SIZE]**.
Then in the following section 14 they tell you where to get the binaries:
> **[SIZE="5"]14. References[/SIZE]**

* nVidia driver website
[http://www.nvidia.com/object/linux_display_ia32_180.22.html](http://www.nvidia.com/object/linux_display_ia32_180.22.html)
[http://www.nvidia.com/object/linux_display_ia32_173.14.12.html](http://www.nvidia.com/object/linux_display_ia32_173.14.12.html) (legacy chipsets)
[http://www.nvidia.com/object/linux_display_x86_96.43.01.html](http://www.nvidia.com/object/linux_display_x86_96.43.01.html) (old legacy chipsets)
[http://www.nvidia.com/object/linux_display_x86_71.86.01.html](http://www.nvidia.com/object/linux_display_x86_71.86.01.html) (very old legacy chipsets)
[http://www.nvidia.com/object/linux_display_amd64_180.22.html](http://www.nvidia.com/object/linux_display_amd64_180.22.html)
[http://www.nvidia.com/object/linux_display_amd64_173.14.12.html](http://www.nvidia.com/object/linux_display_amd64_173.14.12.html) (legacy chipsets)
[http://www.nvidia.com/object/linux_display_amd64_96.43.01.html](http://www.nvidia.com/object/linux_display_amd64_96.43.01.html) (old legacy chipsets)
[http://www.nvidia.com/object/linux_display_amd64_71.86.01.html](http://www.nvidia.com/object/linux_display_amd64_71.86.01.html) (very old legacy chipsets)

* nvidia installer
[http://download.nvidia.com/XFree86/Linux-x86/180.22/NVIDIA-Linux-x86-180.22-pkg1.run](http://download.nvidia.com/XFree86/Linux-x86/180.22/NVIDIA-Linux-x86-180.22-pkg1.run)
[http://download.nvidia.com/XFree86/Linux-x86/173.14.12/NVIDIA-Linux-x86-173.14.12-pkg1.run](http://download.nvidia.com/XFree86/Linux-x86/173.14.12/NVIDIA-Linux-x86-173.14.12-pkg1.run) (legacy chipsets)
[http://download.nvidia.com/XFree86/Linux-x86/96.43.01/NVIDIA-Linux-x86-96.43.01-pkg1.run](http://download.nvidia.com/XFree86/Linux-x86/96.43.01/NVIDIA-Linux-x86-96.43.01-pkg1.run) (old legacy chipsets)
[http://download.nvidia.com/XFree86/Linux-x86/71.86.01/NVIDIA-Linux-x86-71.86.01-pkg1.run](http://download.nvidia.com/XFree86/Linux-x86/71.86.01/NVIDIA-Linux-x86-71.86.01-pkg1.run) (very old legacy chipsets)
[http://download.nvidia.com/XFree86/Linux-x86_64/180.22/NVIDIA-Linux-x86_64-180.22-pkg2.run](http://download.nvidia.com/XFree86/Linux-x86_64/180.22/NVIDIA-Linux-x86_64-180.22-pkg2.run)
[http://download.nvidia.com/XFree86/Linux-x86_64/173.14.12/NVIDIA-Linux-x86_64-173.14.12-pkg2.run](http://download.nvidia.com/XFree86/Linux-x86_64/173.14.12/NVIDIA-Linux-x86_64-173.14.12-pkg2.run) (legacy chipsets)
[http://download.nvidia.com/XFree86/Linux-x86_64/96.43.01/NVIDIA-Linux-x86_64-96.43.01-pkg2.run](http://download.nvidia.com/XFree86/Linux-x86_64/96.43.01/NVIDIA-Linux-x86_64-96.43.01-pkg2.run) (old legacy chipsets)
[http://download.nvidia.com/XFree86/Linux-x86_64/71.86.01/NVIDIA-Linux-x86_64-71.86.01-pkg2.run](http://download.nvidia.com/XFree86/Linux-x86_64/71.86.01/NVIDIA-Linux-x86_64-71.86.01-pkg2.run) (very old legacy chipsets)
Hope this has been of help.

---

### Post by PARO on 2010-03-14
Thanks for pointing me to SUSE, they do suppot this card via RPM packages too! Only i cant get openSUSE to install on this computer.  During installation the kernal panicks everytime no matter what settings i start the install with (text, addswap, etc.).  I tried the net install, livecd, and soad.  Puppy also supports it.. but Puppy on a computer that will have multiple users who will require lots of different software options doesn't seem to work for me (Upup /w Ubuntu sources the driver fails in).  Ubuntu now has packages for all the new drivers except the 71 set, which we need o_o.

---

