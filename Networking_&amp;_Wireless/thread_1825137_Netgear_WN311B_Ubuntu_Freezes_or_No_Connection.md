---
title: "Netgear WN311B Ubuntu Freezes or No Connection"
date: 2011-08-14
forum: Networking &amp; Wireless
---

### Post by ravensqu on 2011-08-14
I hope you guys can help me, I am trying to get a Netgear WN311B pci wireless adapter to work in Ubuntu 11.04 x64.

When using the original Broadcom STA wireless driver found in "Additional Drivers" I am able to connect to wireless networks, but after very minor network traffic ubuntu completely freezes up requiring a hard-reboot.

Following the cue from [http://ubuntuforums.org/showthread.php?t=1764126](http://ubuntuforums.org/showthread.php?t=1764126) I have attempted to install the b43 driver instead of the STA driver. After using the following commands taken from [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx),
```
sudo apt-get remove bcmwl-kernel-source
``````
sudo apt-get install b43-fwcutter firmware-b43-installer
``` and rebooting, I am unable to see the b43 drivers in "Additional Drivers" and am unable to see any wireless networks from my adapter.

I appreciate any help you can give to get this working. I am relatively new to Ubuntu and could really use the wireless.

-RavenSqu

---

