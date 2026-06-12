---
title: "setting hostnames"
date: 2009-12-08
forum: Networking &amp; Wireless
---

### Post by sdd231163 on 2009-12-08
I have several computers networked through a modem/router. The router assigns dynamic IP addresses that can change each time computers are booted. One computer is on Kubuntu 9.10 - the printer connects to this one. One is a laptop running Arch linux that MUST have dynamic addresses because it has to plug into another network half the time. One computer runs WinXP.

All computers can print to the printer on the Kubuntu box. The Arch linux machine finds the printer even if the IP changes, The windows PC needs to know the IP address to print.

Can I assign a name to the computer that the others can use even if the IP address changes? If so how?

---

### Post by Yoann Juet on 2009-12-08
This can be achieved with dhcp3-server + bind. The DHCP daemon automatically registers and updates 'PTR' and 'A' DNS records on behalf of its dhcp-enabled clients. It's called Dynamic DNS update (DDNS).

---

### Post by chili555 on 2009-12-08
Or, you could set a static IP address on the Kubuntu machine. Please post back if you decide this is the method you prefer.

---

### Post by pricetech on 2009-12-08
Or set your router to always assign a specific IP to that computer's MAC address.

---

### Post by Iowan on 2009-12-08
I like (and use) the static lease option, but **dnsmasq** is another option to tie DHCP and DNS together.

---

