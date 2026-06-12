---
title: "Get IP from DHCP"
date: 2010-08-16
forum: Networking &amp; Wireless
---

### Post by infestor on 2010-08-16
apparently someone on my LAN is running his own DHCP server (by mistake i assume) and broadcasting an address (it is 192.168.1.155) prevents me to connect to the 'real' DHCP server (**195.249.186.1**) thus the **internet**. how can i connect to my usual DHCP server? what commands should i use?

---

### Post by infestor on 2010-08-16
apparently someone on my LAN is running his own DHCP server (by mistake i assume) and broadcasting an address (it is 192.168.1.155) prevents me to connect to the 'real' DHCP server (195.249.186.1) thus the **internet**. how can i connect to my usual DHCP server? what commands should i use?

---

### Post by K.Mandla on 2010-08-16
Similar threads merged.

---

### Post by Iowan on 2010-08-16
Check **man dhclient.conf**. One of the options sounds right:>         reject ip-address;
       The reject statement causes the  DHCP  client  to  reject  offers  from servers  who  use  the specified address as a server identifier.   This can be used to avoid being configured by rogue  or  misconfigured  dhcp servers, although it should be a last resort - better to track down the bad DHCP server and fix it.

---

### Post by capscrew on 2010-08-16
> **infestor said:**
> apparently someone on my LAN is running his own DHCP server (by mistake i assume) and broadcasting an address (it is 192.168.1.155) prevents me to connect to the 'real' DHCP server (**195.249.186.1**) thus the **internet**. how can i connect to my usual DHCP server? what commands should i use?

Is this your LAN exclusively?  If so then I would have a firewall at the edge of the LAN (i.e. gateway or router).  If this is a shared LAN, who is administering it?

---

### Post by infestor on 2010-08-17
> **capscrew said:**
> Is this your LAN exclusively?  If so then I would have a firewall at the edge of the LAN (i.e. gateway or router).  If this is a shared LAN, who is administering it?
it is my dorm's LAN

---

### Post by infestor on 2010-08-17
> **Iowan said:**
> Check **man dhclient.conf**. One of the options sounds right:

I guess that would work

---

