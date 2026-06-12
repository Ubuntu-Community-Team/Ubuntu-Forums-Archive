---
title: "I could not able to connect to internet"
date: 2012-04-30
forum: Networking &amp; Wireless
---

### Post by SwaroopKunduru on 2012-04-30
I upgraded to 12.04 a couple of days ago it worked well for a day and started giving trouble with wireless. The wireless connection donot work now. It looks like broadcasting and prompt for password for every 5 min and then after 25 min it just disconnects.Please help me with the issue of wireless.

Regards,

Swaroop Kunduru.

---

### Post by SwaroopKunduru on 2012-04-30
For som reason it is working after 2 days of reading in the forum and the following command I have given to get it working.

sudo modprobe -r rt2800pci
sudo modprobe rt2800pci nohwcrypt=1

---

