---
title: "DHCPD ignore declines not working?"
date: 2009-07-19
forum: Networking &amp; Wireless
---

### Post by ScottEChapman on 2009-07-19
So, on my network, I need to ignore the DHCPDECLINE response I am getting.

I have tried the following in my dhcp.conf file:
```
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.200 192.168.1.250;
  option broadcast-address 192.168.1.255;
  option routers 192.168.1.1;
  ignore declines;
}
```

But the responses are still preventing the client from getting the IP address.

Any ideas what I am doing wrong?

---

### Post by ScottEChapman on 2009-07-19
Just to be clear, here is the DHCP log:
```
Jul 19 19:51:06 DomainController dhcpd: DHCPDISCOVER from 00:23:a2:8f:00:ef via eth0
Jul 19 19:51:06 DomainController dhcpd: DHCPOFFER on 192.168.1.101 to 00:23:a2:8f:00:ef via eth0
Jul 19 19:51:06 DomainController dhcpd: DHCPREQUEST for 192.168.1.101 (192.168.1.75) from 00:23:a2:8f:00:ef via eth0
Jul 19 19:51:06 DomainController dhcpd: DHCPACK on 192.168.1.101 to 00:23:a2:8f:00:ef via eth0
Jul 19 19:51:06 DomainController dhcpd: DHCPDECLINE of 192.168.1.101 from 00:23:a2:8f:00:ef via eth0: not found
```

---

