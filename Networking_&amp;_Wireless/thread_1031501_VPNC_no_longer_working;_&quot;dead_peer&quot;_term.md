---
title: "VPNC no longer working; &quot;dead peer&quot; terminations, odd routing table"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by Bootsy Collins on 2009-01-05
Hi folks.  I very much need vpn to work under Ubuntu, so any help here would be appreciated.

Machine:  Two on-mobo ethernet interfaces, only one (eth0) of which is in use; eth1 not configured and not in use in any way; recent install of Intrepid.

Background:  Immediately after my install, I was able to get my vpn connection working perfectly through the network manager applet. However, I had trouble of a different sort:  my intended LAN config is to have some machines with DHCP-assigned addresses and others (including this one) with a static IP address.  Although I configured the interface as manual with a static IP address through the network manager applet, after each boot and login, it would end up with a DHCP-assigned address.  Presumably something in the boot process was making a DHCP call early on, so what I did in my personal network manager config was irrelevant.  On the advice of folks here, I gave up on network manager and configured eth0 through /etc/network/interfaces.  This worked perfectly as far as establishing my net connection through eth0 with a static IP on my home LAN.  However, apparently once you decide to configure an interface through /etc/network/interfaces, you can no longer use network manager to manage a vpn connection through that interface.  Since the network manager applet appears to store its vpnc configuration info in a not-known-by-vpnc place (~/.gconf?), it also meant I had to configure vpnc manually.

I created a file /etc/vpnc/(my_vpn_name).conf with gateway, ID, secret, and username.  Running "sudo vpnc (my_vpn_name)" results in a prompt for my VPN password; when I give it, I get a connect banner from the VPN server and am informed "VPNC started in background".  So at this point, it looks like things are going great.

But immediately after that, nothing I try to do on the vpn works -- any attempt to connect to any machines only accessible from within the vpn hangs.  After a little while, the vpn connection itself simply goes away -- no vpnc running, no tun0 device in ifconfig, routing table back to pre-vpn state, /etc/resolv.conf back to before with no vpn-specific nameservers listed.  /var/log/daemon.log shows lines that look like this:

```

Jan  5 12:43:37 stax vpnc[14504]: sendto: Message too long
Jan  5 12:44:08 stax last message repeated 50 times
Jan  5 12:44:11 stax last message repeated 13 times
Jan  5 12:44:13 stax vpnc[14504]: connection terminated by dead peer detection

```

Looking at this in more detail, I did the following before, and *immediately* after starting vpnc, to look for oddities:  cat /etc/resolv.conf ; cat /etc/hosts ; ifconfig -a ; netstat -r .  /etc/resolv.conf picked up two lines at the start specifying nameservers within the vpn.  /etc/hosts didn't change.  ifconfig -a looked good:  nothing changed except for a new interface, tun0, with what looked to my neophyte eyes like a good config:

```

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:(my_internal_vpn_addy)  P-t-P:(my_internal_vpn_addy)  Mask:255.255.248.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1390  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:33920 (33.9 KB)

```
. . .where "(my_internal_vpn_addy)" is the IP address I'm supposed to be assigned on the private network -- and the address is correct.

Where things seemed odd was the routing table.  Here's what it was **before** running vpnc:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         router          0.0.0.0         UG        0 0          0 eth0

```
( "router" is the /etc/hosts specification for 192.168.1.1, the internal address of our house router)

. . .and here's what it was **immediately after** starting vpnc:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
(vpn_gateway)   *               255.255.255.255 UH     1390 0          0 tun0
192.168.1.0     *               255.255.255.0   U         0 0          0 eth0
(vpn .0 IP)     *               255.255.248.0   U         0 0          0 tun0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         *               0.0.0.0         U         0 0          0 tun0
default         router          0.0.0.0         UG        0 0          0 eth0

```
. . .where by "(vpn_gateway)", I mean the correct IP address of the primary server for my vpn, and by "(vpn .0 IP)", I mean the same IP address as the primary vpn server but with ".0" in the last decimal field.

I'm not a network maven, by any means -- but does that routing table even make sense?  How can I have two default destination routes?  Why is the route to the VPN server itself configured over tun0 rather than eth0?  I googled a bunch before posting here, and this routing table doesn't look like the ones I see in discussions of established vpnc connections; I expected to see something like a default to gateway "*" on tun0; the vpn server as a destination routed to my home router on eth0; and the link-local and 192.168.1.0 entries on eth0.

Am I diagnosing this issue correctly?  Is vpnc setting up my routing table incorrectly?  If so, why, and how might I fix this?

Thanks for any help.  This is costing me a ton of time.

---

### Post by Bootsy Collins on 2009-01-05
Attempting to manually adjust the routing tables in the window between connection and connection being dead-peer-terminated has brought no joy.  Either my diagnosis is incorrect, or that route isn't succeeding.

Any advice would be greatly appreciated.  Now lost a whole day of work because of this -- especially frustrating when it was working three weeks ago.  Thanks.

---

### Post by Bootsy Collins on 2009-01-05
More talking to myself . . .in the discussion attached to Bug [lpbug]206673[/lpbug], it was noted that some old VPN concentrators have the dead peer issue; a revision of the Ubuntu vpnc package was made available there, with the default dead peer detection idle time set to zero.  Installing and running this did indeed stop my "connection terminated by dead peer detection" message.  Furthermore, using ifconfig to increase the tun0 MTU value from 1390 to 1500 also stopped the "sendto: Message too long" messages.

However, still no luck actually using the vpn.  It's as if every machine on the other side of the vpn server is down (which I know for a fact is not true) -- I connect, authenticate, and get a banner from the vpn server that tells me I'm in.  But anything I try to do after that -- browse a Windows share, ssh into a Solaris box, or just ping a machine -- hangs / times out.

Again, any guidance gratefully appreciated.

---

### Post by tpurch on 2009-01-15
> **Bootsy Collins said:**
> I connect, authenticate, and get a banner from the vpn server that tells me I'm in.  But anything I try to do after that -- browse a Windows share, ssh into a Solaris box, or just ping a machine -- hangs / times out.

not sure if this helps but you could try:

sudo vpnc --natt-mode cisco-udp /path_to_your_vpn.conf

---

