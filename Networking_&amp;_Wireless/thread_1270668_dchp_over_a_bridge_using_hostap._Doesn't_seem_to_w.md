---
title: "dchp over a bridge using hostap. Doesn't seem to work."
date: 2009-09-19
forum: Networking &amp; Wireless
---

### Post by Jophish on 2009-09-19
Hi

I am trying to get my server to act as a wireless AP for my wired network. It is running Karmic server amd64 I did get this working for a short time, however I wasn't sure if dhcp was being forwarded over dhcp3-relay or over the bridge, so I disabled dhcp3-relay. Nothing could get an ip from it, so I re-enabled the relay, however nothing can get a ip address now either!

Anyway, the setup on the server is as follows:

[hostapd.conf]("http://pastebin.com/m6c840588")

[/etc/network/interfaces]("http://pastebin.com/m4c68be12")

dhcp3-relay is watching eth0 and wlan0

A typical output from dhcp3-relay:
```
sudo dhcrelay3 -d -i br0 192.168.0.1
Internet Systems Consortium DHCP Relay Agent V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/
Listening on LPF/br0/00:01:2e:27:58:15
Sending on   LPF/br0/00:01:2e:27:58:15
Sending on   Socket/fallback
forwarded BOOTREQUEST for 00:16:ea:61:b6:00 to 192.168.0.1
4 bad udp checksums in 5 packets
forwarded BOOTREPLY for 00:16:ea:61:b6:00 to 192.168.0.13
forwarded BOOTREQUEST for 00:16:ea:61:b6:00 to 192.168.0.1
3 bad udp checksums in 5 packets
forwarded BOOTREPLY for 00:16:ea:61:b6:00 to 192.168.0.13
forwarded BOOTREQUEST for 00:16:ea:61:b6:00 to 192.168.0.1
3 bad udp checksums in 5 packets
forwarded BOOTREPLY for 00:16:ea:61:b6:00 to 192.168.0.13
forwarded BOOTREQUEST for 00:16:ea:61:b6:00 to 192.168.0.1
3 bad udp checksums in 5 packets
forwarded BOOTREPLY for 00:16:ea:61:b6:00 to 192.168.0.13

```

The ip is being forwarded to the client, however it is never getting there, as the client keeps on sending requests.

Please let me know if you need any more information.

Thanks.

---

### Post by Jophish on 2009-09-20
More information:
I can get the client to connect for a short time (about 30 seconds) using dhcp-helper. dhcp-helper is forwarding requests to 192.168.0.1, and listening on all interfaces.

---

