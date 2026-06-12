---
title: "RT3572 not working after kernel upgrade"
date: 2010-08-28
forum: Networking &amp; Wireless
---

### Post by giddensdb on 2010-08-28
I just updated and installed kernel 2.6.35-19.  Ususally when I upgrade kernel I can just re-build the drivers and restart and its good.  This time I get errors during the "make" step.  Rebooted to previous kernel and it works fine.  Any suggestions?

---

### Post by giddensdb on 2010-08-29
Bump diddly bump bump

---

### Post by chili555 on 2010-08-29
> /home/broc/[COLOR="Blue"]2009[/COLOR]_[COLOR="Blue"]1214[/COLOR]_RT3572_LinuxSTA_V2.3.0.0I imagine that a file built in Decemebr 2009 is too old. You might go to Realtek's site and try a newer version.

---

### Post by giddensdb on 2010-09-01
I did and got the same error.  The one I have now is 2010_0709.  Good thought though!!

---

### Post by giddensdb on 2010-09-08
updated to yet another newer kernel and tried both the 2009 and 2010 versions and I keep getting an error on the same .o file.  Anyone have any ideas?  Please refer to my make command output.  Thanks

---

### Post by giddensdb on 2010-09-08
Some research points to usb_buffer_alloc and usb_buffer_free no longer existing in 2.6.35 kernels or more accurately being renamed.  What do I do about that to allow my drivers to compile correctly??

---

### Post by garyyoung on 2010-09-11
> **giddensdb said:**
> Some research points to usb_buffer_alloc and usb_buffer_free no longer existing in 2.6.35 kernels or more accurately being renamed.  What do I do about that to allow my drivers to compile correctly??

I have the same problem compiling the drivers. According to this post, the driver is now built into the kernel:
[http://comments.gmane.org/gmane.linux.redhat.fedora.general/377427](http://comments.gmane.org/gmane.linux.redhat.fedora.general/377427)
[http://comments.gmane.org/gmane.linux.redhat.fedora.general/377427](http://comments.gmane.org/gmane.linux.redhat.fedora.general/377427)

Could that be why the ralink drivers don't compile?

My system with the 2.6.35 doesn't recognize my usb rt3572, so I'd welcome any pointers in getting it going.

---

### Post by garyyoung on 2010-09-19
There's a new driver on the ralink site, dated 9-15-10, but it still won't compile.

---

### Post by MinorFreedom on 2010-09-22
Going to copy and paste the solution that worked for me from my Launchpad post:

> I believe I have found a solution to getting the latest rt3572 driver, 2.4.0.1, to work with newer kernels. This was, however, tested on a fresh net install (via ethernet) of ArchLinux 2010.05 x86_64 with kernel 2.6.35.

Per this post, related to a different Ralink chipset:
[http://art.ubuntuforums.org/showpost.php?p=9778612&postcount=108](http://art.ubuntuforums.org/showpost.php?p=9778612&postcount=108)
It appears that usb_buffer_alloc and usb_buffer_free, which the driver calls on, were renamed to usb_alloc_coherent and usb_free_coherent (respectively) in kernel 2.6.35.

In order to get the driver to compile, edit ../include/os/rt_linux.h and change all instances of "usb_buffer_alloc" to "usb_alloc_coherent" and all instances of "usb_buffer_free" to "usb_free_coherent". From what I can tell, there is only once occurrence of each, on lines 1077 and 1078, respectively.

Make sure you've made the usual changes (enabling WPA Supplicant support in ../os/linux/config.mk and adding the USB ID to ../common/rtusb_dev_id.c) and the driver should compile, install and modprobe just fine.

I also had to blacklist the rt2800 modules as the OS was trying to use them instead. If ifconfig/iwconfig show the device as "wlan0" then it's most likely trying to use the rt2800 module.

Pardon any misplaced or misused terminology, I'm no expert. :)

_EDIT_: I've now also tested and confirmed that the solution works on the Ubuntu 10.10 Beta with kernel 2.6.35-22.

---

### Post by psykodan on 2010-10-10
MinorFreedom's solution also working with D-Link DWA-140 on final Ubuntu 10.10.

EDIT: which is with this driver from ralink: RT2870USB(RT2870/RT2770) 07/09/2010 2.4.0.1 [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

Thx, m8

/Dan

---

