---
title: "IP Resolving not working? And other such things."
date: 2010-09-05
forum: Networking &amp; Wireless
---

### Post by TheCraneMan on 2010-09-05
Hello everyone, I have a server running Debian - Lenny and I have some weird problems. I want to be able to access the HTTP webpage with just the computer name, or if all else the computer and domain name. This is some other info I have:
```

# hostname -f
debianserver.gateway.2wire.net

# hostname
debianserver

# cat resolv.conf
domain gateway.2wire.net
search gateway.2wire.net
nameserver 192.168.1.254
# ^^Servers IP Address^^
# This was all automatically added by connecting to my ISP

# cat hosts
127.0.0.1       localhost
192.168.1.60    debianserver.gateway.2wire.net  debianserver

# cat hostname
debianserver
```I can access my web page via the IP Address (192.168.1.60), also I can access Webmin, Usermin, FTP, and Samba via this address to but not via a name like [http://debianserver](http://debianserver) or [http://debianserver.gateway.2wire.net ]("http://debianserver.gateway.2wire.net")
My Server has a static IP address that I pretty much manually configured because I needed to load ndiswrapper first.

Thanks in advance to anyone who answers!  -Canute

---

