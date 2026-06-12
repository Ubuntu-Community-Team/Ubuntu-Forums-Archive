---
title: "specific DHCP configuation"
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by aswin on 2011-02-23
Hi all,
Due to the nature of my application, I have to configure a DHCP server that assigns addresses that end with bits '10'. The IP addresses must be of the type 10.x.y.z/22

So some examples of IP addr to be assigned:

10.1.2.2
10.12.18.14
10.6.155.6
10.121.76.22
10.5.45.18
...etc

As you see all the IP addr end with '10' binary bits.

How do I write the dhcpd.conf file?

Thanks a lot in advance

---

### Post by SeijiSensei on 2011-02-23
Just specify the correct network address and netmask in the "subnet" declaration of dhcpd.conf.

---

