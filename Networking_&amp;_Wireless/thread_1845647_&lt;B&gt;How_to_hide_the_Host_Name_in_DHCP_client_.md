---
title: "&lt;B&gt;How to hide the Host Name in DHCP client list&lt;/B&gt;"
date: 2011-09-17
forum: Networking &amp; Wireless
---

### Post by rootnet47 on 2011-09-17
[SIZE=4]Hi! I'm new to Linux and I'm using Oneiric Ocelot alpha 3. where I'm using broadband and in the modem's DHCP client list highlights my IP address, Host Name as well as the interface device's MAC address and is also visible to other clients connected in the network. If is there any way to hide my PC then please help.[/SIZE]

---

### Post by pdkta on 2011-10-13
Anyone??????

---

### Post by papibe on 2011-10-13
First I would recommend updating to the Oneiric Ocelot official release (out today).

Regarding your main concern:

If your router is working as a DNS, you can't completed hide from the LAN. First of all, the modem/router has to know you, otherwise you wouldn't have Internet access. Once the router knows you, you are in the router's database of known machines.

If you set your router to give its DHCP clients an external DNS server, the machines only will know each other trough broadcast systems (like NETBIOS and avahi services). If you are able to set that, you should not install samba, disable or uninstall avahi, and (not sure) uninstall winbind.

Another idea would be to set your machine to use an static IP. You would have to also check your router, so that the static address chosen won't be assigned to another client.

**All these ideas are under the assumption that you are the administrator of the router, and thus of the network.**

Does that helps?
Regards.

---

### Post by pdkta on 2011-11-21
Ill give a try thank you _papibe!!!!_

---

