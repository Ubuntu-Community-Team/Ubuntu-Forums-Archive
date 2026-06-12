---
title: "Possible solution to jockey-gtk, broadcom sta, maybe dell"
date: 2010-11-05
forum: Networking &amp; Wireless
---

### Post by threegremlins on 2010-11-05
Installing the wireless driver

I have a Dell Vostro 1500 with a broadcom sta wireless. 

I found this to work over in the Crunchbang Forums.

Thanks to rich-lxh over at Crunchbang Forum for the link to [http://wiki.debian.org/wl#Squeeze](http://wiki.debian.org/wl#Squeeze)

These  commands I've modified from the above link, don't install the repositories they suggest on that page if you've gone over and read them.

Update the list of available packages. Install the module-assistant and wireless-tools packages:

#    sudo aptitude update
#    sudo aptitude install module-assistant wireless-tools

Build and install a broadcom-sta-modules-* package for your system, using Module-Assistant:

#    sudo m-a a-i broadcom-sta

Rebuild your initial ramdisk, to blacklist modules defined at /etc/modprobe.d/broadcom-sta-common.conf within initramfs:

#     sudo update-initramfs -u

Unload conflicting modules:

#     sudo modprobe -r b44 b43 b43legacy ssb

Load the wl module:

#     sudo modprobe wl

Verify your device has an available interface:

#     sudo iwconfig

    
I found it didn't work right away, but after rebooting and running the last two commands again here I am writing this. 

I don't know if it matters but before doing the above, I did go through Synaptic and removed with configuration files everything broadcom. Basically to get the wired network running again. Who knows maybe it helps.

---

### Post by threegremlins on 2010-11-06
for some reason it doesn't load in the boot up, I might have to go look at the coding again. I ran through the commands itramfs modprobe and iwconfig a few times and it eventually started loading on boot up. I'm wondering if it's because I'm working out a minimal installation of Ubuntu with openbox as a desktop and probably what's causing the problem is I am trying to stay away from Gnome oriented software.

Did it again with Meercat and worked fine.

---

