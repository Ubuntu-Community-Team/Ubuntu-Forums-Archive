---
title: "ltsp boot problems."
date: 2013-03-17
forum: Networking &amp; Wireless
---

### Post by vidyadhara on 2013-03-17
I have set the client to do a pxe boot from the server.

The server dhcp configuration file is the following (at /etc/ltsp/dhcpd.conf)

----
#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 192.168.2.0 netmask 255.255.255.0 {
range 192.168.2.20 192.168.2.250;
option domain-name-servers 192.168.2.1;
option broadcast-address 192.168.2.255;
option routers 192.168.2.1;
next-server 192.168.2.2;
get-lease-hostnames true;
option subnet-mask 255.255.255.0;
option root-path "/opt/ltsp/i386";
if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
filename "/ltsp/i386/pxelinux.0";
} else {
filename "/ltsp/i386/nbi.img";
}
}
----

I turned off all boot options in the bios of the client except the pxe lan boot.

The client comes up displays a pxe 2.0 message waits for some time and informs me that it was not able to get an address from the dhcp server.

However it then boots up from the disk and acquires an address from the same server. This seems to be a bios behavior using the hdd to boot even if it is not included in the boot sequence. That is a different problem.


I have a very simple router with dhcp turned off that is my connection to the internet.
the ip address on the router is 192.168.2.1

the error log on the server (/var/log/syslog) shows, a sequence like thus.

Mar 14 22:47:06 v--------- dhcpd: DHCPDISCOVER from 00:e0:4c:10:06:9c via eth0
Mar 14 22:47:07 v--------- dhcpd: DHCPOFFER on 192.168.2.21 to 00:e0:4c:10:06:9c via eth0
Mar 14 22:47:07 v--------- dhcpd: BOOTREQUEST from 00:e0:4c:10:06:9c via eth0: BOOTP from dynamic client and no dynamic leases
Mar 14 22:47:08 v--------- dhcpd: DHCPREQUEST for 172.31.254.254 (10.254.254.254) from 00:e0:4c:10:06:9c via eth0: wrong network.
Mar 14 22:47:08 v--------- dhcpd: DHCPNAK on 172.31.254.254 to 00:e0:4c:10:06:9c via eth0
Mar 14 22:47:08 v--------- dhcpd: DHCPREQUEST for 172.31.254.254 from 00:e0:4c:10:06:9c via eth0: wrong network.
Mar 14 22:47:08 v--------- dhcpd: DHCPNAK on 172.31.254.254 to 00:e0:4c:10:06:9c via eth0
Mar 14 22:47:08 v--------- dhcpd: DHCPREQUEST for 172.31.254.254 from 00:e0:4c:10:06:9c via eth0: unknown lease 172.31.254.254.
Mar 14 22:50:02 v--------- dhcpd: DHCPDISCOVER from 00:e0:4c:10:06:9c via eth0
Mar 14 22:50:03 v--------- dhcpd: DHCPOFFER on 192.168.2.22 to 00:e0:4c:10:06:9c (v----------desktop) via eth0
Mar 14 22:50:03 v--------- dhcpd: DHCPREQUEST for 192.168.2.22 (192.168.2.2) from 00:e0:4c:10:06:9c (v----------desktop) via eth0
Mar 14 22:50:03 v--------- dhcpd: DHCPACK on 192.168.2.22 to 00:e0:4c:10:06:9c (v----------desktop) via eth0
Mar 14 22:50:04 v--------- dhcpd: DHCPDISCOVER from 00:e0:4c:10:06:9c via eth0
Mar 14 22:50:04 v--------- dhcpd: ICMP Echo Reply for 192.168.2.22 late or spurious.
Mar 14 22:50:04 v--------- dhcpd: BOOTREQUEST from 00:e0:4c:10:06:9c via eth0: BOOTP from dynamic client and no dynamic leases
Mar 14 22:50:05 v--------- dhcpd: DHCPOFFER on 192.168.2.21 to 00:e0:4c:10:06:9c via eth0
Mar 14 22:50:05 v--------- dhcpd: DHCPREQUEST for 172.31.254.254 (10.254.254.254) from 00:e0:4c:10:06:9c via eth0: wrong network.
Mar 14 22:50:05 v--------- dhcpd: DHCPNAK on 172.31.254.254 to 00:e0:4c:10:06:9c via eth0
Mar 14 22:50:05 v--------- dhcpd: DHCPREQUEST for 172.31.254.254 from 00:e0:4c:10:06:9c via eth0: wrong network.
Mar 14 22:50:05 v--------- dhcpd: DHCPNAK on 172.31.254.254 to 00:e0:4c:10:06:9c via eth0
Mar 14 22:50:05 v--------- dhcpd: DHCPREQUEST for 172.31.254.254 from 00:e0:4c:10:06:9c via eth0: unknown lease 172.31.254.254.
Mar 14 22:55:09 v--------- dhcpd: DHCPDISCOVER from 00:e0:4c:10:06:9c via eth0
Mar 14 22:55:10 v--------- dhcpd: DHCPOFFER on 192.168.2.21 to 00:e0:4c:10:06:9c via eth0
Mar 14 22:55:10 v--------- dhcpd: BOOTREQUEST from 00:e0:4c:10:06:9c via eth0: BOOTP from dynamic client and no dynamic leases
Mar 14 22:55:11 v--------- dhcpd: DHCPREQUEST for 172.31.254.254 (10.254.254.254) from 00:e0:4c:10:06:9c via eth0: wrong network.
Mar 14 22:55:11 v--------- dhcpd: DHCPNAK on 172.31.254.254 to 00:e0:4c:10:06:9c via eth0

--
Now a constant chatter seems to be on between the client (actually an autonomous machine now) and the server.
every few seconds a new round of discover, offer request and nak are doing the rounds.


---
Mar 15 03:17:01 v--------- CRON[6257]: (root) CMD ( cd / && run-parts --report /etc/cron.hourly)
Mar 15 03:19:17 v--------- dhcpd: DHCPDISCOVER from 00:e0:4c:10:06:9c via eth0
Mar 15 03:19:18 v--------- dhcpd: DHCPOFFER on 192.168.2.21 to 00:e0:4c:10:06:9c via eth0
Mar 15 03:19:18 v--------- dhcpd: BOOTREQUEST from 00:e0:4c:10:06:9c via eth0: BOOTP from dynamic client and no dynamic leases
Mar 15 03:19:23 v--------- dhcpd: DHCPREQUEST for 172.31.254.254 (10.254.254.254) from 00:e0:4c:10:06:9c via eth0: wrong network.
Mar 15 03:19:23 v--------- dhcpd: DHCPNAK on 172.31.254.254 to 00:e0:4c:10:06:9c via eth0
Mar 15 03:19:23 v--------- dhcpd: DHCPREQUEST for 172.31.254.254 from 00:e0:4c:10:06:9c via eth0: wrong network.
Mar 15 03:19:23 v--------- dhcpd: DHCPNAK on 172.31.254.254 to 00:e0:4c:10:06:9c via eth0
Mar 15 03:19:23 v--------- dhcpd: DHCPREQUEST for 172.31.254.254 from 00:e0:4c:10:06:9c via eth0: unknown lease 172.31.254.254.
--

can someone help me with this thing.

I need to get ltsp running in a public service organization for allowing a minimal level of IT ability on a shoe string budget and some charity.

Thanks a ton in advance for any help.

regards
vidyadhara buddhiraju

---

