---
title: "webmin can't find dhcp3-server"
date: 2011-08-10
forum: Networking &amp; Wireless
---

### Post by jewfromdahood on 2011-08-10
I installed webmin to be a web gui for the router I am trying to set up on a linux server for the business. And for some reason webmin can't see it. which is fine by me, unfortunately the other IT people are lazy windows people and need a GUI for troubleshooting. I am happy with an SSH to the server. but whatever. Can I get a little help I get this 
"The DHCP server /usr/sbin/dhcpd3 could not be found on your system. Maybe it is not installed, or your DHCP module configuration is incorrect.

The ISC DHCPd package can be automatically installed by Webmin. Click here to have it downloaded and installed using APT."

I know for a fact it is installed.

I want to get rid of this Cisco RV042 router as soon as possible so I can start using a complete open-source backbone on a gigabit ethernet.

---

### Post by jewfromdahood on 2011-08-10
figured it out did some digging in the OS and edited the following... Voila

DHCP server config file /etc/dhcp/dhcpd.conf 
DHCP server executable /usr/sbin/dhcpd 
Command to start DHCP server /etc/init.d/isc-dhcp-server start 
Command to apply configuration /etc/init.d/isc-dhcp-server restart 
Command to stop DHCP server /etc/init.d/isc-dhcp-server stop 
Path to DHCP server PID file /var/run/dhcp-server/dhcpd.pid 
DHCP server lease file /var/lib/dhcp/dhcpd.leases

---

