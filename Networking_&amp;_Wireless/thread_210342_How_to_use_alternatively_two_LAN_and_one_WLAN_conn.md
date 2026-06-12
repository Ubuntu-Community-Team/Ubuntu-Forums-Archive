---
title: "How to use alternatively two LAN and one WLAN connection?"
date: 2006-07-06
forum: Networking &amp; Wireless
---

### Post by Kimmo_S on 2006-07-06
If everyrthing was perfect, I'd have a choice between two locations. Let's call them "home" and "work."

- At work, there is only a wired LAN, with address (and DNS server addresses, this is important) obtainable via DHCP.
- At home, there is a wired LAN, with static IP addresses, static gateway address and two DNS servers different from the ones at work. The old network-admin had the wired LAN covered, with the exception that DNS servers obtained via DHCP at "work" always override manually typed in DNS servers used by the home LAN.
- At home, there is also WLAN, with IP, DNS and gateway obtained via DHCP. I'd like the WLAN card be the default gateway device, using its DNS servers, when the card is inserted. And after the card is removed, the system should go back to using the DNS servers and gateway address of the wired LAN.

WLAN alone now works with the help of NetworkManager.  It is an Atheros card manufactured by SMC, and I use WPA for security.  Problem is that any DHCP activity by either LAN at work or any WLAN overwrites the hand-made DNS settings needed by the network with static IP addresses at home.

My hope is that I could let NetworkManager keep controlling the WLAN, and find some kind of trickery to have network-admin and /etc/network/interfaces deal with the wired networks.  Though it feels like giving up, as a last resort I know I could set up a DHCP server in my firewall machine at home.

Also, if there is a way to have static addresses for the WLAN, please do tell me.

---

