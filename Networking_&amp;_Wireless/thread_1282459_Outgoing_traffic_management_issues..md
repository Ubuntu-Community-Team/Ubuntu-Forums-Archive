---
title: "Outgoing traffic management issues."
date: 2009-10-04
forum: Networking &amp; Wireless
---

### Post by abacan79 on 2009-10-04
Hello, 
       i have 2 Internet connections in my network, and i would like that all outgoing traffic using the port 3389 uses the router A (192.168.10.20), wile everything else (Internet, mail, etc..) uses router B (192.168.10.21 and DHCP server).

For me it's totally OK to put a fixed IP address.

Is this possible? Can I do it with 1 network card?
Thanks a lot.

---

### Post by kreggz on 2009-10-06
You could probably do this if the IP address of the rdp connection you are trying to get to is static.

man route - manipulate routing tables.

---

