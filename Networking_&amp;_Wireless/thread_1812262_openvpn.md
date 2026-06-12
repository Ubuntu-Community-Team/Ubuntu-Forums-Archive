---
title: "openvpn"
date: 2011-07-26
forum: Networking &amp; Wireless
---

### Post by sandsjh on 2011-07-26
I am ashamed of myself for not knowing this answer, but to no avail.

I have my router, and behind that several PCs. One of those PCs is an Ubuntu box. If I create a VPN on that, will I be able to connect to all the other PCs, or do I have to have the PCs all stacked behind the Ubuntu, like Ubuntu is a firewall.

My goal in this is to access network shares and remote desktop on my M$7 box. Albeit Win 7 has PPTP built in, I have read where it's not good to run that, but expert opinions here will be taken into account.

router
pc - pc - pc - ubuntu


does it have to be
router
ubuntu
pc - pc - pc

TIA.

---

### Post by sandsjh on 2011-07-28
Anyone?

---

### Post by sandsjh on 2013-01-21
It has to be
router
ubuntu
pc - pc - pc


Thanks to all that answered.

---

### Post by ahallubuntu on 2013-01-21
You can setup OpenVPN on one of the computers on your network and you should have access to all of the other computers on the local network.  (This may be an option in the OpenVPN server config file, but the default as I recall is to let you see all the local computers.)  You don't have to make the OpenVPN server a "firewall" for the rest of the  machines.  However, if your router can run DD-WRT firmware, look into installing OpenVPN directly on the router, so you don't need to install OpenVPN on any of the computers.

---

### Post by howefield on 2013-01-21
Old thread closed.

---

