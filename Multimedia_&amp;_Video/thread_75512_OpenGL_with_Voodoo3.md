---
title: "OpenGL with Voodoo3"
date: 2005-10-13
forum: Multimedia &amp; Video
---

### Post by StinkyPete on 2005-10-13
Eeek! This is my first ever post/experience with Linux (please be gental :)

After install Ubuntu 5.1 for my son on an old machine (Celeron 333 - 256Mb RAM) with a Voodoo3 3dfx card. I've had a lot of grief trying to get the accelaration to work.

I've found that in order to enable DRI I needed to edit the Xorg.conf to remove the higher resolutions, leaving just 1024x768 and below. This was indicated by the /var/log/Xorg.log. Now when I run glxgears (with LIBGL_DEBUG=verbose) I get:

[SIZE="2"][FONT="Courier New"]
libGL: XF86DRIGetClientDriverName: 1.0.0 tdfx (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/tdfx_dri.so
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
libGL error:
tdfx DRI driver expected DDX version 1-1.1.x but got version 1.0.0
libGL warning: 3D driver returned no fbconfigs.
libGL error: InitDriver failed
libGL error: reverting to (slow) indirect rendering
[/SIZE][/FONT]

How do I resolve the DRI-DDX conflict?

(I'd be thankful for any reply)

---

### Post by davidjneff on 2005-10-13
[QUOTE=StinkyPete]Eeek! This is my first ever post/experience with Linux (please be gental :)

After install Ubuntu 5.1 for my son on an old machine (Celeron 333 - 256Mb RAM) with a Voodoo3 3dfx card. I've had a lot of grief trying to get the accelaration to work.

I've found that in order to enable DRI I needed to edit the Xorg.conf to remove the higher resolutions, leaving just 1024x768 and below. This was indicated by the /var/log/Xorg.log. Now when I run glxgears (with LIBGL_DEBUG=verbose) I get:

[SIZE="2"][FONT="Courier New"]
libGL: XF86DRIGetClientDriverName: 1.0.0 tdfx (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/tdfx_dri.so
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
libGL error:
tdfx DRI driver expected DDX version 1-1.1.x but got version 1.0.0
libGL warning: 3D driver returned no fbconfigs.
libGL error: InitDriver failed
libGL error: reverting to (slow) indirect rendering
[/SIZE][/FONT]

How do I resolve the DRI-DDX conflict?

(I'd be thankful for any reply)[/QUOTE]

I have a VERY similar setup on an old machine.  Voodoo3 can only do the accelerated graphics in Linux in 16 bit color depth.  Get rid of any of the 24 bit color depth options in your xorg.conf.

Don't expect miracles though.  This doubled my glxgears frame rate to about 100.  Still games are awful.

---

### Post by davidjneff on 2005-10-14
[QUOTE=davidjneff]I have a VERY similar setup on an old machine.  Voodoo3 can only do the accelerated graphics in Linux in 16 bit color depth.  Get rid of any of the 24 bit color depth options in your xorg.conf.

Don't expect miracles though.  This doubled my glxgears frame rate to about 100.  Still games are awful.[/QUOTE]

OK, this was working on Hoary -- installed glide2, made the driver "tdfx" in xorg.conf, eliminated all but 16 bit color, got some reasonable acceleration -- OK for screen, windows, and such, not OK for games.

Then, upgraded to Breezy.  No acceleration at all.  Oddly, the X log file says DRI is initialized and all is well, but glxinfo says no DRI, and glxgears is super slow.

Since I have just been playing with Ubuntu for a week or so I'm going to start all over with a fresh Breezy install.  I think all you get is 2D acceleration, but it still made windows scrolling and such snappier, and thats all I'm looking for.

Getting graphics acceleration to work is still a huge gap in every Linux distribution I've used, including ubuntu.  I have 3 very different PCs (very old Celeron PC, medium old laptop with ATI graphics, fairly new desktop with NVIDIA graphics).   Some distributions work just great on one PC but not others, ubuntu is the first that "just worked' out of the box, but on other distributions Voodoo acceleration worked out of the box but it was very hard to get other acceleration to work.  Mepis worked pretty good on this old Celeron PC and I THINK with Voodoo acceleration.  Then I tried Fedora, it was a pig.  Then my monitor died, got a new monitor, and all of a sudden Mepis wouldn't boot off the live CD -- just due to a different monitor!  The all to common xwindows error "no default screen found".

With ubunto I ran into:

1.  Very difficult to get Voodoo3 acceration to work.  Broke when upgraded to Breezy.  But general trick is getting glide2, setting driver to "tdfx" (which may occur when installing glide, I forget), and only using 1024x768 or less and 16 bit color.

2.  Reasonable ATI acceleration "out of the box", grabbing the flrgx stuff totally broke it, and I have been unable to get it back to where it was when I started -- even uninstalling the flrgx drivers, restoring xorg.conf.  Very odd, in other words, the initial driver was "ati", and even when I now load the original driver I have no acceleration -- even though I did before!

3.  NVIDIA acceleration got going pretty easily by just grabbing the nvidia module and changing the driver from "nv" to "nvidia".

SOMEBODY, SOMEWHERE, please work on making all of this graphics configuration smarter and more automatic.  There are a few things I look for in a "successful" Linux distribution.

1.  Just works on wide range of hardware.  So far, ubuntu has done well here.  Works, but with graphics, not works optimally.

2.  Hardly ever is there a need to manually edit any config file.  ubuntu has been OK here, but i've had to edit the grub menu.lst to make Windows boot by default, sources.list to add repositories, and of course the ever popular xorg.conf to try to get graphics acceleration.  

3.  Easy upgrade path.  I upgraded from Hoary to  Breezy, only on 1 of my 3 PCs did it go smoothly.  On my old Celeron I got a bunch of errors with some Gstreamer setup components, and it broke my Voodoo3 acceleration.  On my new desktop, it hung twice, I had to kill the program that was hanging (once starting up RAID, which I do not have, the worst, setting up the kernel, which did not complete and resulted in a non-bootable system).  Only my medium old laptop seemed to upgrade with no problems.

I plan to just re-install Breezy on all 3 and start over with hopefully more initial knowledge.  I don't plan to mess with the ATI driver on the notebook, as it was good enough out of the box, and attempts to make it better have broken it.

---

### Post by StinkyPete on 2005-10-14
Do you think I should install 5.04 then to get the Voodoo to work?

I recently updated some of the X components and now I get "ignoring GLcore" as well as all Open GL stugg crashing with "Illegal operation" - All I did was upgrade some stuff - how do I revert? Is it best just re-installing?

--Peter

---

