---
title: "Compaq w200 wireless card on n610c not working"
date: 2010-01-03
forum: Networking &amp; Wireless
---

### Post by westinman on 2010-01-03
I have a Compaq n610c laptop equipped with a w200 wireless card on the lid of the laptop.  Works fine on XP.  I recently formatted the HDD and installed Ubuntu 9.10.  Wired network works fine and I've updated to the latest updates etc...

However wireless won't work.  I've followed the instructions on [https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200](https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200).  Everything was going fine until I have to compile. I tried the make command and get the following.

Errors:

make -C /usr/src/linux-headers-2.6.31-16-generic M=/home/gsoo/usb KERNELRELEASE=2.6.31-16-generic modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'
  CC [M]  /home/gsoo/usb/orinoco_usb.o
In file included from /home/gsoo/usb/orinoco_usb.c:70:
/home/gsoo/usb/orinoco.h: In function ‘orinoco_spin_unlock’:
/home/gsoo/usb/orinoco.h:188: warning: ‘__raw_spin_unlock’ is static but used in inline function ‘orinoco_spin_unlock’ which is not static
/home/gsoo/usb/orinoco.h:188: warning: ‘raw_local_irq_enable’ is static but used in inline function ‘orinoco_spin_unlock’ which is not static
/home/gsoo/usb/orinoco_usb.c: In function ‘ezusb_request_out_callback’:
/home/gsoo/usb/orinoco_usb.c:568: error: implicit declaration of function ‘warn’
/home/gsoo/usb/orinoco_usb.c: In function ‘ezusb_probe’:
/home/gsoo/usb/orinoco_usb.c:1460: error: ‘struct net_device’ has no member named ‘hard_start_xmit’

Anyone know of a fix or an updated version of this driver for Ubuntu 9.10 ?

Thanks !

Westinman

---

### Post by Cambone on 2010-04-25
I too have this problem. I got the exact same errors when I tried to compile. The guide gives a link to [http://osdir.com/ml/linux-wireless/2009-07/msg00460.html](http://osdir.com/ml/linux-wireless/2009-07/msg00460.html) for those who have 9.10, but that site does not contain any actual directions. 

It would be very helpful if someone more knowledgeable then myself could sum up to me what exactly needs to be done to compile and use orinoco_usb using Ubuntu 9.10 / 2.6.31-20-generic. The part that confuses me (I am very new when it comes to linux/ubuntu) is how exactly to use the 'updates' provided by David Gerard in the guide(which is says you have to do if you are using 9.10).

Any help would be greatly appreciated. If any other info is needed, please let me know.

Cameron
[email]cr4zyfool@gmail.com[/email]

---

### Post by johndoe32102002 on 2010-05-31
I too have this problem and have not been able to get it to work.  In addition, neither lspci or lshw shows the networking device.  There is no option in the BIOS to turn on the wireless card and Fn+F2 does not turn on or off the wireless card in linux (none of the Fn hotkeys work).  Ubuntu, please add support for the w200 wireless card.

---

### Post by Guepard on 2010-12-09
I am also suffering from this problem, and it has stranded me with an old version of Ubuntu.  I used the guide at_ _[https://help.ubuntu.com/community/Wi...ice/CompaqW200]("https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200") to get wireless working for my Compaq w200 wireless card under version 8.10 (Intrepid).  That version is no longer supported, but I am unable to update because the wireless instructions do not seem to work past Jaunty.  Is there anyone who can offer us assistance with this?

Any help would be greatly appreciated.

---

