---
title: "Using PuTTY to connect to home computer from work?"
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by helstreak on 2009-05-24
Hi,

When I'm at home I can use PuTTY to connect to my Ubuntu computer but when I'm at work I cannot.  I think it's because I'm using the wrong IP address.  Which IP should I be using when I pull up the information with ifconfig?  Also, do I need to configure the Ubuntu computer in order to allow the "outside" world to access it?

Thank you for your help :)

---

### Post by mellowd on 2009-05-24
If you're using port 22 to ssh in you'll need to forward that port on your router

Then ssh in via your public_ip:22 - the router will forward that to your server

make sure iptables or any other firewall is blocking any communication (moblock for instance)

---

### Post by helstreak on 2009-05-24
> **mellowd said:**
> If you're using port 22 to ssh in you'll need to forward that port on your router

Then ssh in via your public_ip:22 - the router will forward that to your server

make sure iptables or any other firewall is blocking any communication (moblock for instance)

can i get the public ip from formyip.com?

---

### Post by mellowd on 2009-05-24
yeah, or visit [http://www.whatismyip.com/](http://www.whatismyip.com/)

---

### Post by Iowan on 2009-05-24
Do you have fixed (static) IP from your ISP? If you have DHCP address (more likely), you will need a service like no-ip.com or DynDNS.com.

---

