---
title: "Getting XvMC working"
date: 2008-01-23
forum: Mythbuntu
---

### Post by mikeyandmary on 2008-01-23
Hi all

I am trying to get HDTV working on my mythtv setup. I read that getting XvMC will assist with this but I cannot get it going. 

I have tried changing the line in XvMCConfig to libXvMCNVIDIA_dynamic.so.1 and to libXvMCNVIDIA.so.1 each time the screen goes blank and I need to restart X using ctrl+alt+backspace

I know that the OSD should be grey if XvMC is working and it remains the usual blue colour. 

If it helps, my system is:

CPU: Celeron 2800
RAM: 768Mb
OS: Ubuntu 7.04
HDD: 320Gb (2 partitions: 1-32Gb root 2-286Gb + 2Gb swap)
Video Card: Geforce 7600GS
DVB Cards: DVICO Fusion USB + DVICO Dual Digital 4

The NVIDIA drivers were installed using ENVY

All three tuners work in kaffeine and I can watch HDTV perfectly in Kaffeine but not in Mythtv. Standard definition is playing fine. 

Thanks for any assistance.

---

### Post by not4us on 2008-01-23
I know this one!!

Edit yor /etc/X11/xorg.conf file and add this lines after BoardName unde the "device" section:

Option "RenderAccel" "true"
Option "NVAGP" "1"
Option "UseEvents" "True"
Option "XvmcUsesTextures" "false" 

It worked for me and I was having your exact same problem.

---

### Post by jeremynd01 on 2009-01-10
I had a similar desire for a slightly older hardware (P4/1.6 w/ 768Mb RDRAM and geForce FX 5200).  My system still stutters a during live playback, but I have made progress.  Some of this is beyond just getting XvMC working, but given the topic of your post it appropriate.  Here's what I found worked:

Also, my Mythbuntu 8.10 install had libXvMCNVIDIA_dynamic.so.1 in /etc/X11/XvMCConfig.  A quick `ls -l /usr/lib/libXvMC*` showed that this library and libXvMCNVIDIA.so.1 were both sym linked to libXvMCNVIDIA.so.1.173.14.12 (because my FX 5200 uses the 173 driver).  Check and make sure yours are similarly linked (probably to a so.1.177.x.y driver, for the 7600 card - I've not used Envy, so this might be missed).  FYI - the 180 driver is out of beta release, so look for an update package soon (or get it straight from nVidia: [http://www.nvidia.com/object/linux_display_ia32_180.22.html](http://www.nvidia.com/object/linux_display_ia32_180.22.html).  Your 7600 may even have superior VDPAU support.

Next, per not4us's suggested, add those lines to /etc/X11/xorg.conf, under Section "Device".  While there, double check that the Driver is set to "nvidia" and not "nv".  The RenderAccel and XvmcUsesTextures are the default options for the nvidia drivers, so probably won't change much.  UseEvents seems to add a workaround if the hardware is busy, so may help.

Now, AGP support and the "NvAGP" "1" option had me stuck for a while.  In the [nVidia driver README v180]("http://us.download.nvidia.com/XFree86/Linux-x86/180.22/README/chapter-12.html") there is a list of motherboard chipsets where nVidia's AGP support is preferred (i.e. set "NvAGP" "1"), some the rest where the kernel's AGPGART is preferred (set "NvAGP" "2").  You can find your chipset with an `lspci |less` and look for an entry that mentions Intel, Via, SiS, or nVidia.  My chipset (Intel 850) was on the list, so I set "NvAGP" "1" ___AND___ had to edit /boot/grub/menu.lst, adding the argument "agp=off" to the end of the default kernel line (and then reboot).  Apparently Ubuntu kernels have the APG GART backend stuff all compiled in, which interferes with nVidia's AGP stuff and has to be disabled (see the README).  Before this, my /var/log/Xorg.0.log would have an entry:
NVIDIA(0): No usable AGP GART found.

After passing agp=off to the kernel, the successful entries looked like this:
NVIDIA(0): Initialized GPU GART

And one final xorg.conf note:  Apparently nVidia motherboard chipsets have a problem with GLX and Composite being on at the same time (also a prob w/ old versions of X, pre XFree86, X11R6.9.0, whatever that means for Xorg...).  But if you have one of those chipsets, add can try additing these three lines to the end of your xorg.conf:
```
 Section "Extensions"
      Option "Composite" "Disabled"
 EndSection

```

You appear to know that, after changing xorg.conf, to press CTRL+ALT+BACKSPACE to restart the X server.


Once X is configured properly, it's time to explore the MythTV playback profiles, which control what decoding method is used.  Within mythfrontend, navigate to Utilities/Setup > Setup > TV Settings > Playback.  On page 3/9, you can select a profile.  I think the default was CPU++.  There is an entry called "CPU--" which has an item "if rez > 0 0 -> XvMC".  Move this to the top of the priority list and try watching a vid now, and see if the OSD is grey.  If that works, you can edit this entry and try using OpenGL rendering as well as XvMC, change deinterlacing options, and so on.


Many others have reported that HD playback works great with other players (mplayer, xine, or like you mentioned, kaffeine), but chokes in MythTV.  There is a whole wiki entry on this ([http://www.mythtv.org/wiki/index.php/HD_Playback_Reports](http://www.mythtv.org/wiki/index.php/HD_Playback_Reports)).  Even if you get XvMC working, performance in Myth may not stack up to the external players.

---

