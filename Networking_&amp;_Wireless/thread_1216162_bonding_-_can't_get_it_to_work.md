---
title: "bonding - can't get it to work"
date: 2009-07-18
forum: Networking &amp; Wireless
---

### Post by matt_garman on 2009-07-18
Using Ubuntu 9.04.

My computer has two network interfaces.  I'm trying to use the bonding module to aggregate them together for faster performance on my LAN.

I've followed every tutorial and HOWTO I can find, yet the bond0 interface doesn't work.  If I manually assign it an IP address, I can't ping any other machines on my LAN.  If I try to assign it an address via dhclient, it never receives any DHCP offers.

I have verified that both NICs work fine (i.e. when not using bonding).

I know the gist is:
    modprobe mode=6 miimon=100
    ifconfig bond0 up
    ifenslave bond0 eth0 eth1

At this point, I can either do a "ifconfig bond0 <address>" or "dhclient bond0".  The results are as described above.

During all of this, I'm not getting any errors in dmesg or otherwise.  It's as though the "bond0" interface really isn't "connected" to eth0/eth1.

I've done this before with Ubuntu Server 8.04, and likewise with CentOS 5.3.

Is there some subtle step I'm missing?

Thanks,
Matt

---

### Post by matt_garman on 2009-07-18
After much hair-pulling, I believe the problem is that I was trying to use mode 6 (balance-alb).  When I reloaded the bonding module with mode=0 (balance-rr), everything worked as expected.

I have to experiment more to find out why I can't use balance-alb.  It could be my underlying hardware (realtek 8111c), but I doubt it, as the other computer I'm using has the same NIC, and works fine with balance-alb.

---

