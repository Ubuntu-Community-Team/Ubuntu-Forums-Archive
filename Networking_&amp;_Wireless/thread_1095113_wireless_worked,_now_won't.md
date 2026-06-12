---
title: "wireless worked, now won't"
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by Eman1955 on 2009-03-13
After installing Ubuntu 8.1, connected with eternet, downloaded updates, including the Broadcam B43 wireless driver.  disconnected ethernet. activated the Broadcam driver and wireless was up and running!  Shut down computer for the evening, started Ubuntu this morning and cannot connect wirelessly.  Driver is still there and activated.

Any ideas why no wireless anymore?  Ethernet does work

Thanks
Hawkeye

---

### Post by pytheas22 on 2009-03-13
The next time you boot with the wireless not working, please run these commands, in this order, and post the output:
```

lsmod | grep -e b43 -e wl
lshw -C Network
sudo modprobe b43
sudo modprobe wl
lshw -C Network
```

---

