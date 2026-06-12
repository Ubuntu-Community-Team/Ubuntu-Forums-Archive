---
title: "Precisely Painful: SSH over LAN requires Internet access?"
date: 2013-07-17
forum: Networking &amp; Wireless
---

### Post by von Corax on 2013-07-17
After upgrading from Lucid LTS to Precise LTS I've noticed that when my Internet connection is down that opening an SSH or SFTP connection between my Mac (Tiger on G4) and my Ubuntu box, in either direction, reliably takes several minutes, to the point where some of my embedded clients will time out rather than connect. I've also verified that when Internet access is restored, opening the same connection takes less than a handful of seconds, rather than minutes.

Can anyone clue me in to just whiskey tango foxtrot is going on here? I haven't been able to find anything in the documentation, but then to be fair I'm not entirely certain what I should be looking for. Since my Internet access is currently down more than up, this is proving to be exponentially inconvenient.

Much obliged,
von Corax

---

### Post by The Cog on 2013-07-17
My guess is that the server is trying to do a reverse DNS lookup to find out the client's name. The easiest way to prove this is to add the client's address and name to /etc/hosts. I'm not sure what a proper fix for that problem might be.

---

### Post by von Corax on 2013-07-17
> **The Cog said:**
> My guess is that the server is trying to do a reverse DNS lookup to find out the client's name. The easiest way to prove this is to add the client's address and name to /etc/hosts. I'm not sure what a proper fix for that problem might be.

I forgot to mention that both machines are DHCP. Normally I use mDNS to find them (Bonjour on the Mac, Avahi on Linux) but I have the same problem if I use bare IP addresses.

EDIT: Also, if it helps figure things out, both machines are running OpenSSH v.3.something.

---

