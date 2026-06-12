---
title: "Wireless stopped working after install additional driver &quot;Broadcom STA driver&quot;"
date: 2013-07-31
forum: Networking &amp; Wireless
---

### Post by Gabriel_Santana on 2013-07-31
Everything was ok until i tried to install the Broadcom STA wireless driver from jockey.
I got an error during the installation proccess, and then the wireless stopped working.
If i try to reinstall the driver, connected to internet via cable, i keep getting the same error.


> "Sorry, installation of driver failed, take a look at the log jockey.log"

and in the end of the log it was like this:

> 2013-07-31 17:31:26,599 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2013-07-31 17:31:26,660 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted


i already have installed the b43-fwcutter package

How can i reset the configs back to the standard ones? like when i just installed ubuntu, because it was working fine.
Thanks

---

### Post by praseodym on 2013-07-31
Try to uninstall the driver and its config:
```

sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
```
Reboot

---

### Post by Gabriel_Santana on 2013-07-31
this: 
> sudo apt-get remove --purge bcmwl-kernel-source

worked fine.

the other three .conf files don't exist.

im going to reboot now to see if it changed anything.

**EDIT: 5:56PM**

It worked fine, the wireless network is ok after reboot.
Thank you!

---

