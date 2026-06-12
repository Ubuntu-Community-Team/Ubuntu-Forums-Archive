---
title: "Can't surf the web"
date: 2012-12-15
forum: Networking &amp; Wireless
---

### Post by marsheng on 2012-12-15
I've just installed a fresh copy of Ubuntu and I manually set the IP addresses for the cards on our network. I can connect to the windows network and printers but I cannot surf the web. Pinging [www.google.com](www.google.com) says Cannot find address. The router at 10.0.0.1 does ping as well as the printer 10.0.0.21. 

Not sure where to go from here ?

---

### Post by chadk5utc on 2012-12-15
when you sudo ifconfig do you get similar:
> auto eth0
iface eth0 inet static
address 10.0.0.100
netmask 255.255.255.0
gateway 10.0.0.1

---

### Post by Cheesemill on 2012-12-15
How did you set up the IP address, by using Network Manager or by editing the /etc/network/interfaces file?

If you can ping other devices but not resolve names it's more than likely an issue with DNS.

---

