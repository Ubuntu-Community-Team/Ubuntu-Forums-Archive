---
title: "Strange problem with Internet Connection after new ADSL Router Installation!"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by vfafou on 2009-11-09
Hello!

I have installed Ubuntu Karmic 64bit. Three days after new installation, I replaced my ADSL router with a new one. I use static IP's. 
I changed my wireless IP according to the router IP addressing and I connect to the router very normally. But when I try to open a web page into Firefox, I can see the page title on the titlebar (the page is recognized) but it does a time-out and tells me that Server not found. Pinging several addresses (e.g. [www.google.com](www.google.com)), I have 100% success (0% packets lost). As well as, I can't hit the repos in order to install some apps, but pinging the repos addresses, I take the same result: 100% success.

The old WLAN IP's format is 192.168.0.x and 
the new WLAN IP's format is 192.168.1.x

If I try with DHCP, I take the same result - cannot display pages, 100% successful Ping!

Is there any idea?

Thank you in advance! :confused:

---

### Post by Iowan on 2009-11-09
Nameservers are proper in */etc/resolv.conf*? I have an eerie feeling that I've seen this in another thread... somewhere.

---

