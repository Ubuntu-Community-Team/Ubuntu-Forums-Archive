---
title: "Help with /renew through DHCP"
date: 2006-05-03
forum: Networking &amp; Wireless
---

### Post by vladimir-dk on 2006-05-03
Hi,

Im have worked a coulpe of weeks to get my WLAN up and running. 
I have installed the following:

- ipw2200-1.1.2
- ipw2200-fw-2.3.tgz 
- ieee80211-1.1.13

I managed to get a IP-configuration through DHCP when i disabled the encryption on the wireless network. But i cant renew the IP-adresse when i enable WPA-PSK in my router.

Here is what i tried:

```

danny@laptop:~$ sudo dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 8571
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/ath0/00:14:a4:39:40:16
Sending on   LPF/ath0/00:14:a4:39:40:16
Sending on   Socket/fallback
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
Trying recorded lease 192.168.1.105
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 3.118/3.118/3.118/0.000 ms
bound: renewal in 87535 seconds.

```

The ICMP echo reply that was recieved is because my LAN-cable is plugged in.


Any help would be appriciated!

---

