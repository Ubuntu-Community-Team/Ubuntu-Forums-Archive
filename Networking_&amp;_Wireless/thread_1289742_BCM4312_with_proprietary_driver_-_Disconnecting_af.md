---
title: "BCM4312 with proprietary driver - Disconnecting after a while"
date: 2009-10-12
forum: Networking &amp; Wireless
---

### Post by DanPaulCiocan on 2009-10-12
Hi, please help me with this issue. I have a Dell Inspiron Mini 12 with Ubuntu 9.04 installed (with all the updates). I have this wifi card:
```
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
``` and I'm using this driver:
```
Broadcom 802.11 Linux STA driver
```After a while (it could be 30 minutes or 3 hours) my computer disconnects from Internet and I'm not able to reconnect again. It asks for my WPA key, but it's already written in the box. I click on the button to connect and after 30 seconds it asks me again for the WPA key. I have to restart my computer in order to be able to use my Internet again. With Windows, it's working correctly. Maybe this is a bug caused by the driver? Do you know how can I fix this problem, or is it better to use ndiswrapper? I searched in doc.ubuntu-fr.org and there they say that this card should work correctly on Ubuntu Jaunty... Thank you very much for reading this, and please answer me if you know what is the problem.

EDIT: After I installed linux-backports-modules-jaunty, it worked correctly.

---

