---
title: "Changing auto-acquire VPN route details"
date: 2009-08-11
forum: Networking &amp; Wireless
---

### Post by darragh on 2009-08-11
Hi I have a VPN client setup using the network manager, I guess with vpnd, however my IP and route details are acquired automatically and it's a bit of a problem because it will route everything! (0.0.0.0 to vpn-gw) I only need to be able to access the DNS and mail server IP (which I know) and the rest route over the local gateway

Using the network manager GUI one can set static IP and Route details, however when the connection is made this is ignored because of the DHCP client, 

Is there a way I can explicitly allow only access to a route over the vpn without acquiring setting from the vpn-dhcp server?

---

