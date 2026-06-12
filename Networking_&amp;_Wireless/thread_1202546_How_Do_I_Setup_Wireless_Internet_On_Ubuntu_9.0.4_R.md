---
title: "How Do I Setup Wireless Internet On Ubuntu 9.0.4 Running On VMWare Server."
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by mine070 on 2009-07-02
Any Idea? I have no idea how to. I have Windoes Vista 32 Bit.

---

### Post by scorp123 on 2009-07-02
Underneath VMware there is no "wireless". All an OS inside a virtual machines gets to see are "AMD PCnet" devices.

If you want a virtual OS to go out via wireless you have to configure VMware to bridge the virtual AMD ethernet interface the virtual machine will use to the WiFi interface of the server. For the VM underneath it will still all look as if it's going out via ethernet cable.

---

### Post by mine070 on 2009-07-03
> **scorp123 said:**
> Underneath VMware there is no "wireless". All an OS inside a virtual machines gets to see are "AMD PCnet" devices.

If you want a virtual OS to go out via wireless you have to configure VMware to bridge the virtual AMD ethernet interface the virtual machine will use to the WiFi interface of the server. For the VM underneath it will still all look as if it's going out via ethernet cable.
Well I Switched To VMWare Player. Is it diffrent for Player?

---

