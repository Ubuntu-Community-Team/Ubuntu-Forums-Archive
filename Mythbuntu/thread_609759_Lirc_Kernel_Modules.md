---
title: "Lirc Kernel Modules"
date: 2007-11-11
forum: Mythbuntu
---

### Post by ghuber on 2007-11-11
I have compiled linux kernel  2.6.23.1 on my Mythbuntu box.   All has gone well with the exception of lirc.  When I start lirc I get the following error:

#####################################################
## I couldn't load the required kernel modules ##
## You should install lirc-modules-source to build ##
## kernel support for your hardware. ##
#####################################################
## If this message is not appropriate you may set ##
## LOAD_MODULES=false in /etc/lirc/hardware.conf ##
#####################################################

What do I need add to the kernel to get lirc back up and running?  

Geoff

---

### Post by Akriss on 2007-11-11
Probably should recompile LIRC with the modules you need, for the new kernel.

---

### Post by superm1 on 2007-11-12
Personally,
I would recommend you stick with 2.6.22 if at all possible.  The kernel modules for LIRC and restricted modules are all shipped with it even with kernel updates.

Do you have a compelling reason to use 2.6.23?

---

### Post by ghuber on 2007-11-12
I found a link last night that said lirc had a problem compiling with 2.6.23, the fix was in the lirc source repository.  I took a stab at getting that to compile but had no luck so I went ahead and changed my grub file to go back to the old kernel.  Works fine again.   The reason for trying that kernel was to see if it would get my PVR150 working with this computer.  It hangs at the point of hardware detection.   It did not help.  It looks like it would be best to avoid 2.6.23 until the next release of lirc that is fixed so that it will compile on it.

---

### Post by Akriss on 2007-11-12
This post [[COLOR="Red"]Here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=587732")  should help. possibly.

---

