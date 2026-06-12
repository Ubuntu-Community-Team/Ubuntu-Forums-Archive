---
title: "Using my schools internet?"
date: 2011-05-12
forum: Networking &amp; Wireless
---

### Post by polishdude20 on 2011-05-12
My teacher has an old computer that is going to have ubuntu on it and we want to use the school internet for it. 

My school operates on a Novell network so I don't know if ubuntu will detect the network right away and let me use the internet.

All we need is internet access. We don't need any network drives and folders access just internet.

Is there any way to do this?

---

### Post by An Sanct on 2011-05-12
If other computers can access the network, then Ubuntu will have no problem.

Basically: the only thing you need to know are the IP settings (IP address/netmask/gateway and DNS).
If you have DHCP enabled, you don't even need to know that, Ubuntu will connect automatically.

---

### Post by josephmills on 2011-05-12
Also you might want to make sure that there is no mac address filtering going on there. If there is then add the mac number of the computer and it should work out fine. Thanks and I hope that this helps out some how.

---

