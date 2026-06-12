---
title: "One command configuration for UFW?"
date: 2013-06-07
forum: Networking &amp; Wireless
---

### Post by chrishyder on 2013-06-07
Hi guys,

I've been struggling to get DLNA working with my installed version of Ubuntu 12.04 server.  Regardless of the myriad ports that I open, devices aren't able to see the the Plex server advertisement.

The server is used purely for file sharing within my local network - I don't want any inbound access allowed from the internet.  Rather than having rules for each service/port (e.g OpenSSH, Samba etc.), can any of you see a problem with issuing the following:

sudo ufw default deny
sudo ufw allow from 192.168.0.0/24

I'm assuming that this blanket rule will allow access to the internet but block all inbound traffic while allowing full access to local network clients.

Are there any real security issues with having the firewall configured in this manner?

Any advice would be most appreciated - thanks. :p

---

