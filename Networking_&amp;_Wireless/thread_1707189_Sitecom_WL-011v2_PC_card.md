---
title: "Sitecom WL-011v2 PC card"
date: 2011-03-15
forum: Networking &amp; Wireless
---

### Post by handydoug on 2011-03-15
I am new to ubuntu, installed 10.10 on dell 250n. I am trying to use a Sitecom WL-011v2 wireless PC card. Can someone help me please?

---

### Post by chili555 on 2011-03-15
Please see post #6 here: [http://ubuntuforums.org/showthread.php?t=1197013](http://ubuntuforums.org/showthread.php?t=1197013)

---

### Post by handydoug on 2011-03-27
Thanks for reply.
I had to completely disassemble laptop to resolve heating problems and broken charging jack.
I tried those steps in the link, still not working.
I did get Wicd to list the networks, I can select my wireless router and it says connecting at the bottom of the window. Thats as far as it goes.

---

### Post by chili555 on 2011-03-28
Please try to connect and then run:```
sudo tail -n25 /var/log/syslog
```See if there is any information there about why it won't connect. Have you double-checked the encryption key? Is the network a mixed WPA and WPA2 encrypted network? Ubuntu is a bit difficult to connect to mixed encryption. Can you change the encryption to WPA2 only?

---

