---
title: "HP mini wireless device driver not installed"
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by masksalesman on 2009-12-14
hello there! 
i have an netbook HP mini, and the driver for the wifi device is not installed. where can i find it and how can i install the driver?? when i used the live ubuntu netbook remix 9.1 cd he told me to install the "restricted drivers", i just accepted and everything worked fine. But now that ubuntu is installed he dont ask me to do it, even when i manually open the tool "hardware driver"!

---

### Post by Brandon Williams on 2009-12-15
Does the HP mini use the same Broadcom wireless chip as the Dell mini? If so, then you'll need an ethernet cable. Plug your mini into your router to get an address via ethernet. Then 'sudo apt-get install bcmwl-kernel-source'. You might have to use 'System->Harware Drivers' to enable the Broadcom STA driver after that.

---

