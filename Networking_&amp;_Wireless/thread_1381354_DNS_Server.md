---
title: "DNS Server"
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by fbifido on 2010-01-14
How can i build an internal dns server for my network, but don't use the top level domain, eg: mycat.com. I want to use mycat.kgn.
and i want to put a mycat.kgn mail server on the network for internal uses.

my setup:
dns mx mail2.mycat.com (my server)
    mx mail.mycat.com (godaddy)

inet-gateway & firewall & mailserver:
centos 4, mail2.mycat.com
nic1 - internet
nic2 - 192.168.0.1
kerio email server 6

all workstation & server uses:
ip: (below)
netmask: 255.255.255.0
gateway: 192.168.0.1
dns: 192.168.0.1

workstations:
windows & linux
nic1 - (192.168.0.20 - 192.168.0.199)

Printers:
HP laserjet
jetdirect (192.168.0.211 - 192.168.0.249)

Data server:

1. ubuntu 8.04 LTS, nic1 - 192.168.0.8
2. redhat AS 2.1, nic1 - 192.168.0.10
3. xenserver 5.0, nic1 - 192.168.0.11
    - windows 2003 terminal server, xen-nic1 - 192.168.0.210
    - winxp sp3 accpac, xen-nic2 - 192.168.0.2
    - win2000 sp4, xen-nic2 - 192.168.0.200


-----------------------------------------------------------------
=====[ Config i need ]===========================================

i need a dns server with:
dns mx zimbra.mycat.kgn   192.168.0.127
    A  mycat.kgn          192.168.0.1
    A  samba.mycat.kgn    192.168.0.128
    A  [www.mycat.kgn](www.mycat.kgn)      192.168.0.1
   NS  ns1.mycat.kgn      192.168.0.129

all workstation and servers:
ip: (same as above)
netmask: 255.255.255.0
gateway: 192.168.0.1
dns: 192.168.0.129

ldap all machine to zimbra.mycat.kgn for login info and password.
map drive g: to samba.mycat.kgn data-share (with users rights from ldap)

?????????????????????????????????????????????????????????????????

I tried to do this in virtualbox, but fail badly!!! :(
i created 6 vm using ubuntu 804 and 910, but my dns was not getting any records with dig, so i found an howto on powerdns. but i had to use mycat.com and not mycat.kgn?

Help !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

can someone and one build a setup of a network with the following info for me PLEASE !!!!

i will draw my network to be!

each machine:
ip: (sameas above)
gateway: 192.168.0.1
dns: 192.168.0.129
dns-nameserver 192.168.0.129
nameserver 192.168.0.129

and if the dns server does not find the info it forward it to the gateway 192.168.0.1

---

### Post by Iowan on 2010-01-14
DNSMasq is my favorite DHCP/DNS server - dunno if it'll fit your needs.

---

### Post by Lars Noodén on 2010-01-15
+1 for the suggestion for [dnsmasq](http://www.thekelleys.org.uk/dnsmasq/doc.html) if it's for a very small LAN.  It's very, very easy to [apt://dnsmasq/]install dnsmasq[/url] and very, very easy to configure.

---

