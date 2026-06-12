---
title: "Compiling Linksys WMP11 Drivers - Where is the Kernen Source?"
date: 2006-02-12
forum: Networking &amp; Wireless
---

### Post by azidrane on 2006-02-12
Hey guys,
Another nube here. I'm trying to compile these drivers to get my WLAN up and running and I'm just not having any luck. I'm using linux-wlan-ng-0.1.12 right now. Trying to run Make Config and i'm getting this

root@azidlinux:/home/azidrane/Desktop/linux-wlan-ng-0.1.12# make config

-------------- Linux WLAN Configuration Script -------------

The default responses are correct for most users.

Build Prism2.x PCMCIA Card Services (_cs) driver? (y/n) [y]: n

Build Prism2 PLX9052 based PCI (_plx) adapter driver? (y/n) [n]: y

Build Prism2.5 native PCI (_pci) driver? (y/n) [n]: y

Build Prism2.5 USB (_usb) driver? (y/n) [n]: n

Linux source directory [/usr/src/linux]:
Linux source tree /usr/src/linux is incomplete or missing!
    See the HOWTO for a list of FTP sites for current kernel sources.

Configuration failed

make: *** [config] Error 1


What to I need to put here (Linux source directory [/usr/src/linux]:). I've searched all over, but I cannot find the answer.

Cheers!

(Its a fresh install of Ubuntu 5.10 btw)

---

### Post by Lambert on 2006-02-12
Azz knows better then I here, see nextpost.

---

### Post by az on 2006-02-12
[QUOTE=azidrane]Hey guys,
Another nube here. I'm trying to compile these drivers to get my WLAN up and running and I'm just not having any luck. 
[/QUOTE]

You absolutely do not need to compile anything to get it to work.  Install linux-wlan-ng.  It is on the install cd.  The kernel module is already installed on your system and the linux-wlan-ng package provides the userspace tools to make it work.

For some people, it still does not work.  Here are the details:
[http://ubuntuforums.org/showpost.php?p=465719&postcount=7](http://ubuntuforums.org/showpost.php?p=465719&postcount=7)


[QUOTE=azidrane]
What to I need to put here (Linux source directory [/usr/src/linux]:). I've searched all over, but I cannot find the answer.

Cheers!

(Its a fresh install of Ubuntu 5.10 btw)[/QUOTE]

In general, to compile a kernel module, you use the linux-headers package that matches your running kernel.  linux-headers-2.6.12-9-386, for example.  You do not need the whole source.  If you use the whole source, you would have to set up, configure and recompile your kernel.

---

### Post by azidrane on 2006-02-12
Thanks for the reply. I just realized that I made a harsh typo when writing the header for this thread. 
So, no compiling necessary. How does one "install" linux-wlan-ng from the cd? The only thing I have been successful in using is Synaptic Packer.

---

### Post by az on 2006-02-12
Using synaptic, search for "linux-wlan-ng" and click it to mark for installation.  Then make it go.  

From the command line you can run

sudo apt-get install linux-wlan-ng

but just use synaptic.

---

### Post by azidrane on 2006-02-12
Thanks for giveing me both options there.
I checked synaptic and I already have it installed. So I reinstalled it to no avail. The device manager still has it marked as "Unknown". It says its PCI and that its from linksys but other then that it looks fairly uninstalled. What else could be happening?

Thanks a ton by the way.

---

