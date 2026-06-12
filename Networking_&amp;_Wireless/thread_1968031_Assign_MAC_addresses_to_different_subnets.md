---
title: "Assign MAC addresses to different subnets"
date: 2012-04-28
forum: Networking &amp; Wireless
---

### Post by Leldoren on 2012-04-28
Hello all,

I have an Ubuntu server setup as a dual-interface firewall running DNS and DHCP. ETH0=WAN, ETH1=LAN. ETH1 is connected to a switch. A wireless access point in bridge mode is also connected to the switch. I have made an inventory of all the network devices in my house and their MAC addresses and would like to used DHCPd to assign them to two different subnets. I have created the two subnets in BIND and host reservations that should be assigning IP's from one of the two subnets I have specified. The problem is, the devices are all being assinged IP's from the first subnet, nothing is pulling from the second.

My goal is to have subnet A point to Google DNS servers, and subnet B point to OPENDNS with filtering.

Any ideas?

---

### Post by SeijiSensei on 2012-04-28
It sounds like your trying to do "host reservations" in BIND, but that may just be the way you wrote that sentence.  To assign specific IP addresses to specific MAC addresses, you use the "host" directive in [dhcpd.conf]("http://www.centos.org/docs/5/html/Deployment_Guide-en-US/s1-dhcp-configuring-server.html").  If you've tried doing that already and it's not working, you probably haven't nested the host directives in a group or subnet stanza correctly.

---

### Post by Leldoren on 2012-04-28
[FONT=Fixedsys]Here is an example of my dhcpd.conf. Host test1, based on its mac address should be assigned to subnet 1 with dns server 192.168.0.254. Host 2 should be assigned to subnet 2 and dns server [/FONT][FONT=Fixedsys]208.67.222.222 , 208.67.220.220.[/FONT]
[FONT=Fixedsys]
#Subnet 1
[/FONT][FONT=Fixedsys]subnet 192.168.0.0 netmask 255.255.255.0 {
[/FONT][FONT=Fixedsys]	option time-servers 192.168.0.254;[/FONT]
  [FONT=Fixedsys]	option domain-name-servers 192.168.0.254;[/FONT]
  [FONT=Fixedsys]	option domain-name "my.lan";[/FONT]
  [FONT=Fixedsys]	option broadcast-address 192.168.0.255;[/FONT]
  [FONT=Fixedsys]	option subnet-mask 255.255.255.0;[/FONT]
  [FONT=Fixedsys]	option routers 192.168.0.254;[/FONT]
[FONT=Fixedsys]range 192.168.0.100 192.168.0.199;[/FONT] [FONT=Fixedsys]	# Test1[/FONT]
 [FONT=Fixedsys]	host test1 {[/FONT]
 [FONT=Fixedsys]		hardware ethernet 00:00:00:00:00:01;[/FONT]
 [FONT=Fixedsys]		}[/FONT]
[FONT=Fixedsys]}

[/FONT] [FONT=Fixedsys]# Subnet 2
[/FONT]
 [FONT=Fixedsys]subnet 192.168.1.0 netmask 255.255.255.0 {[/FONT]
 [FONT=Fixedsys]	option time-servers 192.168.0.254;[/FONT]
 [FONT=Fixedsys]	option domain-name-servers 208.67.222.222 , 208.67.220.220;[/FONT]
 [FONT=Fixedsys]	option domain-name "my.lan";[/FONT]
 [FONT=Fixedsys]	option broadcast-address 192.168.1.255;[/FONT]
 [FONT=Fixedsys]	option subnet-mask 255.255.255.0;[/FONT]
 [FONT=Fixedsys]	option routers 192.168.0.254;[/FONT]
 [FONT=Fixedsys]	range 192.168.1.100 192.168.1.199;[/FONT]
 [FONT=Fixedsys]	# Test2[/FONT]
 [FONT=Fixedsys]	host test2 {[/FONT]
 [FONT=Fixedsys]		hardware ethernet [/FONT][FONT=Fixedsys]00:00:00:00:00:02[/FONT][FONT=Fixedsys];[/FONT]
 [FONT=Fixedsys]		}[/FONT]
[FONT=Fixedsys]}[/FONT]

---

### Post by SeijiSensei on 2012-04-28
I take it those aren't the real MAC addresses.

I'm pretty sure you have to assign the address statically with the "fixed-address" directive in the host stanza. Look at the examples in the document I linked to and the file dhcpd.conf.sample which should be somewhere in /usr/share/doc/.

---

