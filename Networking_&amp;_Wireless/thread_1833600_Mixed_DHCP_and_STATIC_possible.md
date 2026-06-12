---
title: "Mixed DHCP and STATIC possible?"
date: 2011-08-26
forum: Networking &amp; Wireless
---

### Post by Yumi on 2011-08-26
I operate 3 computers running ubuntu 10.04 on a wireless router in my apartment. The router is attached by wire to the neighbors network server which runs Windows, and connects from there to the Internet.

I want to operate 2 computers with the same keyboard and mouse. This requires static IP addresses. Is it possible to configure my subnet with staic IP's while the main network remains on the DHCP server?

If yes, some advice please.

Michael

---

### Post by haqking on 2011-08-26
> **Yumi said:**
> I operate 3 computers running ubuntu 10.04 on a wireless router in my apartment. The router is attached by wire to the neighbors network server which runs Windows, and connects from there to the Internet.

I want to operate 2 computers with the same keyboard and mouse. This requires static IP addresses. Is it possible to configure my subnet with staic IP's while the main network remains on the DHCP server?

If yes, some advice please.

Michael


Yes as long as the Statics are not in the same DHCP scope but yet on the same subnet.

So the DHCP scope for example could be 192.168.0.100-199

so as long as your statics are from 2 to 99 (1 being the router i suspect) or 200-254

or you could make reservations on the DHCP server (router)

---

### Post by e79 on 2011-08-26
+ 1 for what **haqking** said about DHCP reservation.

```
I want to operate 2 computers with the same keyboard and mouse.
```Unless you use some Remote Desktop alike application, you would need a [KVM]("http://en.wikipedia.org/wiki/KVM_switch") in order to manage 2 computers with the same keyboard and mouse without having to unplug-replug it.

---

### Post by Yumi on 2011-08-26
Thank you Haqking, I will discuss the IP setup with my neighbour. According to your advice he has to restrict the range of IP addresses on his server.

e79, I intent to use a program called "synergy" which allows to control 2 computers with 1 keyboard and 1 mouse. But it requires static IP addresses for both machines. See [https://help.ubuntu.com/community/SynergyHowto](https://help.ubuntu.com/community/SynergyHowto).

Michael

---

