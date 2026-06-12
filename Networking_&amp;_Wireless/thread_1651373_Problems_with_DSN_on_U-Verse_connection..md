---
title: "Problems with DSN on U-Verse connection."
date: 2010-12-23
forum: Networking &amp; Wireless
---

### Post by cdysthe on 2010-12-23
Hi,

I recently got a U-verse conncetion. When I connect to the 2Wire 3600 HGV modem using DHCP DNS is set to 192.168.1.254 in Network Manager which is the routers own IP address and not to the DNS server address the modem uses which is:

Primary DNS	68.94.156.1
Secondary DNS	68.94.157.1

This doesn't cause problems for web browsing, but it breaks apt with the following error message when I run sudo apt-get update

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

The only way around this problem is to set DNS manually in Network Manager (using Google's or OpenDNS) for the wireless connection I am using. When I do this apt works fine and I can update without errors.

I'm no network guru so I was wondering why DNS is set to the router/modems own IP and not to the DNS servers actually used? Is this a modem/router problem or is it Network Manager setting it up wrong? Since I do not have any Windows machines around I can not check if the same things happens there.

---

### Post by dineshs on 2010-12-23
Have you tried this?
Set Network manager for [COLOR="Blue"]Automatic (DHCP) addresses only[/COLOR] and give DNSs seperated by a comma in the DNS servers field

---

### Post by cdysthe on 2010-12-23
> **dineshs said:**
> Have you tried this?
Set Network manager for [COLOR="Blue"]Automatic (DHCP) addresses only[/COLOR] and give DNSs seperated by a comma in the DNS servers field

Yes I have, and it works, but I have a lot of machines (laptops) coming and going on my network so it's a hassle having to remember to set their DNS all the time so that updates will work. Also, I would really like to know if anyone could come up with an explanation why this modem/router uses it own IP for DNS instead of the servers it's actually using. I've had many routers/modems up through the years, but this is new to me and there's no way to configure it to do the "normal" thing.

---

