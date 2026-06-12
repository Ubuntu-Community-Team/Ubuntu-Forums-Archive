---
title: "Netkworkmanager and static IP"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by Nekrataal on 2006-06-12
Is there any way to set a static IP for wireless conection with networkmanager?

---

### Post by jvictor on 2006-06-12
Ive never used wireless on linux , but i guess It must be possible bcoz finally ur machine talks TCP/IP  to ur router , and the network interfaces take care of talking thru wire or wireless .. So I feel it possible. I would stand corrected on this else.

---

### Post by nanotube on 2006-06-12
try putting the static config into /etc/network/interfaces (eg, using the default gnome net config), and then network manager "presumably" should read that config and set the static ip.

---

### Post by Nekrataal on 2006-06-12
[QUOTE=nanotube]try putting the static config into /etc/network/interfaces (eg, using the default gnome net config), and then network manager "presumably" should read that config and set the static ip.[/QUOTE]

Yes, i could do that, but the idea of Networkmanager is the easy to use when changing my network, so if i do this, will be the same that not using networkmanager since the network in my home have DHCP but at my college not..

---

### Post by nanotube on 2006-06-12
[QUOTE=Nekrataal]Yes, i could do that, but the idea of Networkmanager is the easy to use when changing my network, so if i do this, will be the same that not using networkmanager since the network in my home have DHCP but at my college not..[/QUOTE]
well, in that case, it appears that you are out of luck. if you search the networkmanager mailing lists, it is clear that this is not supported... (i posted a link to those in the other thread about networkmanager)

---

