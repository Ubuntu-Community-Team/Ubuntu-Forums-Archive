---
title: "3945ABG does not detect A networks"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by pwozney on 2009-09-30
Hi,

I have a 3945ABG card that no longer detects A networks.

I'm not really sure how to troubleshoot this, but I have another laptop that can detect (and successfully connects) to this network so that isn't the issue.

I can connect without a problem to B/G networks.  Is there any way to see if there is some problem with the A radio on my card?

Thanks!

Paul

---

### Post by chili555 on 2009-09-30
Please open a terminal and do:```
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
sudo iwlist wlan0 scan
```Please post back and let us know the result.

---

