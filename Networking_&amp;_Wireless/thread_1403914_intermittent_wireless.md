---
title: "intermittent wireless"
date: 2010-02-10
forum: Networking &amp; Wireless
---

### Post by huviduc on 2010-02-10
Wireless works perfectly sometimes and connects right away when booting up, other times it acts as if wireless has been completely removed as an option. When you click on the network icon in the notification area, there is no option to enable wireless. The only fix I have found is to reboot (sometimes several times). Any ideas?

---

### Post by mikewhatever on 2010-02-11
It's hard to advise anything definite without more info and some research.
Try the following command to restart networking instead of rebooting:

sudo /etc/init.d/networking restart

If successful, just add **/etc/init.d/networking restart** to /etc/rc.local to auto-restart it on every boot.

---

