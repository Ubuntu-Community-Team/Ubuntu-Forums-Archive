---
title: "High latency after bridging with brctl."
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by Gary13579 on 2009-03-07
```
gary@fluffy:~$ sudo ifconfig ath0 0.0.0.0
gary@fluffy:~$ sudo ifconfig eth0 0.0.0.0
gary@fluffy:~$ sudo su
root@fluffy:/home/gary# brctl addbr br0
root@fluffy:/home/gary# brctl addif br0 ath0
root@fluffy:/home/gary# brctl addif br0 eth0
root@fluffy:/home/gary# dhclient br0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/br0/<removed>
Sending on   LPF/br0/<removed>
Sending on   Socket/fallback
DHCPDISCOVER on br0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on br0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on br0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.0.6 from 192.168.0.1
DHCPREQUEST of 192.168.0.6 on br0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.6 from 192.168.0.1
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
bound to 192.168.0.6 -- renewal in 39109 seconds.
root@fluffy:/home/gary# ifconfig br0 up

```

I recently used this to bridge my Xbox onto the network, using my laptops wireless card. Laptops ethernet port is eth0, wireless is ath0.

The Xbox seems to have connected fine and I can stream video files from my notebook to xbox via SMB.

But the connection on the notebook is drastically slowed, and eventually I got NO response from anything outside of the notebook (pinging my router would time out).

Restarting fixed it, but I really want to use this bridge. Anyone know whats wrong?

---

### Post by Gary13579 on 2009-03-07
Bump.

---

