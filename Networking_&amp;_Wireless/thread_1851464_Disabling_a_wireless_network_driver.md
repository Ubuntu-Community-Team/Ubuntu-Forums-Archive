---
title: "Disabling a wireless network driver"
date: 2011-09-28
forum: Networking &amp; Wireless
---

### Post by MonocleMike2 on 2011-09-28
Apologies for what is probable a very simple question but I have only been using Ubuntu for less than a week.  
I need to disable the onboard wireless card as it is duff and use the external Belkin one.  I therefore added the line 

blacklist ath5k

to 
/etc/modprobe.d/blacklist.conf

and rebooted.

This appears to work and now only the rt73usb driver is listed in lsmod.

Was this the right place to do it?

---

### Post by praseodym on 2011-09-28
Hi,

yes it is. Alternatively you can setup an UDEV-rule according to this example:

[http://ubuntuforums.org/showpost.php?p=11247931&postcount=13](http://ubuntuforums.org/showpost.php?p=11247931&postcount=13)

Replace b43 there with ath5k and remove the "blacklist"-line. This switches to the stick if it is plugged in. Otherwise the internal card is automatically in use. If you want to shut it off permanently, your way is the right one.

---

