---
title: "MAC addresses getting mixed"
date: 2010-03-31
forum: Networking &amp; Wireless
---

### Post by harky on 2010-03-31
I am running Karmic with a default networking setup using both wired and wireless connections.  Both are setup in a DHCP configuration and the wireless is authenticated.

NETWORK ENVIRONMENT:
1. I use both wired and wireless as I move from desk to meeting rooms frequently
2. Wireless and wired are on different LAN segments.
3. Wireless and wired have static IP Addresses configured at the DHCP server
4. This is a fairly high-security environment and the MAC address is tied to the IP address

THE ISSUE:
Periodically, the MAC address for my wired NIC ends up showing up on the LAN using my wireless IP address.  This causes an automatic block to be put in at the router for my wireless IP, thus dropping all my packets.  However, I don't necessarily find this out until after it has occurred and I go to use wireless and can't because my IP is blocked. Since I don't know when it occurs, I don't know if it's my wired NIC using my wireless IP or if it's my wireless NIC using my wired MAC address.

Any suggestions would be appreciated. It would be nice to avoid getting blocked.

---

### Post by Schitso on 2010-03-31
Your MAC addresses shouldn't be changing by themselves, and there's no way that the DHCP negotiations for each of the two would get mixed up. I'm stumped.

---

