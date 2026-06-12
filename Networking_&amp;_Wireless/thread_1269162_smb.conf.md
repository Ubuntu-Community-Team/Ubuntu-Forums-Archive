---
title: "smb.conf"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by njb on 2009-09-17
I've changed the name of my local workgroup in 
/usr/share/samba/smb.conf
but still havong workgroup as workgroup name even after rebooting.   

:confused:

NjB

---

### Post by swerdna on 2009-09-18
Try changing it in /etc/samba/smb.conf. Reboot to make it communicate that to the LAN.

[Ref for more]("http://ubuntu.swerdna.org/ubulanprimer.html")

---

### Post by njb on 2009-09-18
> **swerdna said:**
> Try changing it in /etc/samba/smb.conf. Reboot to make it communicate that to the LAN.

[Ref for more]("http://ubuntu.swerdna.org/ubulanprimer.html")

Thank you it worked  :lolflag:

---

