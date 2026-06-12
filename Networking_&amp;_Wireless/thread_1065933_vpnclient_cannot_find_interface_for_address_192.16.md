---
title: "vpnclient: cannot find interface for address: 192.168.11.23"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by void09 on 2009-02-10
Hi

I have patched and installed the latest Cisco vpnclient program. When I run it, I get no internet connectivity - just these error messages:

...
NAT passthrough is active on port UDP 4500
Local LAN Access is disabled

cannot find interface for address: 192.168.11.23
cannot find interface for address: 192.168.11.23
cannot find interface for address: 192.168.11.23
cannot find interface for address: 192.168.11.23
Secure VPN Connection terminated locally by the Client
Reason: Lost contact with the security gateway. Check your network connection
Disconnecting the VPN connection.

ps. 11.23 is the address that my computer gets by DHCP from my broadband router. The router has a static external IP and serves DHCP to inside. From XP this thing works. Not so from Ubuntu.

---

### Post by superprash2003 on 2009-02-10
post output of **ifconfig**.. and output of **cat /etc/resolv.conf** before and after connecting to vpn

---

