---
title: "VPN laptop problem when connected to LAN"
date: 2011-10-10
forum: Networking &amp; Wireless
---

### Post by plo on 2011-10-10
I have a fully working OpenVPN setup using encryption keys via a dlinkddns adress and portforwarding through my router to my server on my home LAN.
The problem is that when I connect my laptop directly to my LAN I cannot access Internet or other LAN resources without disabling the tap0 device ('sudo ifconfig tap0 down') manually.

eth0 and tap0 are assigned the same IP adress causing a conflict (I guess).

Can I add something to /etc/network/interfaces so this is done automatically? Or can I change the VPN config so it only enables when not on my home lan?

Thanks
/Palle

Ubuntu 11.04

---

