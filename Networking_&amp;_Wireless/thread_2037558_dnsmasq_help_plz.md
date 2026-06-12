---
title: "dnsmasq help plz"
date: 2012-08-04
forum: Networking &amp; Wireless
---

### Post by otherethe on 2012-08-04
Every time I start dnsmasq I get this

Starting DNS forwarder and DHCP server: dnsmasq
dnsmasq: no interface with address 10.8.0.1
 failed!

and if I start openvpn my vps shuts down were I can not connect to it at all via ssh I have to reset it all using the website I followed this guild
[http://library.linode.com/networking/openvpn/debian-6-squeeze](http://library.linode.com/networking/openvpn/debian-6-squeeze)
I've done everything there but yet ran into this problem.

---

### Post by papibe on 2012-08-05
Hi otherethe.

I believe the tutorial uses the address 10.8.0.1 as an example of the current address of the server.

A DHCP server must have a proper static LAN IP that coordinates with DHCP range. Use the one your server is set up with.

Let us know how it goes.
Regards.

---

### Post by zhowen on 2012-08-25
I have the same exact problem. Did you ever figure it out?

---

