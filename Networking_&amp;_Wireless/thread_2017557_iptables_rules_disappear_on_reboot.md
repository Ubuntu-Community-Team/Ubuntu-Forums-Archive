---
title: "iptables rules disappear on reboot"
date: 2012-07-05
forum: Networking &amp; Wireless
---

### Post by NilPointer on 2012-07-05
Recently I've decided to get rid of Firestarter and control firewall rules manually. I removed it and applied my rules. However, it seems rule tables don't want to survive reboot. After reboot tables are clean. Is there some way to keep rules?

---

### Post by alexlpratt on 2012-07-05
Yep! It appears that your config is being blown away by default settings when the startup scripts run. Here's a great method for Ubuntu which worked great for me. [IptablesHowTo]("https://help.ubuntu.com/community/IptablesHowTo#Configuration_on_startup") (I used method#1.) Let me know if you have any further questions!

---

### Post by NilPointer on 2012-07-05
My net interface (eth0) wasn't mentioned in /etc/network/interfaces, so i had to assign pre-up to lo interface. Seems like it worked. Thanks!

---

### Post by alexlpratt on 2012-07-05
Excellent! Glad to hear.

---

