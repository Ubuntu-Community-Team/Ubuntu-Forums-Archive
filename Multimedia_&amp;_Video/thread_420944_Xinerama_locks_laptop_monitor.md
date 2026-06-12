---
title: "Xinerama locks laptop monitor"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by DaOane on 2007-04-24
Ubuntu 7.04, Radeon Mobility 9200, 1400x1050 laptop monitor, 1920x1200 external display

I had a working dual-screen setup with the fglrx-drivers under Ubuntu Edgy. After the upgrade to Feisty the available fglrx drivers do not support my graphics card any longer, so I changed to "radeon" drivers. These work very well in a single screen setup. To get back my dual-screen setup I tried both Xinerama and MergedFB with my laptop monitor as primary and the desktop monitor as secodary screen. MergedFB does not work at all (I just get the primary screen on the desktop monitor). With Xinerama I get the secondary screen on the desktop monitor but the Laptop monitor is black. I can move the mouse pointer out of my desktop monitor and (with some trying) even grab the toolbars from the (black) primary monitor and put them onto the secondary monitor, i.e. I know that the primary screen is there, just not displayed on the monitor.
I read that there are bugs in the "radeon" driver which cause this behaviour in AGP mode (although with MergedFB, [http://gentoo-wiki.com/HOWTO_DRI_with_ATi_Open-Source_Drivers](http://gentoo-wiki.com/HOWTO_DRI_with_ATi_Open-Source_Drivers) ),  but it did not help to force the graphics card into pci-mode (Option "BusType" "PCI").

Has this behaviour been observed elsewhere with Xinerama and is there a solution or workaround?
Thanks and cheers,

Henning

---

