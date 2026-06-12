---
title: "DHCP Server and Client Setup Files"
date: 2012-06-21
forum: Networking &amp; Wireless
---

### Post by Ankit Mathur on 2012-06-21
Hello to all,
I am using Ubuntu 11.04 and setting-up DHCP clients and servers here at my end. I have 3 NIC cards with my server. 1 of them is inbuilt and other 2 are externally installed (1 for input and other for output). 
I have configured the isc-dhcp-server, interfaces and dhcpd.conf files here on my server. The server starts successfully. BUT, **still the server is not able to connect with client**. Can you please send me the exact correctly configured files for both server and client so that I can correct the mistakes in the files at my end.

---

### Post by SeijiSensei on 2012-06-21
With multiple interfaces on the server, you usually need to tell dhcpd which one to listen on.  To do so,
edit as root with sudo the file /etc/default/dhcp3-server and add the line:

```
INTERFACES="eth1"
```

replacing eth1 with the interface facing the network shared with the client machines.  Then restart dhcpd.

---

