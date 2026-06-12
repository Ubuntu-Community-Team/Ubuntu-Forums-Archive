---
title: "how to split  port 80 via two gateway by range"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by badai707 on 2009-05-09
i need help..

i've setup gateway server (ip: 192.168.1.4) which connected to LAN (192.168.0.0/24) via eth0. I need to split whatever going out via port 80 to two gateway by eth1 and eth2

1. If user from LAN browse to private ip (192.168.0.0/24), it go via eth1 (192.168.1.2) and
2. If user from LAN browse to public ip (203.0.0.0/24), it go via eth2 (192.168.1.3)
 
plz help & tq.

---

### Post by Triptol on 2009-05-09
I think you are looking for masquerading, but I am not completely sure. Have a look at iptables and masquerading (google will help).

You can also try arno-iptables which is part of Ubuntu. It is Perl script with a lot of explanation inside.

---

