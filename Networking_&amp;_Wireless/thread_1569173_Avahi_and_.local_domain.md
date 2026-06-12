---
title: "Avahi and .local domain"
date: 2010-09-06
forum: Networking &amp; Wireless
---

### Post by wblogan on 2010-09-06
I have two computers using the same ZyXel modem/router (192.168.2.1), both running Ubuntu 10.04. Both computers are Dells, one a desktop connected to the modem/router via ethernet cable with a reserved address of 192.168.2.3, the other a Dell laptop with a wireless connection to the modem/router and an address of 192.168.2.2.

Every time the modem/router is repowered I get a message on the laptop (in a balloon that pops up) saying "Avahi detected that your currently configured local DNS server serves a domain .local."

At the moment I can ping the router from the laptop and the desktop, I can ping and secure shell into the laptop from the desktop, but I cannot ping or secure shell into the desktop from the laptop.

I have port forwarding set up on the router with the desktop set as the default server so that connections to port 22 are allowed through the router firewall. There are no firewalls on either of the computers. (You can no doubt tell that I have little idea of what I'm talking about here.)

I've been to the address the message gives for more information; it's Greek to me. I've also searched the web for information with no luck.

Can someone tell me in plain english what the problem is and how to correct it?

Thanks.

If it helps, here is a look at the syslog message when I get the balloon message on the laptop
```
Sep  5 16:09:22  NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Sep  5 16:09:22  dhclient: Listening on LPF/wlan0/00:1f:3c:d2:77:76
Sep  5 16:09:22  dhclient: Sending on   LPF/wlan0/00:1f:3c:d2:77:76
Sep  5 16:09:22  dhclient: Sending on   Socket/fallback
Sep  5 16:09:25  dhclient: DHCPREQUEST of 192.168.2.2 on wlan0 to 255.255.255.255 port 67
Sep  5 16:09:25  dhclient: DHCPNAK from 192.168.2.1
Sep  5 16:09:25  NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> expire
Sep  5 16:09:25  dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Sep  5 16:09:25  NetworkManager: <info>  DHCP: device wlan0 state changed expire -> preinit
Sep  5 16:09:29  dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Sep  5 16:09:35  dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Sep  5 16:09:35  dhclient: DHCPOFFER of 192.168.2.2 from 192.168.2.1
Sep  5 16:09:35  dhclient: DHCPREQUEST of 192.168.2.2 on wlan0 to 255.255.255.255 port 67
Sep  5 16:09:35  dhclient: DHCPACK of 192.168.2.2 from 192.168.2.1
Sep  5 16:09:35  dhclient: bound to 192.168.2.2 -- renewal in 98709 seconds.
Sep  5 16:09:35  NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> bound
Sep  5 16:09:35  NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Sep  5 16:09:35  NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Sep  5 16:09:35  NetworkManager: <info>    address 192.168.2.2
Sep  5 16:09:35  NetworkManager: <info>    prefix 24 (255.255.255.0)
Sep  5 16:09:35  NetworkManager: <info>    gateway 192.168.2.1
Sep  5 16:09:35  NetworkManager: <info>    hostname 'dhcppc0'
Sep  5 16:09:35  NetworkManager: <info>    nameserver '192.168.2.1'
Sep  5 16:09:35  NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Sep  5 16:09:35  NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Sep  5 16:09:35  NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Sep  5 16:09:35  avahi-daemon[804]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.2.2.
Sep  5 16:09:35  avahi-daemon[804]: New relevant interface wlan0.IPv4 for mDNS.
Sep  5 16:09:35  avahi-daemon[804]: Registering new address record for 192.168.2.2 on wlan0.IPv4.
Sep  5 16:09:36  NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Sep  5 16:09:36  NetworkManager: <info>  Policy set 'Auto ZyXEL_A77' (wlan0) as default for routing and DNS.
Sep  5 16:09:36  NetworkManager: <info>  Activation (wlan0) successful, device activated.
Sep  5 16:09:36  NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Sep  5 16:09:36  avahi-daemon[804]: Got SIGTERM, quitting.
Sep  5 16:09:36  avahi-daemon[804]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.2.2.
Sep  5 16:09:36  init: avahi-daemon main process (804) terminated with status 255
Sep  5 16:09:36  avahi: Avahi detected that your currently configured local DNS server serves
Sep  5 16:09:36  avahi: a domain .local. This is inherently incompatible with Avahi and thus
Sep  5 16:09:36  avahi: Avahi disabled itself. If you want to use Avahi in this network, please
Sep  5 16:09:36  avahi: contact your administrator and convince him to use a different DNS domain,
Sep  5 16:09:36  avahi: since .local should be used exclusively for Zeroconf technology.
Sep  5 16:09:36  avahi: For more information, see http://avahi.org/wiki/AvahiAndUnicastDotLocal
```

After a reboot of the desktop (due to a kernel upgrade) here is what I see in the syslog messages:
```
Sep  6 07:47:41  NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Sep  6 07:47:41  dhclient: Listening on LPF/wlan0/00:1f:3c:d2:77:76
Sep  6 07:47:41  dhclient: Sending on   LPF/wlan0/00:1f:3c:d2:77:76
Sep  6 07:47:41  dhclient: Sending on   Socket/fallback
Sep  6 07:47:42  dhclient: DHCPREQUEST of 192.168.2.2 on wlan0 to 255.255.255.255 port 67
Sep  6 07:47:42  dhclient: DHCPNAK from 192.168.2.1
Sep  6 07:47:42  NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> expire
Sep  6 07:47:42  dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Sep  6 07:47:42  NetworkManager: <info>  DHCP: device wlan0 state changed expire -> preinit
Sep  6 07:47:47  dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Sep  6 07:47:47  dhclient: DHCPOFFER of 192.168.2.2 from 192.168.2.1
Sep  6 07:47:47  dhclient: DHCPREQUEST of 192.168.2.2 on wlan0 to 255.255.255.255 port 67
Sep  6 07:47:47  dhclient: DHCPACK of 192.168.2.2 from 192.168.2.1
Sep  6 07:47:47  dhclient: bound to 192.168.2.2 -- renewal in 101665 seconds.
Sep  6 07:47:47  NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> bound
Sep  6 07:47:47  NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Sep  6 07:47:47  NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Sep  6 07:47:47  NetworkManager: <info>    address 192.168.2.2
Sep  6 07:47:47  NetworkManager: <info>    prefix 24 (255.255.255.0)
Sep  6 07:47:47  NetworkManager: <info>    gateway 192.168.2.1
Sep  6 07:47:47  NetworkManager: <info>    hostname 'dhcppc0'
Sep  6 07:47:47  NetworkManager: <info>    nameserver '192.168.2.1'
Sep  6 07:47:47  NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Sep  6 07:47:47  NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Sep  6 07:47:47  NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Sep  6 07:47:48  NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Sep  6 07:47:48  NetworkManager: <info>  Policy set 'Auto ZyXEL_A77' (wlan0) as default for routing and DNS.
Sep  6 07:47:48  NetworkManager: <info>  Activation (wlan0) successful, device activated.
Sep  6 07:47:48  NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
```

---

### Post by wblogan on 2010-09-06
Removed the avahi-daemon.

---

