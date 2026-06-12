---
title: "Need ideas for home network setup"
date: 2013-02-13
forum: Networking &amp; Wireless
---

### Post by eljefegenial on 2013-02-13
I have Ubuntu set up as a home server on a G4 PowerPC. I'm sure someone has had a similar problem before. The D-Link router we have spits out IPs via DHCP, and so the Ubuntu server gets a new IP every time, which is obviously a problem.

I could set up static IPs, but I'd also like to be able to have hostname resolution. Apart from setting up static IPs and updating /etc/hosts on each PC is there anything else I can do? DNS server setup would probably be overkill, though it might be fun.

---

### Post by ali abry on 2013-02-13
looks like you did the only way (using /etc/host )
installing dns server isn't that much hard you can make it easier by using control panels like [webmin]("http://ubuntuforums.org/www.webmin.com/")  or [ispconfig]("http://ubuntuforums.org/www.ispconfig.org/").

---

### Post by lykwydchykyn on 2013-02-13
Depends on the capabilities of your D-link.  Some routers let you reserve or assign IP addresses by MAC address. This would be a good solution here.

You can also set up dnsmasq on your server, which is a dead simple DNS server that just uses the /etc/hosts file on the server to resolve names.  I did this for a while, but it requires that your router lets you specify DNS information (my new one doesn't).

How many machines do you have that updating /etc/hosts is such an issue?

---

### Post by matthewboh on 2013-02-13
I was under the impression that avahi would take care of that. For example, I have a WRT54G router, a server that I set up with a static IP address and 4 additional PC's on the network. I just use "computer name".local and can get to every last one of them.

It sort of magically worked.

---

### Post by eljefegenial on 2013-02-13
> **lykwydchykyn said:**
> Depends on the capabilities of your D-link.  Some routers let you reserve or assign IP addresses by MAC address. This would be a good solution here.

You can also set up dnsmasq on your server, which is a dead simple DNS server that just uses the /etc/hosts file on the server to resolve names.  I did this for a while, but it requires that your router lets you specify DNS information (my new one doesn't).

How many machines do you have that updating /etc/hosts is such an issue?

The D-Link is quite capable I think as I installed dd-wrt on it, although I haven't updated that in a while. DD-WRT has a ton of options, but so far I've only found DHCP server or DHCP forwarder.   I'll have to mess around with that a bit. 

I only have four machines so it's not an issue at all, but I thought that perhaps there would be a better, more automated way :-)

---

### Post by willy53 on 2013-02-13
You may find what you're looking for as static DHCP. As previously mentioned that will reserve IPs by MAC address.

---

### Post by eljefegenial on 2013-02-13
Thanks a lot all. DD-WRT does wonders.

I set up static DHCP and I'm working on DNSMasq as there seem to be some issues.

---

