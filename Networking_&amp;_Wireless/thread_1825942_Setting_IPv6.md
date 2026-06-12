---
title: "Setting IPv6"
date: 2011-08-16
forum: Networking &amp; Wireless
---

### Post by nox007 on 2011-08-16
how to setting IPv6 in ubuntu  router?
I use ubuntu 10.10..
i have tried to use "/sbin/ifconfig/ eth0 inet6 add 3ffe:ffff:0:f101::1/64" but after reboot the configuration is lost..
please help me

---

### Post by lemming465 on 2011-08-16
First, I recommend using the newer "ip -6 addr add 3ffe:ffff:0:f101::1/64 dev eth0" rather than the obsolescent ifconfig.

Second, the 3ffe::/16 addresses were retired in 2006 when the experimental 6bone was decommissioned; tell your ISP to go back to its RIR and get a real IPv6 prefix.

To make a permanent static IPv6 address, if you are using the GUI you can do this from the network manager.  Pick "Edit Connections ...", select your active connection, use the edit button, go to the IPv6 tab, set method "manual", and fill in the boxes.

Or if you are hand-editing /etc/network/interfaces, add a stanza starting like ```

iface eth0 inet6 static
    address 3ffe:ffff:0:f101::1/64
```

---

