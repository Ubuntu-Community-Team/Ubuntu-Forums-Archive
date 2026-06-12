---
title: "Restricted HW drivers Dont function need help"
date: 2009-07-18
forum: Networking &amp; Wireless
---

### Post by CheresZabor on 2009-07-18
Hello,
So i have upgraded to 9.04 a while back and just now reinstalled it again on my asus 1000HA. And for the past day have been trying to get the restricted hardware driver for the wireless card (Ath. AR5700EG) to work. 

Now every time i try to activate the restricted drivers and restart i completely "loose" the wireless device and neither ifconfig nor iwconfig is show any wireless devices present. Does anyone have any idea on how to fix this?

Thanks

---

### Post by irishlyrucked on 2009-07-18
try blacklisting ath_hal and ath_pci.  then use ndiswrapper to install the windows driver.

---

