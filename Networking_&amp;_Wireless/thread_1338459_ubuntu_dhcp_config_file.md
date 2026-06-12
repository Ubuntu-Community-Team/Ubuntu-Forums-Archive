---
title: "ubuntu dhcp config file"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by navinderbawa on 2009-11-26
i am trying to configure ubuntu 9.10 but without any sucess foe DHCP . I have following entry in dhcp config file
 
#for Helia labs
# Copyright 2006 Tero Karvinen [http://www.iki.fi/karvinen/ubuntu_dhcp.html](http://www.iki.fi/karvinen/ubuntu_dhcp.html)
# License: GNU General Public License, version 2 or later
# ChangeLog:
# 2006-03-27 Initial version, testing in Helia labs
 
# Don't set "authoritative" until everything else is correct in dhcpd.conf
authoritative; # Warning: this overrides other DHCP servers
# Default options in Ubuntu:
ddns-update-style none;
default-lease-time 600;
max-lease-time 7200;
log-facility local7;
# Subnet row defines server's network card. Also set in "/etc/default/dhcp3-server"
# 'ifconfig' shows subnet (ipaddress, zeroes as in mask) and netmask
subnet 172.28.0.0 netmask 255.255.0.0 {
host navinder-laptop {
# 'ping target_host', 'arp' shows MAC address
# only give DHCP information to this computer:
hardware ethernet 00:0D:56:73:F0:0D;
# Basic DHCP info (see 'ifconfig', 'route', 'cat /etc/resolv.conf')
fixed-address 172.28.1.7;
option subnet-mask 255.255.0.0;
option routers 172.28.1.254;
option domain-name-servers 172.28.1.67, 172.28.1.69, 192.168.1.1;
# Non-essential DHCP options
option domain-name "tielab.helia.fi";
}
}
# 'sudo /etc/init.d/dhcp3-server force-reload'
# [http://www.iki.fi/karvinen/ubuntu_dhcp.html](http://www.iki.fi/karvinen/ubuntu_dhcp.html)
 
~ 
~ 
~ 
 
please , also, tell me what is a domain name, how to find it?
i have been using this dhcp client to install oracle on my desktop ubuntp editionm.

---

### Post by navinderbawa on 2009-11-27
I have tried many sources available on net to configure DHCP3-server, but remain unsucessfull. The entry in dphc.config file asks about DOMAIN name. is it the computer name? if some one can provide me with there enteries in dphc.config, resolv file other files which are required to be changed. I Have ubuntu 9.10
 
> **navinderbawa said:**
> i am trying to configure ubuntu 9.10 but without any sucess foe DHCP . I have following entry in dhcp config file
 
#for Helia labs
# Copyright 2006 Tero Karvinen [http://www.iki.fi/karvinen/ubuntu_dhcp.html](http://www.iki.fi/karvinen/ubuntu_dhcp.html)
# License: GNU General Public License, version 2 or later
# ChangeLog:
# 2006-03-27 Initial version, testing in Helia labs
 
# Don't set "authoritative" until everything else is correct in dhcpd.conf
authoritative; # Warning: this overrides other DHCP servers
# Default options in Ubuntu:
ddns-update-style none;
default-lease-time 600;
max-lease-time 7200;
log-facility local7;
# Subnet row defines server's network card. Also set in "/etc/default/dhcp3-server"
# 'ifconfig' shows subnet (ipaddress, zeroes as in mask) and netmask
subnet 172.28.0.0 netmask 255.255.0.0 {
host navinder-laptop {
# 'ping target_host', 'arp' shows MAC address
# only give DHCP information to this computer:
hardware ethernet 00:0D:56:73:F0:0D;
# Basic DHCP info (see 'ifconfig', 'route', 'cat /etc/resolv.conf')
fixed-address 172.28.1.7;
option subnet-mask 255.255.0.0;
option routers 172.28.1.254;
option domain-name-servers 172.28.1.67, 172.28.1.69, 192.168.1.1;
# Non-essential DHCP options
option domain-name "tielab.helia.fi";
}
}
# 'sudo /etc/init.d/dhcp3-server force-reload'
# [http://www.iki.fi/karvinen/ubuntu_dhcp.html](http://www.iki.fi/karvinen/ubuntu_dhcp.html)
 
~ 
~ 
~ 
 
please , also, tell me what is a domain name, how to find it?
i have been using this dhcp client to install oracle on my desktop ubuntp editionm.

---

