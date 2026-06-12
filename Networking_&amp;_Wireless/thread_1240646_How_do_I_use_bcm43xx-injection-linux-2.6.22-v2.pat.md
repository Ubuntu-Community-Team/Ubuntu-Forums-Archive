---
title: "How do I use bcm43xx-injection-linux-2.6.22-v2.patch with ubuntu v9.04 ?"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by 1080p on 2009-08-14
How do I use bcm43xx-injection-linux-2.6.22-v2.patch with ubuntu v9.04 ?

---

### Post by t0mppa on 2009-08-15
How about you go aircrack's website and read the [tutorial]("http://aircrack-ng.org/doku.php?id=patching")? Or if you're feeling as lazy as when you posted here instead of going to the above address yourself to learn what's required you can just edit the files manually: lines beginning with + are added and the ones beginning with - are removed and the @@'s mark the line numbers.

Also, bcm43xx is deprecated (as it uses the old ieee80211 stack) in favor of b43 (that uses the newer mac80211 stack).

---

### Post by 1080p on 2009-08-17
So I need to download the driver from, [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
 
then patch it & compile it ?

---

### Post by t0mppa on 2009-08-17
No. That's a completely different driver. There are three different drivers available for Broadcom cards on Linux:
[LIST=1]
[*]**bcm43xx** is an older driver, reverse engineered from the closed source drivers used on Linksys routers, that still relies on firmware (closed source piece of code for operating the chip)
[*]**b43** is a newer version of the above, updated for the newer wireless stack that's on its way to becoming a de facto standard on Linux wireless drivers
[*]**STA** (that you referred to) is the newest one, made by Broadcom (fully closed source) and it only works with a few specific chips
[/LIST]
If you use the STA, you can't patch it with an update to bcm43xx and the STA doesn't support monitor mode or packet injection.

Thus if you're using a recent version of Ubuntu, the easiest choice is to go with b43, that supports packet injection and is the default driver for Broadcom chips.

But if you really insist on using the patch in the topic, you'll have to use bcm43xx. Can get more info on that from [here]("http://bcm43xx.berlios.de/").

---

### Post by governorphd on 2009-09-24
The tutorial  'How to make b43 packet injection work states:

"Hi guy's here is the complete guide on how to make the b43 (driver for the Broadcom wireless chips) packet injection and aircracking 802.11a/b/g/n work with kernel 2.6.24 (ubuntu 8.04 / ubuntu ultimate edition 1.9 )"

I have Ubuntu, 9.04,  desktop.  My kernel is 2.6.28-15-generic.  

Do I need to download and install a patch?  If so, which one for my kernel version?

If not how do I apply the tutorial to my version?  

I have been reading a lot.  But most of it is new to me, as is Ubuntu, so I need step by step instructions as are outlined in the tutorial, for kernel 2.6..28-15-generic.

I have installed the b43 driver.  I have installed Kismet.  Now I need help with Aircrack

---

