---
title: "Connection issues with WICD (both wired and wireless)"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by vckeating on 2009-02-05
Hi all,

I've been trying to use a wired connection at my university using WICD, but can't seem to get it going.  According to the sysadmins, my MAC address is registered and I'm hooked into the right port, but still I don't have any luck.  Whenever I try to connect I get something resemling this in the log:

```
Feb  5 13:13:36 chuck-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Feb  5 13:13:36 chuck-laptop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Feb  5 13:13:36 chuck-laptop dhclient: All rights reserved.
Feb  5 13:13:36 chuck-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Feb  5 13:13:36 chuck-laptop dhclient: 
Feb  5 13:13:36 chuck-laptop dhclient: wmaster0: unknown hardware address type 801
Feb  5 13:13:36 chuck-laptop dhclient: wmaster0: unknown hardware address type 801
Feb  5 13:13:36 chuck-laptop kernel: [  306.325733] NET: Registered protocol family 17
Feb  5 13:13:36 chuck-laptop dhclient: Bind socket to interface: No such device
Feb  5 13:13:36 chuck-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Feb  5 13:13:36 chuck-laptop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Feb  5 13:13:36 chuck-laptop dhclient: All rights reserved.
Feb  5 13:13:36 chuck-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Feb  5 13:13:36 chuck-laptop dhclient: 
Feb  5 13:13:36 chuck-laptop dhclient: wmaster0: unknown hardware address type 801
Feb  5 13:13:36 chuck-laptop dhclient: wmaster0: unknown hardware address type 801
Feb  5 13:13:36 chuck-laptop dhclient: Bind socket to interface: No such device
Feb  5 13:13:36 chuck-laptop kernel: [  306.467494] eth0: link up, 100Mbps, full-duplex, lpa 0x43E1
Feb  5 13:13:36 chuck-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Feb  5 13:13:36 chuck-laptop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Feb  5 13:13:36 chuck-laptop dhclient: All rights reserved.
Feb  5 13:13:36 chuck-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Feb  5 13:13:36 chuck-laptop dhclient: 
Feb  5 13:13:36 chuck-laptop dhclient: wmaster0: unknown hardware address type 801
Feb  5 13:13:37 chuck-laptop dhclient: wmaster0: unknown hardware address type 801
Feb  5 13:13:37 chuck-laptop dhclient: Listening on LPF/eth0/00:c0:9f:77:80:9f
Feb  5 13:13:37 chuck-laptop dhclient: Sending on   LPF/eth0/00:c0:9f:77:80:9f
Feb  5 13:13:37 chuck-laptop dhclient: Sending on   Socket/fallback
Feb  5 13:13:40 chuck-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Feb  5 13:13:48 chuck-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Feb  5 13:13:59 chuck-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Feb  5 13:14:10 chuck-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Feb  5 13:14:25 chuck-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Feb  5 13:14:40 chuck-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
Feb  5 13:14:41 chuck-laptop dhclient: No DHCPOFFERS received.
Feb  5 13:14:41 chuck-laptop dhclient: No working leases in persistent database - sleeping.
Feb  5 13:14:41 chuck-laptop avahi-autoipd(eth0)[6065]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 112).
Feb  5 13:14:41 chuck-laptop avahi-autoipd(eth0)[6065]: Successfully called chroot().
Feb  5 13:14:41 chuck-laptop avahi-autoipd(eth0)[6065]: Successfully dropped root privileges.
Feb  5 13:14:41 chuck-laptop avahi-autoipd(eth0)[6065]: Starting with address 169.254.8.127
Feb  5 13:14:46 chuck-laptop avahi-autoipd(eth0)[6065]: Callout BIND, address 169.254.8.127 on interface eth0
Feb  5 13:14:46 chuck-laptop avahi-daemon[4655]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.8.127.
Feb  5 13:14:46 chuck-laptop avahi-daemon[4655]: New relevant interface eth0.IPv4 for mDNS.
Feb  5 13:14:46 chuck-laptop avahi-daemon[4655]: Registering new address record for 169.254.8.127 on eth0.IPv4.
Feb  5 13:14:50 chuck-laptop avahi-autoipd(eth0)[6065]: Successfully claimed IP address 169.254.8.127
```

The problem is the WICD says that I'm not connected, and I have no access to the network through various programs.  

I should also mention that I asked to use the wired connection because I kept having wireless issues.  I could connect, but after some time my access to the internet would go away despite WICD telling me that I was still 'connected.'  The connection log is here:

