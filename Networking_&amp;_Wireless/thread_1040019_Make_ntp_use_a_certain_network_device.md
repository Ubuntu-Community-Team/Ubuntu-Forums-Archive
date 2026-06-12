---
title: "Make ntp use a certain network device"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by mtausig on 2009-01-15
Hy!

I want to use ntp to syncronise the clocks within my vpn (using openvpn). I set the "server" entry in ntp.conf to "server 10.1.1.112", which is another VPN host.

The problem is, that it tries to connect to the NTP-server via the normal LAN, which doesn't work due to firewall restrictions. How can I tell ntpd to explicitely use tun0 as a device, respectively the correct network address.

---

### Post by mtausig on 2009-01-19
bump

---

