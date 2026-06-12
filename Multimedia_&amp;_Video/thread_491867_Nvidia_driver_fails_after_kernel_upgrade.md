---
title: "Nvidia driver fails after kernel upgrade"
date: 2007-07-04
forum: Multimedia &amp; Video
---

### Post by supertdog on 2007-07-04
I'm new to ubuntu but have used several other distros.

I have a GeForce 6600 series graphics card and AMD64 processor.

I was able to get the x86_64 ubunto 7.04 distribution running but I had to build and load the nvidia driver before I could get any UI at all.

On first reboot the nvidia splash screen was displayed, the graphics display came up and everything seemed wonderful.  I then accepted the prompt to update the installation which upgraded the kernel from 2.6.20-15-generic to 2.6.20-16-generic

After that update the xserver fails to start and I find this in the Xorg.0.log
```

(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.11  Wed Jun 13 17:16:40 PDT 2007
(II) Loading extension GLX

(II) NVIDIA dlloader X Driver  100.14.11  Wed Jun 13 16:35:28 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 03:00:0
(WW) NVIDIA: No matching Device section for instance (BusID PCI:0:5:0) found
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found

(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Video Driver

(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly.
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.
```
even after re-installing the driver I cannot get gdm to start.  I have tried 100.14.11 as well as 1.0-7185 versions of the driver.  

Could someone point me in the right direction?

---

### Post by eentonig on 2007-07-04
You need to recompile your nvidea drivers for the new kernel. If it's already supported.

---

### Post by scxtt on 2007-07-04
you should still be able to boot into the 2.6.20-15-generic kernel and have nvidia drivers working ... but you'll need to download the headers/kernel source for the NEW kernel, boot to it, and make sure /usr/src/linux points to THAT new kernel's source --- i'd download the *.run from nvidia.com and do it that way ...

or not even worry about it - if you don't have a specific reason to use that new kernel, just stick w/ the -15 kernel ...

---

### Post by supertdog on 2007-07-04
Well, I'm not sure what I've done but even going back and booting into the 2.6.20-15-generic kernel fails now.

I have tried to use the *run scripts from nvidia to recompile as well as the lovely "[envy]("http://albertomilone.com/pmwiki/pmwiki.php")"  script, however I can only get a graphical display by using the "nv" driver.  I thought the envy utility did a pretty good job of cleaning out anything nvidia before compiling so I'm not sure where to look for a fix.

Thanks for your help btw.

---

### Post by supertdog on 2007-07-04
Okay, after switching back to the 15-generic kernel and using the "nv" driver to get a graphics display I re-ran "envy" and that seemed to do the trick.  So I'll leave things as they are for the moment.  I might try and get the 16-generic working someday but while this is working I don't want to mess with it too much.

Thanks again for your help.

---

### Post by SGI on 2007-07-04
For those that got the problem doing the installation manually.  You need to delete/disable the linux restricted driver that comes with Ubuntu.  This is how I got my most current driver installed (but I think there are some problem w/ my settings that gives me artifacts in the other "virtual desktops" ... it just won't redraw itself - but this is on a thread on its own)

to do it manually, I typed this:

nvidia-glx --purge

then edit /etc/default/linux-restricted-modules (or  /etc/default/linux-restricted-modules-common) so that it shows DISABLED_MODULES="nv nvidia_new"

then I was suggested to do a: rm -f /lib/linux-restricted-modules/.nvidia_new_installed (but I just renamed it by typing mv /lib/linux-restricted-modules/.nvidia_new_installed  /lib/linux-restricted-modules/backup.nvidia_new_installed.back

then reinstall the driver as usual. (which will also recompile the kernel module as well)

hope this helps for those who is still looking.

-=SGI=-

---

### Post by moffa on 2007-07-14
> **SGI said:**
> For those that got the problem doing the installation manually.  You need to delete/disable the linux restricted driver that comes with Ubuntu.  This is how I got my most current driver installed (but I think there are some problem w/ my settings that gives me artifacts in the other "virtual desktops" ... it just won't redraw itself - but this is on a thread on its own)

to do it manually, I typed this:

nvidia-glx --purge

then edit /etc/default/linux-restricted-modules (or  /etc/default/linux-restricted-modules-common) so that it shows DISABLED_MODULES="nv nvidia_new"

then I was suggested to do a: rm -f /lib/linux-restricted-modules/.nvidia_new_installed (but I just renamed it by typing mv /lib/linux-restricted-modules/.nvidia_new_installed  /lib/linux-restricted-modules/backup.nvidia_new_installed.back

then reinstall the driver as usual. (which will also recompile the kernel module as well)

hope this helps for those who is still looking.

-=SGI=-

Thanks a lot!  Removing the .nvidia_new_installed directory did the trick for me

---

