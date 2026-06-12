---
title: "Jaunty/Mint 7: eth0 won't auto connect after router reboot"
date: 2009-07-17
forum: Networking &amp; Wireless
---

### Post by mibadt on 2009-07-17
Hi,
I'm on  a fully updated Linux Mint 7 (derivative of Ubuntu 9.04), connected via eth0 to a physical LAN with a router (providing DHCP services for LAN members too) and an ADSL "modem".
Every time I reboot the router ( I have to do it once a day), this PC won't renew its IP address lease (ifconfig shows no IP address), whereas another PC on the same LAN reconnects within 15 seconds.
Naturally, running "sudo dhclient" on the Mint PC solves the problem, but **I'd prefer to do it automatically**.

Below please find the Mint dhclient.conf (standard except for DNS modification).

Please advise!

Thanks!

Regards,
Michael Badt

-------Mint dhcliet.conf-----------------------
# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, domain-search, host-name,
	netbios-name-servers, netbios-scope, interface-mtu,
	rfc3442-classless-static-routes, ntp-servers;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
-------------------------

---

### Post by Tman5293 on 2009-07-17
Is there an important reason why you have to reboot the router cause if there isn't then you should stop doing it.

---

### Post by mibadt on 2009-07-17
Thanks, unfortunately, I DO have to reboot at least the ADSL modem (poor local internet infrastructure, reboots speeds up Internet speed). So far. I've always rebooted both the ADSL modem **and** the nearby router (just in case...), next time I'll try to reboot only modem

Yet, I'd like to **get an answer to my original question** namely, how to configure the Mint to **automatically renew dhcp lease **(like my other Linux PC on smae LAN)?

Best Regards,

Michael Badt

---

### Post by sam_delta on 2009-08-03
im also interested in the original question

sam

---

