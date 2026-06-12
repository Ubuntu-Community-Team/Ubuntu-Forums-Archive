---
title: "Firestarter / Network Sharing"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by asaph_0 on 2009-08-14
Good morning,

I've read many posts on this, tried Firestarter, DNSMASQ/IPMASQ, etc.

Having a lot of difficulties figuring out how to provide visibility across my network; the set up:

Modem --> Laptops [2] (Wireless)
      --> Ubuntu PPC (Wireless) --> Tivo (Wired)
      --> VoIP (Wired)

As it stands, the Laptops and Ubuntu PC can see each other and VoIP; Tivo can get to the internet.

What I can't do is see Tivo from the laptops; Tivo can "see" the laptops, but cannot access any files on them (lists of transfered files come back blank).

Any ideas on how to fix the visibility for this?

Firestarter sharing is on now; Firestarter DHCP with the DNS as the Modem. I've made Tivo --> Internet work with and without Firestarter's DHCP turned on.

Thanks.

---

### Post by 3rdalbum on 2009-08-14
In order to actually share files, you need to have Samba server installed and set up. I recommend using "system-config-samba" to set up Samba.

---

### Post by asaph_0 on 2009-08-14
Already have samba, can share from Ubuntu PC --> Laptop and vice-versa; what I can't do is communicate properly between the Tivo and other network PCs (except for the Ubuntu PC which is sharing it's network connection).

---

### Post by asaph_0 on 2009-08-14
Follow-up --> If I plug one of the laptops into the Ubuntu box's ethernet, it is able to access Internet, but not the other laptop; issue is routing between the main network, and the sub-network created by Ubuntu/Firestarter.

---

### Post by superprash2003 on 2009-08-14
does it work when you disable firestarter? cause you need to allow the tivo ips through the firewall

---

### Post by asaph_0 on 2009-08-14
Nope, doesn't work if I disable; I've allowed all connections on the Tivo IPs, modified the firestarter inbound config, and explicitly allowed connections from the laptop IPs.

This looks like it has more to do with "finding" the Tivo than access; I can't "see" any computers on the network other than the firestarter host if I plug a laptop into the ubuntu-pc's ethernet port.

---

