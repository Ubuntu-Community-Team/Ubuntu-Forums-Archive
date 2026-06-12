---
title: "How to relinquish DHCP lease on shutdown?"
date: 2009-08-30
forum: Networking &amp; Wireless
---

### Post by xerces8 on 2009-08-30
Hi!

I have Ubuntu 9.04 and a WLAN connection (WPA2).

How can I make it relinquish the allocated address on shutdown (or at any time manually) ?

Thanks,
David

---

### Post by t0mppa on 2009-08-30
Just got to ask this: why do you want to relinquish the lease manually to begin with? The whole point of DHCP is assigning a large enough range of addresses to it, so you don't have to worry about them running out when you add more devices to the network. And if you want specific addresses to be assigned to specific devices, it's better to use static addresses.

To answer the question: either through **sudo dhclient -r** to simply release the lease or **ifdown <interface_logical_name>** to put the interface down.

---

### Post by xerces8 on 2009-08-30
1.) I have my reasons.

2.)
"sudo ifdown wlan0" returns:
Ignoring unknown interface wlan0=wlan0


"sudo dhclient -r wlan0" returns:
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/pan0/52:a1:f6:4b:24:71
Sending on   LPF/pan0/52:a1:f6:4b:24:71
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Listening on LPF/eth0/00:20:ed:6c:61:f6
Sending on   LPF/eth0/00:20:ed:6c:61:f6
Listening on LPF/wlan0/00:1c:df:77:cd:7c
Sending on   LPF/wlan0/00:1c:df:77:cd:7c
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
 * Reloading /etc/samba/smb.conf smbd only
   ...done.

It sends the DHCPRELEASE to to wrong address. I don't know where it took 192.168.1.1 from, but it is not the DHCP server.

---

### Post by t0mppa on 2009-09-01
That's odd, never done this with wireless, but it shouldn't be that much different from wired, since DHCP is just a protocol that doesn't care how the network connection is made.

You could try checking /var/lib/dhcp3/dhclient.leases to see if there are multiple leases active, which could possibly cause it to try and terminate an older one.

---

### Post by xerces8 on 2009-09-01
/var/lib/dhcp3/dhclient.leases appear to have som old/invalid leases

Maybe this should give a clue:
root      3556  0.0  0.0   2276   984 ?        S    18:17   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-wlan0.pid -lf /var/lib/dhcp3/dhclient-wlan0.lease -cf /var/run/nm-dhclient-wlan0.conf wlan0

?

---

### Post by t0mppa on 2009-09-02
Ah yes, the wireless leases are stored in another file. Try running **sudo dhclient -r -lf /var/lib/dhcp3/dhclient-wlan0.lease** then, that should force it to remove the lease stated in the wlan0 lease file. Just tested it and it worked on my laptop at least.

---

