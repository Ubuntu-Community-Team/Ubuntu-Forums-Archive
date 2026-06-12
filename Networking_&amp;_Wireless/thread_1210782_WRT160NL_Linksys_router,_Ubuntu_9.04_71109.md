---
title: "WRT160NL Linksys router, Ubuntu 9.04 7/11/09"
date: 2009-07-11
forum: Networking &amp; Wireless
---

### Post by Wolvenreign on 2009-07-11
(Excuse me if this sounds rude. This is a copy and paste from my paid Experts Exchange post. So if it sounds business-y, that's why. I appreciate the time you guys give for free. Ahem)

Salutations.

     I am running Ubuntu/Kubuntu 9.04 64-bit, Jaunty Jackalope, currently updated completely at 9:44. My motherboard is MSI 790GX-G65, with an AMD Phenom II CPU and two routers. One currently works as a wired router, but is being replaced due to it's wireless dying. It is a Netgear WGT624v3. The router I am currently migrating to is a WRT160NL. I have gone to it's configuration page and set up everything to the settings provided by my ISP, Comcast. It is set to use DHCP and automatically acquire the IP address. However, it doesn't appear to obtain any IP address, as the IP address on the "Status" tab is content with 0.0.0.0. As you may have guessed, this means I cannot connect to the internet through this router.

     Something rather peculiar about this is that we cannot plug the computer directly into the modem and get an internet connection, but we can plug it into the Netgear WGT624v3 and we will have a connection. At any rate, I did some research into the problem, and it seems that Jaunty Jackalope's Dhclient.conf, the file which tells Ubuntu how to dynamically obtain IPs, has a small typo in it that prevents it from connecting correctly. I tried as those guides had said, but everytime I attempted to run with the new file, it wouldn't let me obtain a connection, even on my old router.

     My Dhclient, unmodified, is posted in the code box. I need this file fixed, if it is the problem, or if it is not the problem, then I need to know how to get my new router to obtain the dynamic IP. Gentlemen....start your engines.

```
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
```

---

