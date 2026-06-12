---
title: "Access to Network Shares from Ubuntu stopped after an IP change"
date: 2012-05-05
forum: Networking &amp; Wireless
---

### Post by transporter_ii on 2012-05-05
I went from a WISP to DSL. The only change that happened was I changed my LAN from 192.168.3.x to 192.168.1.x, which was the default for a new LinkSys X2000 DSL modem/router (yeah, IP address change and new router).

Ubuntu 10.04 LTS with a static IP address on the LAN. Changed it to new IP.

When I uses Places > Network, I now get: Unable to mount location. failed to retrieve share list from server

However, if I go to Places > Connect to Server, and put in an IP address of the Windows share, it works.

I've gone through etc\samba and I can't see anything tied to an IP address and I'm kind of at a loss as to what happened. Places > Network worked before the switch to DSL.

???

---

### Post by transporter_ii on 2012-05-06
Still not working and after hours of searching, just going to give up. I really like Linux, but I can say if just changing an IP address hoses everything up, pretty clear why we haven't taken the world by storm.

Here is what I found, though it did not resolve my issue. It did, however, confirm for me it was probably just changing my IP address that did me in. Who would have thought it. In the year 2012, you can't change an IP address on a computer.

[http://xania.org/200809/samba-problems-after-ip-change](http://xania.org/200809/samba-problems-after-ip-change)

…then there might be a simple explanation. If you’ve recently changed your server’s IP address, there are a number of places where the old IP will still be lurking, possibly causing the issues above.

nmbd caches browse master information in /var/cache/samba/browse.dat — your PDC’s old IP address will be listed here, and when nmbd starts up, it sees it as an existing, distinct domain master browser that then doesn’t respond to it any more. Stop nmbd and then delete the file.

In a similar way the WINS resolution system caches IPs — delete /var/lib/samba/wins.dat.

Restart the samba servers, and hopefully all will be well.

---

