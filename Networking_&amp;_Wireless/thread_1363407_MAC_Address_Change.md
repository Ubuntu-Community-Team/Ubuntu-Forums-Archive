---
title: "MAC Address Change"
date: 2009-12-24
forum: Networking &amp; Wireless
---

### Post by JDA on 2009-12-24
Please excuse a "newbie's inquiry.

If I have to replace a NIC card or switch from an on-board NIC to a NIC card, how do I get reset the MAC address in Ubuntu Server 8.04?

---

### Post by adam814 on 2009-12-24
I'm not sure I understand what you're asking.  When you replace a NIC the new one will have a different MAC address than the one you replaced.

If you use some kind of MAC-based authentication scheme you can always change the MAC address using ifconfig hw <interface> ether <MAC address of old card>.

I believe 8.04 still uses /etc/network/interfaces so you could probably add a line like this to do it at boot:
> pre-up ifconfig eth0 hw ether <MAC address you want>

---

### Post by aprigiosimoes on 2009-12-24
#vi /etc/network/interfaces

hwaddress ether FF:FF:FF:FF:FF:FF

---

### Post by JDA on 2009-12-24
Thanks - I'll try that and see if it works

---

