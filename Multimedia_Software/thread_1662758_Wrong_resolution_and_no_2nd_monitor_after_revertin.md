---
title: "Wrong resolution and no 2nd monitor after reverting to Nouveau"
date: 2011-01-08
forum: Multimedia Software
---

### Post by jdholman on 2011-01-08
All:

I reverted from the NVIDIA driver to Nouveau to address some dual-screen performance issues I have been having.  I am on 10.10 64-bit on a Dell M6400 with a 1680x1024 2nd monitor.

After removing the Nvidia stuff and reinstalling Nouveau and rebooting, I find that the Monitor Preferences application won't go more than 1280x1024 which is strange as the native resolution on the laptop is 1920x1280.  Also, after plugging in the 2nd monitor to the VGA port, the Monitor Preferences application does not detect the 2nd monitor.

The resolution and the 2nd monitor worked fine on the Nvidia drivers and also work fine when I boot from the Live CD.

What do I need to do to get my resolution and 2nd monitor fixed without using the Nvidia driver?

Thanks,

Jim

---

### Post by BicyclerBoy on 2011-01-08
Sounds like nouveau X server can not read the display data.

What's in the /var/log/Xorg.0.log file ?
dmesg

Laptop panels do not have EDID eeprom as such but have their EDID data in the video processor firmware..

The 2nd (ext) monitor should have EDID tho..

What was problem with nvidia ?
I bet you were using twinview with nvidia ?
Try configure separate X screens..

---

### Post by jdholman on 2011-01-08
Hey BB:

Thanks for you reply.  I am attaching my xorg.o.log file for you to view.

Do you want to see the dmesg output as well?

The issue I had with the Nvidia drivers was twofold.  It wouldn;t reliable allow me to activate a 2nd display when the display hadn;t been used before, such as a client's LCD projector.  I would get a black screen that wouldn't reset without restarting X or rebooting.  Also, on either Twinview or Separate X, while running a CPU intensive application such as VMWare Workstation, my CPU would peg at 100%.  It wouldn't do this when using the primary display only.

Anyway, this works fun under Nouveau when I boot from the Live CD, so I need to know how to get it working again with the NVidia drivers or reloading Ubuntu.

Thoughts?

Jim

---

### Post by BicyclerBoy on 2011-01-08
There is no real plug & play in X server system like with windoze...
This is a real limitation in Xorg.

I have been able to plug in new display , open nvidia-settings (GUI), click detect monitor, select monitor & set resolution...
.. but the setting of separate X screen or twinview requires restart of X server.

The possible nvidia workaround is dynamic twinview where you have meta-modes for the single monitor & two monitors with the same overall pixel dimension.

 [http://ru.download.nvidia.com/XFree86/Linux-x86/180.22/README/chapter-13.html](http://ru.download.nvidia.com/XFree86/Linux-x86/180.22/README/chapter-13.html)


Is possible your resolution is wrong because 
[    18.211] (WW) VESA(0): Unable to estimate virtual size
[    18.211] (II) VESA(0): Not using built-in mode "1920x1200" (no mode of this name)


Never used nouveau but maybe it needs a xorg.conf file generated 
Maybe it needs  Option "DPI" "string" so it can calculate the virtual size. This option specifies the Dots Per Inch for the X screen; for example:
     Option "DPI" "75 x 85"

---

### Post by jdholman on 2011-01-09
I wasn't in the mood for extended troubleshooting something as tricky as video resolution, 3d graphics, Nvidia "Anything", etc.

I ended up backing up up my home directory, installed packages, and re-installed off the CD.  I am running Nouveau now.

I am sure that I will miss 3D graphics functionality and "wobbly windows", but I love being able to boot up with a new external monitor connected and having Ubuntu auto-detect and mirror for me.  I am also hoping that running VMWare Workstation while using a 2nd display avoids the performance problems the NVidia proprietary drivers had.

I'll give this a week or so of heavy use and update this thread for posterity.

Thanks for your help,

Jim

---

### Post by efflandt on 2011-01-09
You could try installing **libgl1-mesa-dri-experimental** package which should give you glx for 3D effects with nouveax.  I don't think you have to reboot, it would probably take effect if you log out and back into X.  It will not be nearly as fast as nvidia drivers, but that probably does not matter for the desktop.

---

