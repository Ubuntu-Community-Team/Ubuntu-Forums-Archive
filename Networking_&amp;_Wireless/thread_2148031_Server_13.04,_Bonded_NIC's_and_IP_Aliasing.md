---
title: "Server 13.04, Bonded NIC's and IP Aliasing"
date: 2013-05-23
forum: Networking &amp; Wireless
---

### Post by lpltac on 2013-05-23
Hello all.

I am able to get the nic bonding to work with no problems.  Using two nic cards.  But I
need to have multiple IP addresses.  I have scoured the internet looking for examples
but cannot find any.   The configuration below will sort of work but it takes a long time
at boot up to get past the networking setup.  If I do not put the dns lines in twice for each
interface dns does not work at all (no resolution).  

Below is my interfaces file.  Any suggestions?

Thanks.

# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto p4p1
iface p4p1 inet manual
   bond-master bond0


auto p9p1
iface p9p1 inet manual
   bond-master bond0


auto bond0
iface bond0 inet static
   address 192.168.90.51
   netmask 255.255.255.0
   gateway 192.168.90.252
   network 192.168.90.0
   broadcast 192.168.90.255
   dns-search pri.net
   dns-nameservers 192.168.90.252 75.75.75.75
   bond-mode balance-rr
   bond-miimon 100
   bond-slaves none


auto bond0:0
iface bond0:0 inet static
   address 192.168.90.155
   netmask 255.255.255.0
   gateway 192.168.90.252
   network 192.168.90.0
   broadcast 192.168.90.255

---

