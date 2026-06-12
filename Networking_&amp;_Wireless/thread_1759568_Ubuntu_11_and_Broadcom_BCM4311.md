---
title: "Ubuntu 11 and Broadcom BCM4311"
date: 2011-05-15
forum: Networking &amp; Wireless
---

### Post by arjones85 on 2011-05-15
Has anyone had success getting this wireless card to work with the Broadcom STA drivers in the Additional Drivers section? I have read through several threads, the driver shows as "enabled" in the additional drivers section, but the card is not detected by Ubuntu or any third party wireless apps I download.

Any troubleshooting steps that can be taken when the driver actually shows as enabled?

---

### Post by nm_geo on 2011-05-15
> **arjones85 said:**
> Has anyone had success getting this wireless card to work with the Broadcom STA drivers in the Additional Drivers section? I have read through several threads, the driver shows as "enabled" in the additional drivers section, but the card is not detected by Ubuntu or any third party wireless apps I download.

Any troubleshooting steps that can be taken when the driver actually shows as enabled?

You might try this link. 
[http://ubuntuforums.org/showthread.php?t=1700897](http://ubuntuforums.org/showthread.php?t=1700897)
Message 5


 I have the 
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 01)

and use b43 driver quite well.

---

### Post by arjones85 on 2011-05-25
Thanks! That actually worked! b43 working without an issue now.

---