```

Feb  5 13:15:36 chuck-laptop dhclient: There is already a pid file /var/run/dhclient.pid with pid 6072
Feb  5 13:15:36 chuck-laptop dhclient: killed old client process, removed PID file
Feb  5 13:15:36 chuck-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Feb  5 13:15:36 chuck-laptop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Feb  5 13:15:36 chuck-laptop dhclient: All rights reserved.
Feb  5 13:15:36 chuck-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Feb  5 13:15:36 chuck-laptop dhclient: 
Feb  5 13:15:36 chuck-laptop dhclient: wmaster0: unknown hardware address type 801
Feb  5 13:15:36 chuck-laptop dhclient: wmaster0: unknown hardware address type 801
Feb  5 13:15:36 chuck-laptop dhclient: Bind socket to interface: No such device
Feb  5 13:15:36 chuck-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Feb  5 13:15:36 chuck-laptop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Feb  5 13:15:36 chuck-laptop dhclient: All rights reserved.
Feb  5 13:15:36 chuck-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Feb  5 13:15:36 chuck-laptop dhclient: 
Feb  5 13:15:36 chuck-laptop dhclient: wmaster0: unknown hardware address type 801
Feb  5 13:15:36 chuck-laptop dhclient: wmaster0: unknown hardware address type 801
Feb  5 13:15:36 chuck-laptop dhclient: Bind socket to interface: No such device
Feb  5 13:15:36 chuck-laptop kernel: [  426.974081] input: b43-phy0 as /devices/virtual/input/input9
Feb  5 13:15:37 chuck-laptop kernel: [  427.164053] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Feb  5 13:15:37 chuck-laptop kernel: [  427.279142] Registered led device: b43-phy0::tx
Feb  5 13:15:37 chuck-laptop kernel: [  427.279578] Registered led device: b43-phy0::rx
Feb  5 13:15:37 chuck-laptop kernel: [  427.279799] Registered led device: b43-phy0::radio
Feb  5 13:15:38 chuck-laptop kernel: [  428.272096] wlan0: authenticate with AP 00:17:e0:1a:28:e0
Feb  5 13:15:38 chuck-laptop kernel: [  428.272131] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Feb  5 13:15:38 chuck-laptop kernel: [  428.472045] wlan0: authenticate with AP 00:17:e0:1a:28:e0
Feb  5 13:15:38 chuck-laptop kernel: [  428.472088] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Feb  5 13:15:38 chuck-laptop kernel: [  428.672048] wlan0: authenticate with AP 00:17:e0:1a:28:e0
Feb  5 13:15:38 chuck-laptop kernel: [  428.672094] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Feb  5 13:15:38 chuck-laptop kernel: [  428.827633] wlan0: authenticated
Feb  5 13:15:38 chuck-laptop kernel: [  428.827645] wlan0: associate with AP 00:17:e0:1a:28:e0
Feb  5 13:15:38 chuck-laptop kernel: [  428.827651] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
Feb  5 13:15:38 chuck-laptop kernel: [  428.872033] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Feb  5 13:15:41 chuck-laptop kernel: [  431.288323] wlan0: authenticate with AP 00:17:e0:1a:28:e0
Feb  5 13:15:41 chuck-laptop kernel: [  431.289134] wlan0: authenticate with AP 00:17:e0:1a:28:e0
Feb  5 13:15:41 chuck-laptop kernel: [  431.488045] wlan0: authenticate with AP 00:17:e0:1a:28:e0
Feb  5 13:15:41 chuck-laptop kernel: [  431.594012] wlan0: authenticated
Feb  5 13:15:41 chuck-laptop kernel: [  431.594025] wlan0: associate with AP 00:17:e0:1a:28:e0
Feb  5 13:15:41 chuck-laptop kernel: [  431.792034] wlan0: associate with AP 00:17:e0:1a:28:e0
Feb  5 13:15:41 chuck-laptop kernel: [  431.992038] wlan0: associate with AP 00:17:e0:1a:28:e0
Feb  5 13:15:42 chuck-laptop kernel: [  432.192040] wlan0: association with AP 00:17:e0:1a:28:e0 timed out
Feb  5 13:15:51 chuck-laptop kernel: [  442.068187] wlan0: authenticate with AP 00:17:e0:1a:28:e0
Feb  5 13:15:51 chuck-laptop kernel: [  442.068991] wlan0: authenticate with AP 00:17:e0:1a:28:e0
Feb  5 13:15:52 chuck-laptop kernel: [  442.094198] wlan0: authenticated
Feb  5 13:15:52 chuck-laptop kernel: [  442.094211] wlan0: associate with AP 00:17:e0:1a:28:e0
Feb  5 13:15:52 chuck-laptop kernel: [  442.099235] wlan0: RX AssocResp from 00:17:e0:1a:28:e0 (capab=0x431 status=0 aid=8)
Feb  5 13:15:52 chuck-laptop kernel: [  442.099242] wlan0: associated
Feb  5 13:15:52 chuck-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Feb  5 13:15:52 chuck-laptop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Feb  5 13:15:52 chuck-laptop dhclient: All rights reserved.
Feb  5 13:15:52 chuck-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Feb  5 13:15:52 chuck-laptop dhclient: 
Feb  5 13:15:52 chuck-laptop dhclient: wmaster0: unknown hardware address type 801
Feb  5 13:15:53 chuck-laptop dhclient: wmaster0: unknown hardware address type 801
Feb  5 13:15:53 chuck-laptop dhclient: Listening on LPF/wlan0/00:90:4b:a5:67:6a
Feb  5 13:15:53 chuck-laptop dhclient: Sending on   LPF/wlan0/00:90:4b:a5:67:6a
Feb  5 13:15:53 chuck-laptop dhclient: Sending on   Socket/fallback
Feb  5 13:15:53 chuck-laptop dhclient: DHCPREQUEST of 144.124.25.14 on wlan0 to 255.255.255.255 port 67
Feb  5 13:15:57 chuck-laptop dhclient: DHCPREQUEST of 144.124.25.14 on wlan0 to 255.255.255.255 port 67
Feb  5 13:15:57 chuck-laptop dhclient: DHCPACK of 144.124.25.14 from 144.124.31.254
Feb  5 13:15:57 chuck-laptop avahi-daemon[4655]: Joining mDNS multicast group on interface wlan0.IPv4 with address 144.124.25.14.
Feb  5 13:15:57 chuck-laptop avahi-daemon[4655]: New relevant interface wlan0.IPv4 for mDNS.
Feb  5 13:15:57 chuck-laptop avahi-daemon[4655]: Registering new address record for 144.124.25.14 on wlan0.IPv4.
Feb  5 13:15:57 chuck-laptop avahi-daemon[4655]: Withdrawing address record for 144.124.25.14 on wlan0.
Feb  5 13:15:57 chuck-laptop avahi-daemon[4655]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 144.124.25.14.
Feb  5 13:15:57 chuck-laptop avahi-daemon[4655]: Interface wlan0.IPv4 no longer relevant for mDNS.
Feb  5 13:15:57 chuck-laptop avahi-daemon[4655]: Joining mDNS multicast group on interface wlan0.IPv4 with address 144.124.25.14.
Feb  5 13:15:57 chuck-laptop avahi-daemon[4655]: New relevant interface wlan0.IPv4 for mDNS.
Feb  5 13:15:57 chuck-laptop avahi-daemon[4655]: Registering new address record for 144.124.25.14 on wlan0.IPv4.
Feb  5 13:15:57 chuck-laptop dhclient: bound to 144.124.25.14 -- renewal in 83054 seconds.
Feb  5 13:16:20 chuck-laptop kernel: [  470.397164] b43-phy0 ERROR: PHY transmission error
Feb  5 13:16:33 chuck-laptop kernel: [  483.418255] b43-phy0 ERROR: PHY transmission error
Feb  5 13:16:33 chuck-laptop kernel: [  483.498482] b43-phy0 ERROR: PHY transmission error
Feb  5 13:16:33 chuck-laptop kernel: [  483.745585] b43-phy0 ERROR: PHY transmission error
Feb  5 13:16:34 chuck-laptop kernel: [  484.228806] b43-phy0 ERROR: PHY transmission error

```

