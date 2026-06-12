---
title: "agpgart... no 3d"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by bhouncy on 2007-10-21
Hi. I have never ever ever got 3d acceleration to work with my 9800pro. 

 /var/log/Xorg.0.log gives me

> 
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.20-16-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): [pci] find AGP GART
[B](EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENODEV"
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0x2b08af532000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *[/B]


The areas highlighted have nothing to do with a fault with the driver but with agpgart apparently (I cut a lot because it kept saying too many images). Is there a solution to get this thing working? I found this but I'm not seeing agpgart.

> X Fails to Load on Systems with Linux Kernel Version 2.6.x

This information applies to the following system configurations:

    * Linux kernel version 2.6.x
    * Any ATI Linux driver 

A blank screen may appear momentarily when X starts to load. The following error message (or similar) may appear on the text console or in /var/log/XFree86.0.log:
(EE) fglrx(0): [agp] unable to acquire AGP, error ""xf86_ENODEV""xf86_ENODEV""

This is not a problem with the display driver.

Version 2.6 kernels require a second kernel module in addition to agpgart, which should be named similar to the manufacturer of your motherboard AGP chipset. This error message should occur if the other agp module is not loaded.

This issue can be worked around as follows:

   1. First make sure that agpgart is loading properly.
   2. To find out which AGP controller your motherboard uses, issue the following command: lspci | grep AGP
   3. To find a list of AGP related kernel modules installed on your machine, issue the following command and look for a module (*.ko file) that suits your AGP Controller: ls /lib/modules/`uname -r`/kernel/drivers/char/agp
   4. Use the modprobe command (as root) to load the module. For example: On a motherboard using a VIA® AGP Controller, you would load the via-agp.ko using modprobe as follows (notice that the trailing .ko is omitted): modprobe via-agp

Check the modprobe manpage for more information on loading kernel modules.

   5. To verify that the AGP module is already loaded, run lsmod as root. With the X server running and the connection established, the usage count of this module must be greater than zero. 

If you cannot find a suitable agp module for your motherboard, then you may want to upgrade to the latest version of the Linux kernel, or check your motherboard manufacturer's website for more information.


Feisty. 9800pro

---

### Post by bhouncy on 2007-10-22
bump.

As you sit their with your hyper fps and freedom think of the poor agp ati users who can't get any 3d rendering... for years. 'Get a new system' I hear you say. Well the UN isn't handing out any souped up graphics cards in this desolate place. Lost in the wilderness fading away with lack of fps. If you're hearing this Bob Geldof or anyone who knows the answer on how to save the planet by bringing vector shading version 4.1 to the needy please help us [-o<

---

### Post by Heazky on 2007-10-24
On a friends PC i got exactly the same error.
This is with Ubuntu Gutsy and also a Radeon 9800 Pro.

```
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENODEV"
(EE) fglrx(0): cannot init AGP
```

Compiling the newest fglrx driver (8.40.4) manually still doesn't fix it.
The agpgart and intel_agp modules seem to be loaded correctly too, as is fglrx.

Only direct rendering keeps out.

```
koen@dreadnought-linux:~$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```


UPDATE - Solved:
I solved it by blacklisting the i82875p_edac and edac_mc modules as described [here](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684).

```
sudo vim /etc/modprobe.d/blacklist
```

And add these lines:

```
blacklist i82875p_edac
blacklist edac_mc
```

---

### Post by shimonlyons on 2007-10-26
I have exactly the same problem but blacklisting the edac modules didn't do it.

nor did messing around with whether to use fglrx's internal agpgart or not (it said it doesn't do internal for 2.6 kernels)

Radeon X1050, Intel AGP bridge, running gutsy

Please help! I've been at this for ages!

---

### Post by Qwerty_ on 2007-10-26
Have you installed the restricted drivers?

System>Administration>Restricted Drivers Manager.

---

### Post by shimonlyons on 2007-10-26
yes, i've tried both ubuntu's fglrx and ati's. had more success with ati's, ubuntu's didn't work at all. the restricted drivers manager is saying it's enabled and X's log says it's ok too, until it tries acquiring the AGP (took me a while to get to that stage too!)

---

### Post by MrClearPore on 2008-02-29
> UPDATE - Solved:
I solved it by blacklisting the i82875p_edac and edac_mc modules

Wow.  You have just become my #1 fan.  I had been grappling with Xorg in Kubuntu since day 1 practically.  Since I first started using Linux back in October, it was a real crap shoot whether or not I could get Xorg to set up my display properly.  On some installations, I would get some errors about my display not being DRI capable, and/or that it could not initiate my AGP card, etc.  Installing the ATI proprietary drivers (fglrx) would, of course, give me Mesa as vendor, instead of ATI.  Direct rendering would be a no-go as well,

On some other installations, everything would fall into place, and I would get no errors regarding AGP and direct rendering from the **Xorg.0.log** file, and ATI's drivers would install properly and give me proper 3D rendering.

However, after following the above tip, I have, for the first time EVER, been able to transform all the occurrences in **fglrxinfo** from Mesa to ATI without having to re-install Kubuntu.  Every other tip/hack/what have you would fail.

I could not have stumbled across this tip at a better time either, as I started using the server install of Kubuntu instead of the full-blown installation (I don't need the extra programs; I like to install a base system and install only the programs I need).  With the server install, I was unable to get Xorg to get my AGP card properly initialized **one single time.**.. until now :)

Thanks again.

---

