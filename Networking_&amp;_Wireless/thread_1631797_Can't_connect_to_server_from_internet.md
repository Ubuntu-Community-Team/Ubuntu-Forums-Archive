---
title: "Can't connect to server from internet"
date: 2010-11-27
forum: Networking &amp; Wireless
---

### Post by Trevski13 on 2010-11-27
I've been working on setting up a Web/Samba/FTP server for awhile now but only recently did I start working on it again. I'm running Ubuntu 9.10 server (32), previously I had it configured correctly (at least the Web and Samba servers) and was connectible from the Internet (but it the server itself was DHCPed so it broke when the power went out) when I went to reconfigure it today one of the first things I did was set it to a static address 192.168.1.122. I also had to resetup my online DDNS host (through no-ip) but now nothing works... I figured its a problem with my router but I don't see the problem. everything look right.

Port Forwarding:

Web server  80 to 80      192.168.1.122
Webmin   10000 to 10000   192.168.1.122
FTP         21 to 21      192.168.1.122

other things I have set up: (which DID and still DO work)
MS RD     3389 to 3389    192.168.1.121
TVersity 41952 to 41952   192.168.1.109

they work locally but not when I type in my host name or my IP Address directly... this all worked before, and I didn't change much, any suggestions?

Server is an old Dell (real old)
Router is a Linksys WRT54GS (not sure what firmware or model)
DDNS service is No-IP

---

