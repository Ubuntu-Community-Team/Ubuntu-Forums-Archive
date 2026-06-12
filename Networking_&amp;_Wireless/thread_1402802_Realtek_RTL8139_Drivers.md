---
title: "Realtek RTL8139 Drivers"
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by Narcyz on 2010-02-09
So i've installed ubuntu 9.10 32 bit version and i dont have internet. Drivers r instaled cause i can see that there is a network connection to make. When i click on it to connect it's connecting like forever and than it says that cable is unplugged. So im typing th lsmod and it shows me that i have 2 drivers to operate my card 8139too and 8139cp. im deleting cp and im reloading network interface but nothing changes. After rebooting linux i have 2 drivers shown in lsmod again.

What can i possiibly do to have internet connection ?


No sugestions on how to fix this problem?

---

### Post by chili555 on 2010-02-09
Please open a terminal and do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add a single line:```
blacklist 8139cp
```Proofread, save and close gedit. Reboot. Are things working correctly now?

---

