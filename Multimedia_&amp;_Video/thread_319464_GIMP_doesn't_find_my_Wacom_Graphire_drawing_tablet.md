---
title: "GIMP doesn't find my Wacom Graphire drawing tablet"
date: 2006-12-15
forum: Multimedia &amp; Video
---

### Post by ramvi on 2006-12-15
Hi there!

(Ubuntu Edgy)

I'm the lucky owner of a Wacom Graphire drawing tablet. I've read a lot of stuff, and I've got it working. But gimp doesn't find it as an extension, so I do not have pressure sensitivity.

What do I do?
Thanks

---

### Post by slayer456 on 2006-12-18
Same here bud, I dont know how I am supposed to use my expensive device if I cant get it to work and I cant return it. I am very dissapointed. Please help someone!

---

### Post by xscd on 2006-12-19
For Edgy Eft and the 2.6 versions of the Linux kernel, first make sure that the Wacom kernel module (the kernel's driver for the Wacom tablets) is installed, by using the command locate:

sudo updatedb

locate wacom.ko

On my system, the kernel module (wacom.ko) is installed in:

/lib/modules/2.6.17-10-386/kernel/drivers/usb/input/wacom.ko

Then using synaptic (in the System--> Administration menu) install the following packages:

[list]
[*]xserver-xorg-input-wacom
[*]wacom-tools
[/list]

The first package installs the Xorg driver (wacom_drv.o) that reads the data from the kernel's Wacom driver and makes it actually do something useful, like respond to stylus pressure. This is the driver that makes the Wacom tablet useful in Gnome or KDE or Fluxbox or any of the GUI environments that Xorg supports. Remember, the kernel driver only "sees" and makes available the raw data from your Wacom tablet, it doesn't "understand" that data or interpret it. The kernel driver simply sees and makes the data from the tablet **available** to other programs (like the Xorg Wacom driver) to interpret and use as those other programs are configured to do.

The second package installs a nifty set of udev scripts and rules that create a symbolic link (like a "shortcut" in Windows-speak) in the /dev directory whenever the tablet is plugged into a USB port (we're referring specifically to a USB Wacom here, not a serial Wacom tablet, although serial tablets will work with the kernel and Xorg Wacom drivers too) that is always called /dev/input/wacom and always points to the real device file in the /dev directory (such as /dev/input/event2).

Be sure to examine and edit your Xorg configuration file, at /etc/X11/xorg.conf

--and in the InputDevice sections that refer to your Wacom tablet, be sure that each "Device" option contains "/dev/input/wacom" as a value --

Option        "Device"        "/dev/input/wacom"

This will allow the Xorg Wacom driver to find the correct "device file" to read the tablet data from, the same device that the **kernel** Wacom module is feeding the tablet data to.

Finally, if you happen to plug in your Wacom tablet **after** you are already in the GUI environment (Gnome or KDE, etc.) then log out and restart the Xorg server (the CONTROL-ALT-BACKSPACE key combination is an easy way to do this, once you are back at the GDM graphical login screen), so that Xorg can see the Wacom tablet as Xorg starts up. Even though there may be entries in Xorg's configuration file (xorg.conf) regarding the Wacom tablet, Xorg processes that file only when it starts up, not while it's running. That's why you have to restart Xorg after you plug in your USB Wacom tablet.

Best wishes--

---

