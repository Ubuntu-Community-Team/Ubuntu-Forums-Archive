---
title: "nVidia GeForce 7900GS 256MB PCI-E x16 Video Card"
date: 2006-09-07
forum: Multimedia &amp; Video
---

### Post by ztirffritz on 2006-09-07
I purchased this card on WOOT here:
[http://www.woot.com/blog/blogentry.aspx?blogentryid=1420](http://www.woot.com/blog/blogentry.aspx?blogentryid=1420)

Now I can't get the nVidia drivers to install.  I tried installing the version used by Automatix Bleeder.  Is there another version that I should try?  Can you provide a link?

---

### Post by tseliot on 2006-09-07
1) What does it mean that you can't install the driver?
2) Which method of installation of the driver did you try?
3) Did you read my guide?
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)
4) Can you post the output of this command:
```
lspci -n | grep 300
```

---

### Post by ztirffritz on 2006-09-07
When I ran that code it returned this.  I'm learning Linux as fast as I can, but this is greek to me.

0000:01:00.0 0300: 10de:0292 (rev a1)

---

### Post by ztirffritz on 2006-09-07
When I try to install the nVidia driver I get this error:

***********
ERROR: Unable to find the kernel source tree for the currently running kernel.  Please make sure you have installed the kernel source files for your kernel and that they are properly configured; on Red Hat Linux systems for example, be sure you have the 'kernel-source' RPM installed.  If you know the correct kernel source files are installed, you may specify the kernel source path with the '--kernel-source-path' command line option
***********

---

### Post by ztirffritz on 2006-09-07
When I try to install the nVidia driver I get this error:

***********
ERROR: Unable to find the kernel source tree for the currently running kernel.  Please make sure you have installed the kernel source files for your kernel and that they are properly configured; on Red Hat Linux systems for example, be sure you have the 'kernel-source' RPM installed.  If you know the correct kernel source files are installed, you may specify the kernel source path with the '--kernel-source-path' command line option
***********

---

### Post by ztirffritz on 2006-09-07
I managed to get it running using this:
apt-get install kernel-headers-$(uname -r)

This installed the kernel headers that were needed.  

I tried to install the nVidia drivers again.

Then it told me that I needed to install the xorg developer files.  I did that with Synaptic.

I tried to install the nVidia drivers yet again.

It failed. 

I checked the log files and it appears that I need to supply power to the card using some obscure power connecter/converter.  I start looking for that and let you know what I come up with next.

---

### Post by colonelk on 2006-09-08
For the last few generations of graphics cards they have needed external power connectors to supply the necessary power.  For PCI Express cards like yours you will need a PCI-Express power connector that plugs into your graphics card.  Many newer power supplies have these connectors natively attached and some supply the connectors as adaptors from a standard molex connector.  

You also need to make sure that the power supply is a good one with plenty of Watts and good stable 12V rails.  Something like an Antec or Enermax or FSP, or Tagan with 480W or above.  You can't really afford to skimp on the PSU these days if you want to run the latest graphics and processors.

HTH

CK

---

### Post by tseliot on 2006-09-08
Your card is not supported by the Nvidia driver yet.

The ID of your card (0292) does is not in this list:
[http://download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/appendix-a.html](http://download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/appendix-a.html)

You should wait for the next release of the driver

---

### Post by ztirffritz on 2006-09-12
I purchased a new power-supply that included a PCI-e 6-pin connector then re-installed the nVidia driver and it worked.  As I suspected, nVidia included support for the 7900GS but didn't document it.  But alas, XGL/Compiz still would not work.  Everytime that I tried to activate it it failed.  I cause GDM to crash everytime that I tried "toggle-compiz-nvidia".  I used Automatixbleeder to install XGL/Compiz because that has been the most consistently successful technique that I've found.

---

