---
title: "Unable to get Ubuntu 10 fullscreen using VirtualBox"
date: 2010-11-01
forum: Multimedia Software
---

### Post by pauljean on 2010-11-01
I am using VirtualBox and I installed the Guest additions successfully.  Host F does not work as it is not the problem.  The resolution under monitor is 800x600. I had the same problem in Fedora where I modified the xorg.conf however Ubuntu does not have the file located in /etc/X11/...

I tried adding it with the same xorg.conf from my Fedora Virtual machine but that screwed up my display and had to fix it from the terminal.  

Not sure why Ubuntu 10 doesn't have an xorg.conf or how to fix the display if not from xorg.conf?

---

### Post by captaintrav on 2010-11-01
you shouldn't need xorg.conf to fix this.
try installing open-vm-tools in the guest os

edit:  scratch that, open-vm-tools seems to be for VMWare

I installed virtualbox-ose-guest-x11, that worked.  Did you try installing guest addons from synaptic, or from the "Install Guest Addons" thingie in VirtualBox.  If you did the later, try the former.

---

### Post by pauljean on 2010-11-02
I am 1 step further :
 
- I installed the virtualbox-ose-X11 and rebooted
       Now my resolution went from 800x600 to 1024x768
 
I still can't get it in full screen.
 
Previously I did install guest additions:
 
Building the VirtualBox Guest Additions kernel modules 
Building the main Guest Additions module ...done. 
Building the shared folder support module ...done. 
Building the OpenGL support module ...done. 
Doing non-kernel setup of the Guest Additions ...done. 
Starting the VirtualBox Guest Additions ...done. 
Installing the Window System drivers 
Warning: unknown version of the X Window System installed. Not installing 
X Window System drivers. 
Installing graphics libraries and desktop services components ...done. 
root@Ubuntu-VirtualBox:/media/VBOXADDITIONS_3.2.8_64453#

---

