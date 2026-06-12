---
title: "rt3062 will not trun on after reboot"
date: 2012-07-02
forum: Networking &amp; Wireless
---

### Post by sanqjj on 2012-07-02
My  rt3062 wireless card will not come on after reboot, so I  run the code in the box after I power up and it works. How do I fix this?  running ubuntu 12.04 thank you  	 	 	 	 	 	   sudo modprobe -rfv rt2800pci  sudo modprobe -v rt2800pci

---

### Post by sanqjj on 2012-07-02
this is what i get when I get it to work with code sudo modprobe -v rt2800pci

WARNING: All config files need .conf: /etc/modprobe.d/blacklist.confuname, it will be ignored in a future release.
insmod /lib/modules/3.2.0-26-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko 
insmod /lib/modules/3.2.0-26-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.2.0-26-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.2.0-26-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko 
insmod /lib/modules/3.2.0-26-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko 
insmod /lib/modules/3.2.0-26-generic/kernel/lib/crc-ccitt.ko 
insmod /lib/modules/3.2.0-26-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko 
insmod /lib/modules/3.2.0-26-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko nohwcrypt=1

---

