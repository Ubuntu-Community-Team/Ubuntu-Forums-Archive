---
title: "iscsi direct connect problem"
date: 2012-04-04
forum: Networking &amp; Wireless
---

### Post by buffchick on 2012-04-04
I have a dell R810 with 4 network interfaces running ubuntu server 10.04. I'm trying to direct connect a dell md3220i iscsi SAN. I have ETH0 set to the main network and it's working fine. The IP address of the SAN ETH0 is 192.168.130.101. I added ETH1 to /etc/network/interfaces and installed open-iscsi. When I sudo ifup ETH1 It shows me```
itadmin@SVR:~$ sudo ifup eth1
 * Setting up iSCSI targets
   ...done.
ssh stop/waiting
ssh start/running, process 25420
itadmin@SVR:~$
```and then I can no longer ping or connect to ETH0. The cabling is a single straight through cat6 patch cable from ETH1 on the server to ETH1 on the SAN. 
 
if I ifdown ETH1 I get ```
itadmin@SVR:~$ sudo ifdown eth1
 * Disconnecting iSCSI targets
   ...done.
 * Stopping iSCSI initiator service
   ...done.
itadmin@SVR:~$
```and everything works fine again

/etc/network/interfaces```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 172.16.0.18
        netmask 255.255.255.0
        network 172.16.0.0
        broadcast 172.16.0.255
        gateway 172.16.0.4

auto eth1
iface eth1 inet static
        address 192.168.130.103
        netmask 255.255.255.0
        network 192.168.130.0
        broadcast 192.168.130.255
        gateway 192.168.130.1
``` Can anyone help me figure out what I'm doing wrong?

---

### Post by buffchick on 2012-04-05
checking back. Anyone?

---

### Post by buffchick on 2012-04-05
it was a routing issue.

---

