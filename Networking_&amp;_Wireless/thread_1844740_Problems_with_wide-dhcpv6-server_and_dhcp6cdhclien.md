---
title: "Problems with wide-dhcpv6-server and dhcp6c/dhclient"
date: 2011-09-15
forum: Networking &amp; Wireless
---

### Post by MichiGreat on 2011-09-15
**Hello!**

My configuration is as follows:

Ubuntu 10.10 Server with wide-dhcpv6-server and the following configuration saved in /etc/dhcp6s.conf:

```
interface eth0 {
  send rapid-commit;
  request domain-name-servers;
  address-pool pool1 3600;
  prefer-life-time 10000;
  valid-life-time 10000;
};

host xub1104vtm1 {
        duid 00:01:00:01:16:03:c9:8d:08:00:27:66:67:5b;
        prefix 2002:55ee:b07a:1::123/64 infinity;
};

pool pool1 {
        range 2002:55ee:b07a:1::100 to 2002:55ee:b07a:1::FFF ;
};
```

My client runs Xubuntu 11.04 and I installed dhcp6c. If I run it with "dhcp6c -D -f eth0", I get the following output:

```
Sep/15/2011 21:37:39: get_duid: extracted an existing DUID from /var/lib/dhcpv6/dhcp6c_duid: 00:01:00:01:16:03:c9:8d:08:00:27:66:67:5b
Sep/15/2011 21:37:39: cfdebug_print: <3>comment [# Default dhpc6c configuration: it assumes the address is autoconfigured using] (78)
Sep/15/2011 21:37:39: cfdebug_print: <3>comment [# router advertisements.] (24)
Sep/15/2011 21:37:39: cfdebug_print: <3>[profile] (7)
Sep/15/2011 21:37:39: cfdebug_print: <7>[default] (7)
Sep/15/2011 21:37:39: cfdebug_print: <3>begin of closure [{] (1)
Sep/15/2011 21:37:39: cfdebug_print: <3>[information-only] (16)
Sep/15/2011 21:37:39: cfdebug_print: <3>end of sentence [;] (1)
Sep/15/2011 21:37:39: cfdebug_print: <3>[request] (7)
Sep/15/2011 21:37:39: cfdebug_print: <3>[domain-name-servers] (19)
Sep/15/2011 21:37:39: cfdebug_print: <3>end of sentence [;] (1)
Sep/15/2011 21:37:39: cfdebug_print: <3>[request] (7)
Sep/15/2011 21:37:39: cfdebug_print: <3>[domain-name] (11)
Sep/15/2011 21:37:39: cfdebug_print: <3>end of sentence [;] (1)
Sep/15/2011 21:37:39: cfdebug_print: <3>[script] (6)
Sep/15/2011 21:37:39: cfdebug_print: <3>["/etc/wide-dhcpv6/dhcp6c-script"] (32)
Sep/15/2011 21:37:39: cfdebug_print: <3>end of sentence [;] (1)
Sep/15/2011 21:37:39: cfdebug_print: <3>end of closure [}] (1)
Sep/15/2011 21:37:39: cfdebug_print: <3>end of sentence [;] (1)
Sep/15/2011 21:37:39: configure_pool: called
Sep/15/2011 21:37:39: clear_poolconf: called
Sep/15/2011 21:37:39: dhcp6_reset_timer: reset a timer on eth0, state=INIT, timeo=0, retrans=290
Sep/15/2011 21:37:39: client6_send: a new XID (a3797f) is generated
Sep/15/2011 21:37:39: copy_option: set client ID (len 14)
Sep/15/2011 21:37:39: copy_option: set elapsed time (len 2)
Sep/15/2011 21:37:39: client6_send: send solicit to ff02::1:2%eth0
Sep/15/2011 21:37:39: dhcp6_reset_timer: reset a timer on eth0, state=SOLICIT, timeo=0, retrans=1078
Sep/15/2011 21:37:39: client6_recv: receive advertise from fe80::226:18ff:feaa:1c03%eth0 on eth0
Sep/15/2011 21:37:39: dhcp6_get_options: get DHCP option client ID, len 14
Sep/15/2011 21:37:39:   DUID: 00:01:00:01:16:03:c9:8d:08:00:27:66:67:5b
Sep/15/2011 21:37:39: dhcp6_get_options: get DHCP option server ID, len 14
Sep/15/2011 21:37:39:   DUID: 00:01:00:01:16:03:90:1d:00:26:18:aa:1c:03
Sep/15/2011 21:37:39: dhcp6_get_options: get DHCP option preference, len 1
Sep/15/2011 21:37:39:   preference: 0
Sep/15/2011 21:37:39: client6_recvadvert: server ID: 00:01:00:01:16:03:90:1d:00:26:18:aa:1c:03, pref=0
Sep/15/2011 21:37:39: client6_recvadvert: reset timer for eth0 to 0.993728
Sep/15/2011 21:37:40: select_server: picked a server (ID: 00:01:00:01:16:03:90:1d:00:26:18:aa:1c:03)
Sep/15/2011 21:37:40: client6_send: a new XID (8ca14f) is generated
Sep/15/2011 21:37:40: copy_option: set client ID (len 14)
Sep/15/2011 21:37:40: copy_option: set server ID (len 14)
Sep/15/2011 21:37:40: copy_option: set elapsed time (len 2)
Sep/15/2011 21:37:40: client6_send: send request to ff02::1:2%eth0
Sep/15/2011 21:37:40: dhcp6_reset_timer: reset a timer on eth0, state=REQUEST, timeo=0, retrans=1006
Sep/15/2011 21:37:40: client6_recv: receive reply from fe80::226:18ff:feaa:1c03%eth0 on eth0
Sep/15/2011 21:37:40: dhcp6_get_options: get DHCP option client ID, len 14
Sep/15/2011 21:37:40:   DUID: 00:01:00:01:16:03:c9:8d:08:00:27:66:67:5b
Sep/15/2011 21:37:40: dhcp6_get_options: get DHCP option server ID, len 14
Sep/15/2011 21:37:40:   DUID: 00:01:00:01:16:03:90:1d:00:26:18:aa:1c:03
Sep/15/2011 21:37:40: dhcp6_remove_event: removing an event on eth0, state=REQUEST
Sep/15/2011 21:37:40: dhcp6_remove_event: removing server (ID: 00:01:00:01:16:03:90:1d:00:26:18:aa:1c:03)
Sep/15/2011 21:37:40: client6_recvreply: got an expected reply, sleeping.
```

