---
title: "Ubuntu Server 10.04 print server firewall rules"
date: 2011-10-26
forum: Networking &amp; Wireless
---

### Post by snobskidoo on 2011-10-26
Hi

I am running a headless ubuntu 10.04 LTS server for media / printing / apache etc.  and recently enabled the firewall.  I have managed to set up rules for the file / web / ftp sharing but cannot get the printer to run.

I can access the CUPS server via chrome on my client XP machine on port 631 (after opening it ofc), but no documents will print.

Any clues as to which ports I need to open on the server ufw?

Thanks for all help/advice.

ps (for those with an opinion).  I wanted the firewall as I am exposing the box to the internet and have some ftp shares set-up (more for practice than practical use) and the box is behind my netgear hardware router.  Am I over complicating things or should I persist?

---

### Post by snobskidoo on 2011-11-01
After some further investigations I have changed the firewall rules to:

If protocol is TCP and destination port is 22	
Accept	If protocol is TCP and destination port is 10000	
Accept	If protocol is TCP and destination port is 20	
Accept	If protocol is TCP and destination port is 21	
Accept	If protocol is TCP and destination port is 80	
Accept	If protocol is TCP and source is 192.168.0.0/24 and destination is 192.168.0.0/24 and destination port is 445	
Accept	If protocol is TCP and destination port is 20000	
Accept	If protocol is ICMP and ICMP type is echo-request	
Accept	If protocol is TCP and source is 192.168.0.0/24 and destination is 192.168.0.0/24 and destination port is 631	
Accept	If protocol is UDP and source is 192.168.0.0/24 and destination is 192.168.0.0/24 and destination port is 631	
Accept	If protocol is UDP and source is 192.168.0.0/24 and destination is 192.168.0.0/24 and destination port is 1024:65535

Which has fixed it, but obviously the last rule is a bit slack. Something to do with the request automatically generating on a random number high port.

If anyone comes up with a neater solution, would be glad to hear it.

---

