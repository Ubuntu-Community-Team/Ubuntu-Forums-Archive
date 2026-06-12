---
title: "HELP: nmap conflicting with ufw rules?"
date: 2010-06-11
forum: Networking &amp; Wireless
---

### Post by jackthechemist on 2010-06-11
Starting with zero rules in ufw I enter the following:   sudo ufw default deny # many people advise doing this sudo ufw allow tcp 80 # (HTTP) sudo ufw allow udp 80 # (HTTP) sudo ufw allow tcp 443 # (HTTPS) sudo ufw allow udp 443 # (HTTPS)  but cannot browse. I would prefer a 'default deny' rule, but for now found that the following is the only way I can get Firefox browsing:  sudo ufw default incoming deny sudo ufw default outgoing allow sudo ufw allow tcp 80 # (HTTP) sudo ufw allow udp 80 # (HTTP) sudo ufw allow tcp 443 # (HTTPS) sudo ufw allow udp 443 # (HTTPS)  Any ideas on how to get the 'default deny' working? This latter way feels less secure. Further, a quick nmap scan:  nmap localhost  reveals that several ports (other than 80 and 443) are open! Why is this? How can I close them? I've read several thread discussing closing ports and services and all I've gathered is that very few people understand it well enough to explain it clearly :P  Any suggestion about how to get the ufw default deny working or why the nmap is apparently conflicting with my ufw rules would be appreciated!

---

