---
title: "DNS Server unresolved in wifi networking"
date: 2010-06-17
forum: Networking &amp; Wireless
---

### Post by jmlynn on 2010-06-17
Hi, my ubuntu is unable to resolve the DNS server during wifi network connection.  The wifi router provided IP address, but not the DNS ip.   This usually happen when I am trying to setup wifi in a hotel environment.

When dual boot into Windows XP, wifi connection will resolve the DNS address automatically.

My work around is to first boot up Windows XP (what a drag, 5 minutes for it to come up to issue the ipconfig command), run IPConfig /all so I can write down the DNS address, then boot up Ubuntu, manually configure the Wifi adapter IP address, network mask, gateway address and  the DNS address.  Then I will be able to use wifi under Ubunto.

What do I have to do to configure Ubuntu wireless network adapter to make the connect smooth?

Thanks and appreciate any help so I don't have to suffer the dual boot work-around solution.

Jeff

---

### Post by jmlynn on 2010-06-20
hmmm, no response.  May be I need to restate the problem.

With WinXP, using auto-assign mode, XP OS can got IP address assigned by the DHCP as well as DNS IP address "discovered".

However, under Ubunto V10.x (the latest version), machine IP address is assigned successfully, as I can ping the router.  However, DNS IP was not assigned.  As soon as I changed the IP assignment mode to Manual, and provide the IP addresses for the machine and the DNS retrieved from the WinXP discovery, I can now able to navigate the Net successfully.

Any clues as to what preventing the "auto assignment of DNS" IP address under Ubuntu V10?

Thanks!

Jeff

---

### Post by Iowan on 2010-06-21
For what it's worth (AKA "bump"), I've had a couple of occasions where I needed to boot into Windows, check the internet connection, then reboot into Ubuntu to get wireless access to work (on 9.04).

---

