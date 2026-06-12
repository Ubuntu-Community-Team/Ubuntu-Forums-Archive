---
title: "Problem With Internet Under Easy Peasy"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by nathanpc on 2009-07-29
Hello,
I have an *Eee PC 904D* that i use for development, because it's tiny and little, but i have a *PC* too. But in my *Eee PC* that i have *Ubuntu Intrepid Ibex* with the *Netbook Remix*(*Easy Peasy*), when i want to use the ethernet cable for the internet i connect it and tryes to connect, but in aproximatly 10 secs trying to connect it fails and change the icon like i don't put any cable, but the cable is connected and other computers when i try to use this cable connect normally. Sorry about my english.

Thanks,
Nathan Paulino Campos

---

### Post by superprash2003 on 2009-07-29
make sure that the router you are trying to connect to has DHCP enabled , looks like you arent getting an ip

---

### Post by nathanpc on 2009-07-29
Hello superprash2003,
 It's all ok, because when i try to use the wireless network at my home all looks good, but in my home too and in every place, this happens with the cable, and in my home i have a PC that i test the cable and all is good.

Thanks,
 Nathan Paulino Campos

---

### Post by superprash2003 on 2009-07-30
post contents of  /etc/dhcp3/dhclient.conf file

---

### Post by nathanpc on 2009-08-01
Here is the content:
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

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, domain-search, host-name,
	netbios-name-servers, netbios-scope, interface-mtu;
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

### Post by superprash2003 on 2009-08-04
post output of **sudo dhclient eth0**

---

### Post by superprash2003 on 2009-08-04
post output of **sudo dhclient eth0**

---

