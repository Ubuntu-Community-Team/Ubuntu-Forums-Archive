---
title: "Ubuntu on our school network has wifi issues BCM4313"
date: 2012-05-29
forum: Networking &amp; Wireless
---

### Post by biodojo on 2012-05-29
I have some machines running 11.04 and they connect to wifi, get an IP address, and will connect for awhile. Then after awhile some will randomly not be able to ping anything. They say they are connected on the network manager applet, they have an IP, dmesg | grep wlan doesn't report any disconnects. Also the wireless access point and the DHCP server says the device is connected. 

While I don't think it is specific to Ubuntu (because they work fine on my home network), it might be some interaction between Ubuntu and our network settings (because other devices connect to our network wifi). I want to help troubleshoot the issue. 

What could cause a device to have an IP but not be able to ping?

Wireless adaptor: BCM4313
Driver: brcmsmac
model: Acer Aspire One 722

---

### Post by praseodym on 2012-05-29
Hi,

this device works with the Broadcom-STA driver, which you can install (via cable) from "additional drivers". The following modules need to be blacklisted:

```
echo -e "blacklist bcma\nblacklist brcm80211\nblacklist brcmsmac" | sudo tee /etc/modprobe.d/blacklist-bcm.conf 
```
This is one line! Reboot after that. From Ubuntu 12.04 it works with the native b43 driver.

---