But after some period of time, the following starts to happen and I lose the connection, which I can only rectify by disconnecting than reconnecting:

```

Feb  5 13:23:06 chuck-laptop kernel: [  876.104059] wlan0: No ProbeResp from current AP 00:17:e0:1a:28:e0 - assume out of range
Feb  5 13:23:06 chuck-laptop kernel: [  876.988267] wlan0: authenticate with AP 00:17:e0:1a:28:e0
Feb  5 13:23:06 chuck-laptop kernel: [  877.007008] wlan0: authenticated
Feb  5 13:23:06 chuck-laptop kernel: [  877.007020] wlan0: associate with AP 00:17:e0:1a:28:e0
Feb  5 13:23:07 chuck-laptop kernel: [  877.090124] wlan0: RX ReassocResp from 00:17:e0:1a:28:e0 (capab=0x431 status=0 aid=8)
Feb  5 13:23:07 chuck-laptop kernel: [  877.090133] wlan0: associated
Feb  5 13:23:32 chuck-laptop kernel: [  903.047479] wlan0: deauthenticated
Feb  5 13:23:33 chuck-laptop kernel: [  904.044042] wlan0: authenticate with AP 00:17:e0:1a:28:e0
Feb  5 13:23:33 chuck-laptop kernel: [  904.056437] wlan0: authenticated
Feb  5 13:23:33 chuck-laptop kernel: [  904.056445] wlan0: associate with AP 00:17:e0:1a:28:e0
Feb  5 13:23:33 chuck-laptop kernel: [  904.063194] wlan0: RX ReassocResp from 00:17:e0:1a:28:e0 (capab=0x431 status=0 aid=8)
Feb  5 13:23:33 chuck-laptop kernel: [  904.063202] wlan0: associated
Feb  5 13:23:58 chuck-laptop kernel: [  929.050377] wlan0: deauthenticated
Feb  5 13:23:59 chuck-laptop kernel: [  930.048036] wlan0: authenticate with AP 00:17:e0:1a:28:e0
Feb  5 13:23:59 chuck-laptop kernel: [  930.049648] wlan0: authenticated
Feb  5 13:23:59 chuck-laptop kernel: [  930.049656] wlan0: associate with AP 00:17:e0:1a:28:e0
Feb  5 13:23:59 chuck-laptop kernel: [  930.055895] wlan0: RX ReassocResp from 00:17:e0:1a:28:e0 (capab=0x431 status=0 aid=8)
Feb  5 13:23:59 chuck-laptop kernel: [  930.055901] wlan0: associated
Feb  5 13:24:24 chuck-laptop kernel: [  955.050558] wlan0: deauthenticated
Feb  5 13:24:25 chuck-laptop kernel: [  956.048040] wlan0: authenticate with AP 00:17:e0:1a:28:e0
Feb  5 13:24:25 chuck-laptop kernel: [  956.051355] wlan0: authenticated
Feb  5 13:24:25 chuck-laptop kernel: [  956.051362] wlan0: associate with AP 00:17:e0:1a:28:e0
Feb  5 13:24:25 chuck-laptop kernel: [  956.054654] wlan0: RX ReassocResp from 00:17:e0:1a:28:e0 (capab=0x431 status=0 aid=8)
Feb  5 13:24:25 chuck-laptop kernel: [  956.054661] wlan0: associated
Feb  5 13:24:50 chuck-laptop kernel: [  981.050455] wlan0: deauthenticated
Feb  5 13:24:51 chuck-laptop kernel: [  982.048034] wlan0: authenticate with AP 00:17:e0:1a:28:e0
Feb  5 13:24:51 chuck-laptop kernel: [  982.049628] wlan0: authenticated
Feb  5 13:24:51 chuck-laptop kernel: [  982.049636] wlan0: associate with AP 00:17:e0:1a:28:e0
Feb  5 13:24:51 chuck-laptop kernel: [  982.052941] wlan0: RX ReassocResp from 00:17:e0:1a:28:e0 (capab=0x431 status=0 aid=8)
Feb  5 13:24:51 chuck-laptop kernel: [  982.052947] wlan0: associated
Feb  5 13:25:19 chuck-laptop kernel: [ 1009.450871] wlan0: deauthenticated
Feb  5 13:25:20 chuck-laptop kernel: [ 1010.448037] wlan0: authenticate with AP 00:17:e0:1a:28:e0
Feb  5 13:25:20 chuck-laptop kernel: [ 1010.450379] wlan0: authenticated
Feb  5 13:25:20 chuck-laptop kernel: [ 1010.450387] wlan0: associate with AP 00:17:e0:1a:28:e0
Feb  5 13:25:20 chuck-laptop kernel: [ 1010.457194] wlan0: RX ReassocResp from 00:17:e0:1a:28:e0 (capab=0x431 status=0 aid=8)
Feb  5 13:25:20 chuck-laptop kernel: [ 1010.457202] wlan0: associated

```

So, I don't know if anyone has any ideas about either problem, but any help/advice would be very much appreciated.  

Cheers!

---

