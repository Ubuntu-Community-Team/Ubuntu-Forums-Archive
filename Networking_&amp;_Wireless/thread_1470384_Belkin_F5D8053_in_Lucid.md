---
title: "Belkin F5D8053 in Lucid"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by kyle-buntu on 2010-05-02
i just install our favorite lynx (lubuntu beta 3) after grub frakked up over the weekend in karmic and now im internet-less i used to use ndiswrapper but now i cant find my driver cd BUT it can see my network with the linux drivers, it just cant connect! this is just plain dumb..... :confused:

---

### Post by ljerabek on 2010-05-03
The really easy way around this is to ensure that the correct driver is loaded and installed. Run the following...

test@test:~$ sudo modprobe -l | grep rt28[67].*

**Your output should show these in the output**

kernel/drivers/staging/rt2860/rt2860sta.ko
kernel/drivers/staging/rt2870/rt2870sta.ko

If they are not in the output you should check to see if they are on your system.

test@test:~$ sudo find /* -name "rt28[67]*"

If those ko files are located on your system you should see somthing like the following:

/lib/firmware/rt2860.bin
/lib/firmware/rt2870.bin
/lib/modules/2.6.31-21-generic/kernel/drivers/staging/rt2860
/lib/modules/2.6.31-21-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
/lib/modules/2.6.31-21-generic/kernel/drivers/staging/rt2870
/lib/modules/2.6.31-21-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
/lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt2860
/lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
/lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt2870
/lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
/usr/src/linux-headers-2.6.32-21/drivers/staging/rt2860
/usr/src/linux-headers-2.6.32-21/drivers/staging/rt2870
/usr/src/linux-headers-2.6.32-21-generic/include/config/rt2860.h
/usr/src/linux-headers-2.6.32-21-generic/include/config/rt2870.h

Install the ko files under:
/lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
/lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt2860/rt2860sta.ko

sudo insmod /lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt2870/rt2870sta.ko

sudo insmod /lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt2860/rt2860sta.ko

sudo depmod -a

You are almost done... just check what modules are currently loaded for your belkin.

test@test:~$ sudo lsmod | grep rt28*

If you have "rt2800usb" as a result you will need to black list that driver

sudo gedit /etc/modprobe.d/blacklist.conf

Goto the bottom of the file and add the following line and save the file:

blacklist rt2800usb

Now reboot and you should be all done.

---

### Post by freakazo on 2010-05-07
> **ljerabek said:**
> The really easy way around this is to ensure that the correct driver is loaded and installed. Run the following...

blacklist rt2800usb.....


Thanks, this worked brilliantly!

---

### Post by ljerabek on 2010-05-09
I am glad I could help!

---

