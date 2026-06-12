---
title: "Server losing direct internet connection, symptomless"
date: 2010-01-22
forum: Networking &amp; Wireless
---

### Post by Nanovox on 2010-01-22
Hey all, this has been happening to me for months and it's getting worse.  I have Ubuntu 9.04 server edition set up on a dedicated machine at home to act as my router/firewall to the Internet.  It's set up with two NICs with one going to our cable modem and the other to a LAN switch, and I have Shorewall masquerading for it all.  And so you know, it is a minimal headless console setup.

As of late, it seems that almost every Friday morning the system stops transmitting to/from the Internet.  I can connect locally to the machine, but the system appears as if it is working properly.  I can ping the Internet, but can't connect to websites from the server or from any local computer.  I'm at work when it happens and when I come home I find it's been like this since mid-morning.  I reboot the machine and everything goes back to normal except my dynamic IP addresses change.

I have no idea where to start looking into this problem.  I'm usually pretty good with hacking around Linux, but this seemingly errorless connectivity issue has me baffled.  I don't have any sort of cron jobs running Friday morning that would do this either.  I hate to say my option appears to be reinstalling from scratch, but I just reinstalled this year and with fresh hardware.  Any ideas? Need more information?

---

### Post by gombadi on 2010-01-22
> 
As of late, it seems that almost every Friday morning the system stops transmitting to/from the Internet. I can connect locally to the machine, but the system appears as if it is working properly. I can ping the Internet, but can't connect to websites from the server or from any local computer


A few questions to start with -

When you say you can ping the Internet - what are you pinging? default gateway, remote ip address, remote domain name?

When you say you can't connect what error does it give? No route to host, connection timed out, hostname not found?

---

### Post by Nanovox on 2010-01-22
> **gombadi said:**
> When you say you can ping the Internet - what are you pinging? default gateway, remote ip address, remote domain name?

I could ping google.com with success.

> **gombadi said:**
> When you say you can't connect what error does it give? No route to host, connection timed out, hostname not found?

The last time it happened, I was able to connect to the local server via ssh and do dns lookups, but actually attempting to browse with Lynx gave connection timeouts with sites like Google as well as my own web servers.

---

### Post by gombadi on 2010-01-22
Able to ping google.com but not connect to the site with a web browser.

Sounds like your ISP may be doing something to your link. Can you log into your ISP site and see what they say about your link.

---

