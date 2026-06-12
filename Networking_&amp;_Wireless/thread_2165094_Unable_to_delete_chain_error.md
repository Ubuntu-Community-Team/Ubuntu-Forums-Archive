---
title: "Unable to delete chain error"
date: 2013-08-03
forum: Networking &amp; Wireless
---

### Post by zfKcMb4 on 2013-08-03
I am in the process of testing a couple of VDI solutions.  Currently I'm testing QVD which runs on Ubuntu 12.04.  I have followed their instructions to setup QVD but when I try to start a VM I receive errors in their log file.  I have reached out for support but, of course unless you purchase the product, help is limited.  So, I thought I would see if anyone here could shed some light on what's wrong with my setup.

The errors I'm getting seems to be related to the /etc/network/interfaces config iptables/ebtables.  Here are the errors in /var/log/qvd/qvd.log:

2013/08/03 04:45:52 1695 DEBUG /usr/lib/qvd/lib/perl5/site_perl/5.14.2/QVD/HKD/VMHandler.pm 259 - deleting ebtables chain QVD_1_INPUT
2013/08/03 04:45:52 1695 ERROR /usr/lib/qvd/lib/perl5/site_perl/5.14.2/QVD/HKD/VMHandler.pm 262 - Unable to delete chain 'QVD_1_INPUT', rc: 16711680

2013/08/03 04:45:52 1695 DEBUG /usr/lib/qvd/lib/perl5/site_perl/5.14.2/QVD/HKD/VMHandler.pm 259 - deleting ebtables chain QVD_1_FORWARD
2013/08/03 04:45:52 1695 ERROR /usr/lib/qvd/lib/perl5/site_perl/5.14.2/QVD/HKD/VMHandler.pm 262 - Unable to delete chain 'QVD_1_FORWARD', rc: 16711680

/etc/network/interfaces:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
  address 192.168.1.10
  netmask 255.255.255.0
  gateway 192.168.1.1
  broadcast 192.168.1.255
  dns-nameservers 192.168.1.1

auto qvdnet0
iface qvdnet0 inet static
  pre-up brctl addbr qvdnet0
  pre-up iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source 192.168.1.10
  pre-up iptables -t nat -A PREROUTING -d 192.168.1.10 -p tcp --dport 8443 -j DNAT --to-destination 192.168.1.20
  post-down brctl delbr qvdnet0
  address 192.168.1.20
  netmask 255.255.255.0


Any help would be appreciated.

Thanks

---

### Post by zfKcMb4 on 2013-08-04
Anybody?  Any ideas?

---