But it does not configure the specified IPv6 address 2002:55ee:b07a:1::123.

If I start dhclient -6 -d -v eth0, I get this output:

```
Internet Systems Consortium DHCP Client 4.1.1-P1
Copyright 2004-2010 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Bound to *:546
Listening on Socket/eth0
Sending on   Socket/eth0
PRC: Soliciting for leases (INIT).
XMT: Forming Solicit, 0 ms elapsed.
XMT:  X-- IA_NA "'fg["
XMT:  | X-- Request renew in  +3600
XMT:  | X-- Request rebind in +5400
XMT: Solicit on eth0, interval 1090ms.
RCV: Advertise message on eth0 from fe80::226:18ff:feaa:1c03.
RCV:  X-- Preference 0.
RCV:  X-- Server ID: 00:01:00:01:16:03:90:1d:00:26:18:aa:1c:03
message status code NoAddrsAvail.
PRC: Lease failed to satisfy.
XMT: Forming Solicit, 1090 ms elapsed.
XMT:  X-- IA_NA "'fg["
XMT:  | X-- Request renew in  +3600
XMT:  | X-- Request rebind in +5400
XMT: Solicit on eth0, interval 2200ms.

```

and so on (the last view lines are just repeated and the interval is increased) until I press Ctrl+C.

Does anybody has an idea of what I am doing wrong or how I could debug my problem? First, I have to know whether the problem is just the server, just the client, or both.

Best regards

*Michael*

---

### Post by MichiGreat on 2011-09-17
Meanwhile I found out that I made two errors: First, the configuration fie must be saved to /etc/wide-dhcpv6/dhcp6s.conf. Second, instead of "prefix" there sould be "address" and then the "/64" after the address must be omitted. Anyway, it still does not work, if I start the daemon in foreground, it processes all of the configuration file as far as I can see that, but at the end, it reports "main: failed to parse configuration file", but it's completely unclear to me, why it fails and there's no hint.

---

### Post by MichiGreat on 2011-09-17
Okay, solved. In dhcp6s.conf, the line "request domain-name-servers;" is wrong and must be removed. Works for me now; solved.

---

