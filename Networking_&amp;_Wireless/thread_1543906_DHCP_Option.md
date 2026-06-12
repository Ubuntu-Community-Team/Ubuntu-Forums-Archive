---
title: "DHCP Option?"
date: 2010-08-01
forum: Networking &amp; Wireless
---

### Post by MAFoElffen on 2010-08-01
Seems my router requires that DCHP is turned on.  Someone at the Cysco Forum said they think Ubuntu's default is with this off....

Where in Ubuntu 10.04 do I go to check what this option is set at and what do I do to change if it's not enabled?

---

### Post by Iowan on 2010-08-01
Network Manager defaults to DHCP access, but it can be changed to static by editing connections.

---

### Post by MAFoElffen on 2010-08-02
> **Iowan said:**
> Network Manager defaults to DHCP access, but it can be changed to static by editing connections.
In 10.04... So Administation>Network Tools>Device>Configuration? I see DNS, but not DHCP.

Oh... I get it now- If it has a "Static IP Address," then DHCP is disabled.  If it it assigned dynamically, then DHCP is what assigns it.

Thanks.

---

