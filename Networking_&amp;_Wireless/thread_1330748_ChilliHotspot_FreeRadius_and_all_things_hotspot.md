---
title: "ChilliHotspot FreeRadius and all things hotspot"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by abean on 2009-11-18
Hi there,

I am currently trying to create a hotspot using ChilliSpot with the intention of creating my own web interface.

I have sucessfully installed all packages needed (Apache,Mysql,FreeRadius, chillispot, FreeRadius-MySQL, incremental dosage of caffeine).

Now my problem:

eth0 is my interface connected to the internet
eth1 is my hotspot interface

clients that connect through eht1 successfully receive an IP Adress from DHCP run by chillispot. But the redirect does not work, I have messed around with the IPTables with no joy, so I was wondering if someone could suggest an ip tables set up that will work for the following:

eth0  = internet conenction
eth1 = hotspot connection
tun0 = VPN setup for chillispot

Cheers

Abe

---

### Post by abean on 2009-11-19
Found the solution, i had the ifaces the wrong way round!

/usr/share/doc/chillispot/firewall.iptables and changed the INTIF and EXTIF variables

EXTIF=eth0
INTIF=eth1

---

