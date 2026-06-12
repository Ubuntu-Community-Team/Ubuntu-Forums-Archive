---
title: "How do I turn off Cox Net 404 Hijecking/Interception"
date: 2013-03-25
forum: Networking &amp; Wireless
---

### Post by cigtoxdoc on 2013-03-25
I use Cox business Internet; and if you type in an incorrect URL, Cox changes the URL to cox.finder.net.

On my remaining XP machines, I can stop the hijack by forcing use of two DNS servers: 68.105.28.13 and 68.105.29.13.

How do I do this with Ubuntu 12.04?

When I go to the help for network connections (GNOME Nettool Manual 2.7), all it will give me is, "Introduction
This is only a template to get the documentation done. It should not be translated."

John

---

### Post by chili555 on 2013-03-25
I think you can do the same thing in Ubuntu by editing IPv4 settings in Network Manager. Change to DHCP (addresses only) and fill in your DNS nameservers. Please see here: [http://cache.gawkerassets.com/assets/images/lifehacker/2009/12/ubuntu_dns.jpg](http://cache.gawkerassets.com/assets/images/lifehacker/2009/12/ubuntu_dns.jpg)

You may have to restart networking:```
sudo service networking restart
```Or, even better, simply restart!

---

### Post by ac5jw on 2013-03-25
I agree, that is how I did it :guitar:

---

