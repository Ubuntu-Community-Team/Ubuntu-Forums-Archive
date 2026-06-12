---
title: "studio 10.10 access point not associated"
date: 2011-05-21
forum: Networking &amp; Wireless
---

### Post by drhavanger on 2011-05-21
hello all.  i'm using stuido 10.10 and am trying to get wireless to work.  i've used Network Settings to enable the wireless connection with correct ESSID and Network Password, though when i type iwconfig it says Access Point: Not-Associated.  how do i associate with the AP?

---

### Post by poolet on 2011-05-21
use the following on terminal and print the output here::
 
```
iwlist scanning
``````
lsmod
``````
lspci
```

---

### Post by drhavanger on 2011-05-21
thanks poolet...  i sloved it by editing /etc/modprobe.d/intel-5300-iwlagn-disable11n.conf i changed the 1 to a 0

---

