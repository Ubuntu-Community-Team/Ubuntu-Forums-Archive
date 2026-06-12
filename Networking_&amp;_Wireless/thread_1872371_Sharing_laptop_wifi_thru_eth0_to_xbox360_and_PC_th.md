---
title: "Sharing laptop wifi thru eth0 to xbox360 and PC thru router"
date: 2011-10-30
forum: Networking &amp; Wireless
---

### Post by mafi127 on 2011-10-30
I have one laptop what I'm using to download stuff and surf web and I have another PC what is made for media center( it dosent have wifi card) and I allso have xbox360.

 I want to make that I'm connected to wifi whit my laptop and I want to share my wifi connection thru ethernet(eth0) to router what is connected to mu mc and xbox360. So that they all have internet connection.

 I have folowed whit this guid [https://help.ubuntu.com/community/EasyWirelessToWiredConnectionSharing](https://help.ubuntu.com/community/EasyWirelessToWiredConnectionSharing) and I only get lan connection, but not internet. I dont underestand what is the problem. 

can someone help me out whit this problem plz, I realy need help in here :confused:

I run thows commands and got this

cat /etc/dhcp3/dhcpd.conf sudo cat /var/log/syslog | grep -i dhcp ifconfig -a


[PHP]tamps@mafia:~$ cat /etc/dhcp3/dhcpd.conf
ddns-update-style interim;
ignore client-updates;

subnet 10.0.0.0 netmask 255.255.255.0 {
    option routers 10.0.0.1;
    option subnet-mask 255.255.255.0;
    option domain-name-servers 192.168.2.1;
    option ip-forwarding off;
    range dynamic-bootp 10.0.0.2 10.0.0.200;
    default-lease-time 21600;
    max-lease-time 43200;
}
tamps@mafia:~$[/PHP][PHP]Oct 30 18:38:06 mafia dhcpd:    you want, please write a subnet declaration
Oct 30 18:38:06 mafia dhcpd:    in your dhcpd.conf file for the network segment
Oct 30 18:38:06 mafia dhcpd:    to which interface eth1 is attached. **
Oct 30 18:38:06 mafia dhcpd: 
Oct 30 18:38:06 mafia dhcpd: 
Oct 30 18:38:06 mafia dhcpd: No subnet declaration for eth0 (10.42.43.1).
Oct 30 18:38:06 mafia dhcpd: ** Ignoring requests on eth0.  If this is not what
Oct 30 18:38:06 mafia dhcpd:    you want, please write a subnet declaration
Oct 30 18:38:06 mafia dhcpd:    in your dhcpd.conf file for the network segment
Oct 30 18:38:06 mafia dhcpd:    to which interface eth0 is attached. **
Oct 30 18:38:06 mafia dhcpd: 
Oct 30 18:38:06 mafia dhcpd: 
Oct 30 18:38:06 mafia dhcpd: Not configured to listen on any interfaces!
Oct 30 18:49:57 mafia NetworkManager[1077]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 11570
Oct 30 18:51:46 mafia dnsmasq[16971]: compile time options: IPv6 GNU-getopt DBus I18N DHCP TFTP IDN
Oct 30 18:51:46 mafia dnsmasq-dhcp[16971]: DHCP, IP range 10.42.43.10 -- 10.42.43.100, lease time 1h
Oct 30 18:51:49 mafia NetworkManager[16939]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct 30 18:51:49 mafia dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct 30 18:51:49 mafia dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 18:51:49 mafia dhclient: /var/lib/dhcp/dhclient-5ba6801d-1c98-456e-86fc-512fee3e7a90-wlan0.lease line 12: semicolon expected.
Oct 30 18:51:49 mafia dhclient: /var/lib/dhcp/dhclient-5ba6801d-1c98-456e-86fc-512fee3e7a90-wlan0.lease line 14: semicolon expected.
Oct 30 18:51:49 mafia dhclient: /var/lib/dhcp/dhclient-5ba6801d-1c98-456e-86fc-512fee3e7a90-wlan0.lease line 14: unterminated lease declaration.
Oct 30 18:51:49 mafia NetworkManager[16939]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Oct 30 18:51:49 mafia dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 30 18:51:50 mafia dhclient: DHCPOFFER of 192.168.2.2 from 192.168.2.1
Oct 30 18:51:50 mafia dhclient: DHCPREQUEST of 192.168.2.2 on wlan0 to 255.255.255.255 port 67
Oct 30 18:51:52 mafia dhclient: DHCPREQUEST of 192.168.2.2 on wlan0 to 255.255.255.255 port 67
Oct 30 18:51:57 mafia dhclient: DHCPREQUEST of 192.168.2.2 on wlan0 to 255.255.255.255 port 67
Oct 30 18:51:58 mafia dhclient: DHCPACK of 192.168.2.2 from 192.168.2.1
Oct 30 18:51:58 mafia NetworkManager[16939]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Oct 30 18:51:59 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 18:51:59 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 18:51:59 mafia dhcpd: All rights reserved.
Oct 30 18:51:59 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 18:52:01 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 18:52:01 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 18:52:01 mafia dhcpd: All rights reserved.
Oct 30 18:52:01 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 18:52:01 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 18:52:01 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 18:52:01 mafia dhcpd: All rights reserved.
Oct 30 18:52:01 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 18:52:01 mafia dhcpd: Wrote 0 leases to leases file.
Oct 30 18:52:01 mafia dhcpd: 
Oct 30 18:52:01 mafia dhcpd: No subnet declaration for eth1 (no IPv4 addresses).
Oct 30 18:52:01 mafia dhcpd: ** Ignoring requests on eth1.  If this is not what
Oct 30 18:52:01 mafia dhcpd:    you want, please write a subnet declaration
Oct 30 18:52:01 mafia dhcpd:    in your dhcpd.conf file for the network segment
Oct 30 18:52:01 mafia dhcpd:    to which interface eth1 is attached. **
Oct 30 18:52:01 mafia dhcpd: 
Oct 30 18:52:01 mafia dhcpd: 
Oct 30 18:52:01 mafia dhcpd: No subnet declaration for eth0 (10.42.43.1).
Oct 30 18:52:01 mafia dhcpd: ** Ignoring requests on eth0.  If this is not what
Oct 30 18:52:01 mafia dhcpd:    you want, please write a subnet declaration
Oct 30 18:52:01 mafia dhcpd:    in your dhcpd.conf file for the network segment
Oct 30 18:52:01 mafia dhcpd:    to which interface eth0 is attached. **
Oct 30 18:52:01 mafia dhcpd: 
Oct 30 18:52:01 mafia dhcpd: 
Oct 30 18:52:01 mafia dhcpd: Not configured to listen on any interfaces!
Oct 30 19:03:09 mafia kernel: [   13.835020] type=1400 audit(1319994185.284:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=755 comm="apparmor_parser"
Oct 30 19:03:09 mafia kernel: [   13.835236] type=1400 audit(1319994185.284:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=707 comm="apparmor_parser"
Oct 30 19:03:09 mafia kernel: [   13.836952] type=1400 audit(1319994185.284:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=848 comm="apparmor_parser"
Oct 30 19:03:18 mafia kernel: [   26.627338] type=1400 audit(1319994198.072:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1164 comm="apparmor_parser"
Oct 30 19:03:21 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 19:03:21 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 19:03:21 mafia dhcpd: All rights reserved.
Oct 30 19:03:21 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 19:03:22 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 19:03:22 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 19:03:22 mafia dhcpd: All rights reserved.
Oct 30 19:03:22 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 19:03:22 mafia dhcpd: Wrote 0 leases to leases file.
Oct 30 19:03:22 mafia dhcpd: 
Oct 30 19:03:22 mafia dhcpd: No subnet declaration for eth1 (no IPv4 addresses).
Oct 30 19:03:22 mafia dhcpd: ** Ignoring requests on eth1.  If this is not what
Oct 30 19:03:22 mafia dhcpd:    you want, please write a subnet declaration
Oct 30 19:03:22 mafia dhcpd:    in your dhcpd.conf file for the network segment
Oct 30 19:03:22 mafia dhcpd:    to which interface eth1 is attached. **
Oct 30 19:03:22 mafia dhcpd: 
Oct 30 19:03:22 mafia dhcpd: 
Oct 30 19:03:22 mafia dhcpd: No subnet declaration for eth0 (10.42.43.1).
Oct 30 19:03:22 mafia dhcpd: ** Ignoring requests on eth0.  If this is not what
Oct 30 19:03:22 mafia dhcpd:    you want, please write a subnet declaration
Oct 30 19:03:22 mafia dhcpd:    in your dhcpd.conf file for the network segment
Oct 30 19:03:22 mafia dhcpd:    to which interface eth0 is attached. **
Oct 30 19:03:22 mafia dhcpd: 
Oct 30 19:03:22 mafia dhcpd: 
Oct 30 19:03:22 mafia dhcpd: Not configured to listen on any interfaces!
Oct 30 19:03:25 mafia dnsmasq[1401]: compile time options: IPv6 GNU-getopt DBus I18N DHCP TFTP IDN
Oct 30 19:03:25 mafia dnsmasq-dhcp[1401]: DHCP, IP range 10.42.43.10 -- 10.42.43.100, lease time 1h
Oct 30 19:03:28 mafia NetworkManager[1109]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct 30 19:03:29 mafia dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct 30 19:03:29 mafia dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 19:03:32 mafia dhclient: /var/lib/dhcp/dhclient-5ba6801d-1c98-456e-86fc-512fee3e7a90-wlan0.lease line 12: semicolon expected.
Oct 30 19:03:32 mafia dhclient: /var/lib/dhcp/dhclient-5ba6801d-1c98-456e-86fc-512fee3e7a90-wlan0.lease line 14: semicolon expected.
Oct 30 19:03:32 mafia dhclient: /var/lib/dhcp/dhclient-5ba6801d-1c98-456e-86fc-512fee3e7a90-wlan0.lease line 14: unterminated lease declaration.
Oct 30 19:03:32 mafia NetworkManager[1109]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Oct 30 19:03:32 mafia dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 30 19:03:32 mafia dhclient: DHCPOFFER of 192.168.2.2 from 192.168.2.1
Oct 30 19:03:32 mafia dhclient: DHCPREQUEST of 192.168.2.2 on wlan0 to 255.255.255.255 port 67
Oct 30 19:03:34 mafia dhclient: DHCPREQUEST of 192.168.2.2 on wlan0 to 255.255.255.255 port 67
Oct 30 19:03:35 mafia dhclient: DHCPACK of 192.168.2.2 from 192.168.2.1
Oct 30 19:03:35 mafia NetworkManager[1109]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Oct 30 19:03:39 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 19:03:39 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 19:03:39 mafia dhcpd: All rights reserved.
Oct 30 19:03:39 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 19:03:41 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 19:03:41 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 19:03:41 mafia dhcpd: All rights reserved.
Oct 30 19:03:41 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 19:03:41 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 19:03:41 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 19:03:41 mafia dhcpd: All rights reserved.
Oct 30 19:03:41 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 19:03:41 mafia dhcpd: Wrote 0 leases to leases file.
Oct 30 19:03:41 mafia dhcpd: 
Oct 30 19:03:41 mafia dhcpd: No subnet declaration for eth1 (no IPv4 addresses).
Oct 30 19:03:41 mafia dhcpd: ** Ignoring requests on eth1.  If this is not what
Oct 30 19:03:41 mafia dhcpd:    you want, please write a subnet declaration
Oct 30 19:03:41 mafia dhcpd:    in your dhcpd.conf file for the network segment
Oct 30 19:03:41 mafia dhcpd:    to which interface eth1 is attached. **
Oct 30 19:03:41 mafia dhcpd: 
Oct 30 19:03:41 mafia dhcpd: 
Oct 30 19:03:41 mafia dhcpd: No subnet declaration for eth0 (10.42.43.1).
Oct 30 19:03:41 mafia dhcpd: ** Ignoring requests on eth0.  If this is not what
Oct 30 19:03:41 mafia dhcpd:    you want, please write a subnet declaration
Oct 30 19:03:41 mafia dhcpd:    in your dhcpd.conf file for the network segment
Oct 30 19:03:41 mafia dhcpd:    to which interface eth0 is attached. **
Oct 30 19:03:41 mafia dhcpd: 
Oct 30 19:03:41 mafia dhcpd: 
Oct 30 19:03:41 mafia dhcpd: Not configured to listen on any interfaces!
Oct 30 19:04:34 mafia NetworkManager[1109]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1562
Oct 30 19:05:15 mafia dnsmasq[4929]: compile time options: IPv6 GNU-getopt DBus I18N DHCP TFTP IDN
Oct 30 19:05:15 mafia dnsmasq-dhcp[4929]: DHCP, IP range 10.42.43.10 -- 10.42.43.100, lease time 1h
Oct 30 19:05:18 mafia NetworkManager[4897]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct 30 19:05:18 mafia dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct 30 19:05:18 mafia dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 19:05:18 mafia dhclient: /var/lib/dhcp/dhclient-5ba6801d-1c98-456e-86fc-512fee3e7a90-wlan0.lease line 12: semicolon expected.
Oct 30 19:05:18 mafia dhclient: /var/lib/dhcp/dhclient-5ba6801d-1c98-456e-86fc-512fee3e7a90-wlan0.lease line 14: semicolon expected.
Oct 30 19:05:18 mafia dhclient: /var/lib/dhcp/dhclient-5ba6801d-1c98-456e-86fc-512fee3e7a90-wlan0.lease line 14: unterminated lease declaration.
Oct 30 19:05:18 mafia NetworkManager[4897]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Oct 30 19:05:18 mafia dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 30 19:05:20 mafia dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Oct 30 19:05:26 mafia dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 30 19:05:26 mafia dhclient: DHCPOFFER of 192.168.2.2 from 192.168.2.1
Oct 30 19:05:26 mafia dhclient: DHCPREQUEST of 192.168.2.2 on wlan0 to 255.255.255.255 port 67
Oct 30 19:05:28 mafia dhclient: DHCPREQUEST of 192.168.2.2 on wlan0 to 255.255.255.255 port 67
Oct 30 19:05:31 mafia dhclient: DHCPREQUEST of 192.168.2.2 on wlan0 to 255.255.255.255 port 67
Oct 30 19:05:32 mafia dhclient: DHCPACK of 192.168.2.2 from 192.168.2.1
Oct 30 19:05:32 mafia NetworkManager[4897]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Oct 30 19:05:33 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 19:05:33 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 19:05:33 mafia dhcpd: All rights reserved.
Oct 30 19:05:33 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 19:05:35 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 19:05:35 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 19:05:35 mafia dhcpd: All rights reserved.
Oct 30 19:05:35 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 19:05:35 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 19:05:35 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 19:05:35 mafia dhcpd: All rights reserved.
Oct 30 19:05:35 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 19:05:35 mafia dhcpd: Wrote 0 leases to leases file.
Oct 30 19:05:35 mafia dhcpd: 
Oct 30 19:05:35 mafia dhcpd: No subnet declaration for eth1 (no IPv4 addresses).
Oct 30 19:05:35 mafia dhcpd: ** Ignoring requests on eth1.  If this is not what
Oct 30 19:05:35 mafia dhcpd:    you want, please write a subnet declaration
Oct 30 19:05:35 mafia dhcpd:    in your dhcpd.conf file for the network segment
Oct 30 19:05:35 mafia dhcpd:    to which interface eth1 is attached. **
Oct 30 19:05:35 mafia dhcpd: 
Oct 30 19:05:35 mafia dhcpd: 
Oct 30 19:05:35 mafia dhcpd: No subnet declaration for eth0 (10.42.43.1).
Oct 30 19:05:35 mafia dhcpd: ** Ignoring requests on eth0.  If this is not what
Oct 30 19:05:35 mafia dhcpd:    you want, please write a subnet declaration
Oct 30 19:05:35 mafia dhcpd:    in your dhcpd.conf file for the network segment
Oct 30 19:05:35 mafia dhcpd:    to which interface eth0 is attached. **
Oct 30 19:05:35 mafia dhcpd: 
Oct 30 19:05:35 mafia dhcpd: 
Oct 30 19:05:35 mafia dhcpd: Not configured to listen on any interfaces!
Oct 30 19:09:03 mafia kernel: [   22.432861] type=1400 audit(1319994543.886:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=724 comm="apparmor_parser"
Oct 30 19:09:03 mafia kernel: [   22.434999] type=1400 audit(1319994543.886:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=730 comm="apparmor_parser"
Oct 30 19:09:04 mafia kernel: [   23.056419] type=1400 audit(1319994544.510:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1081 comm="apparmor_parser"
Oct 30 19:09:06 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 19:09:06 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 19:09:06 mafia dhcpd: All rights reserved.
Oct 30 19:09:06 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 19:09:06 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 19:09:06 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 19:09:06 mafia dhcpd: All rights reserved.
Oct 30 19:09:06 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 19:09:06 mafia dhcpd: Wrote 0 leases to leases file.
Oct 30 19:09:07 mafia dhcpd: 
Oct 30 19:09:07 mafia dhcpd: No subnet declaration for eth1 (no IPv4 addresses).
Oct 30 19:09:07 mafia dhcpd: ** Ignoring requests on eth1.  If this is not what
Oct 30 19:09:07 mafia dhcpd:    you want, please write a subnet declaration
Oct 30 19:09:07 mafia dhcpd:    in your dhcpd.conf file for the network segment
Oct 30 19:09:07 mafia dhcpd:    to which interface eth1 is attached. **
Oct 30 19:09:07 mafia dhcpd: 
Oct 30 19:09:07 mafia dhcpd: 
Oct 30 19:09:07 mafia dhcpd: No subnet declaration for eth0 (10.42.43.1).
Oct 30 19:09:07 mafia dhcpd: ** Ignoring requests on eth0.  If this is not what
Oct 30 19:09:07 mafia dhcpd:    you want, please write a subnet declaration
Oct 30 19:09:07 mafia dhcpd:    in your dhcpd.conf file for the network segment
Oct 30 19:09:07 mafia dhcpd:    to which interface eth0 is attached. **
Oct 30 19:09:07 mafia dhcpd: 
Oct 30 19:09:07 mafia dhcpd: 
Oct 30 19:09:07 mafia dhcpd: Not configured to listen on any interfaces!
Oct 30 19:09:07 mafia dnsmasq[1624]: compile time options: IPv6 GNU-getopt DBus I18N DHCP TFTP IDN
Oct 30 19:09:07 mafia dnsmasq-dhcp[1624]: DHCP, IP range 10.42.43.10 -- 10.42.43.100, lease time 1h
Oct 30 19:09:12 mafia NetworkManager[745]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct 30 19:09:12 mafia dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct 30 19:09:12 mafia dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 19:09:12 mafia dhclient: /var/lib/dhcp/dhclient-5ba6801d-1c98-456e-86fc-512fee3e7a90-wlan0.lease line 12: semicolon expected.
Oct 30 19:09:12 mafia dhclient: /var/lib/dhcp/dhclient-5ba6801d-1c98-456e-86fc-512fee3e7a90-wlan0.lease line 14: semicolon expected.
Oct 30 19:09:12 mafia dhclient: /var/lib/dhcp/dhclient-5ba6801d-1c98-456e-86fc-512fee3e7a90-wlan0.lease line 14: unterminated lease declaration.
Oct 30 19:09:12 mafia NetworkManager[745]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Oct 30 19:09:12 mafia dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 30 19:09:12 mafia dhclient: DHCPOFFER of 192.168.2.2 from 192.168.2.1
Oct 30 19:09:12 mafia dhclient: DHCPREQUEST of 192.168.2.2 on wlan0 to 255.255.255.255 port 67
Oct 30 19:09:12 mafia dhclient: DHCPACK of 192.168.2.2 from 192.168.2.1
Oct 30 19:09:12 mafia NetworkManager[745]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Oct 30 19:09:14 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 19:09:14 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 19:09:14 mafia dhcpd: All rights reserved.
Oct 30 19:09:14 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 19:09:16 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 19:09:16 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 19:09:16 mafia dhcpd: All rights reserved.
Oct 30 19:09:16 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 19:09:16 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 19:09:16 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 19:09:16 mafia dhcpd: All rights reserved.
Oct 30 19:09:16 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 19:09:16 mafia dhcpd: Wrote 0 leases to leases file.
Oct 30 19:09:16 mafia dhcpd: 
Oct 30 19:09:16 mafia dhcpd: No subnet declaration for eth1 (no IPv4 addresses).
Oct 30 19:09:16 mafia dhcpd: ** Ignoring requests on eth1.  If this is not what
Oct 30 19:09:16 mafia dhcpd:    you want, please write a subnet declaration
Oct 30 19:09:16 mafia dhcpd:    in your dhcpd.conf file for the network segment
Oct 30 19:09:16 mafia dhcpd:    to which interface eth1 is attached. **
Oct 30 19:09:16 mafia dhcpd: 
Oct 30 19:09:16 mafia dhcpd: 
Oct 30 19:09:16 mafia dhcpd: No subnet declaration for eth0 (10.42.43.1).
Oct 30 19:09:16 mafia dhcpd: ** Ignoring requests on eth0.  If this is not what
Oct 30 19:09:16 mafia dhcpd:    you want, please write a subnet declaration
Oct 30 19:09:16 mafia dhcpd:    in your dhcpd.conf file for the network segment
Oct 30 19:09:16 mafia dhcpd:    to which interface eth0 is attached. **
Oct 30 19:09:16 mafia dhcpd: 
Oct 30 19:09:16 mafia dhcpd: 
Oct 30 19:09:16 mafia dhcpd: Not configured to listen on any interfaces!
Oct 30 19:13:24 mafia dnsmasq[2842]: compile time options: IPv6 GNU-getopt DBus I18N DHCP TFTP IDN
Oct 30 19:13:24 mafia dnsmasq-dhcp[2842]: DHCP, IP range 10.42.43.10 -- 10.42.43.100, lease time 1h
Oct 30 19:13:24 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 19:13:24 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 19:13:24 mafia dhcpd: All rights reserved.
Oct 30 19:13:24 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 19:13:26 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 19:13:26 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 19:13:26 mafia dhcpd: All rights reserved.
Oct 30 19:13:26 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 19:13:26 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 19:13:26 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 19:13:26 mafia dhcpd: All rights reserved.
Oct 30 19:13:26 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 19:13:26 mafia dhcpd: Wrote 0 leases to leases file.
Oct 30 19:13:26 mafia dhcpd: 
Oct 30 19:13:26 mafia dhcpd: No subnet declaration for eth1 (no IPv4 addresses).
Oct 30 19:13:26 mafia dhcpd: ** Ignoring requests on eth1.  If this is not what
Oct 30 19:13:26 mafia dhcpd:    you want, please write a subnet declaration
Oct 30 19:13:26 mafia dhcpd:    in your dhcpd.conf file for the network segment
Oct 30 19:13:26 mafia dhcpd:    to which interface eth1 is attached. **
Oct 30 19:13:26 mafia dhcpd: 
Oct 30 19:13:26 mafia dhcpd: 
Oct 30 19:13:26 mafia dhcpd: No subnet declaration for eth0 (10.42.43.1).
Oct 30 19:13:26 mafia dhcpd: ** Ignoring requests on eth0.  If this is not what
Oct 30 19:13:26 mafia dhcpd:    you want, please write a subnet declaration
Oct 30 19:13:26 mafia dhcpd:    in your dhcpd.conf file for the network segment
Oct 30 19:13:26 mafia dhcpd:    to which interface eth0 is attached. **
Oct 30 19:13:26 mafia dhcpd: 
Oct 30 19:13:26 mafia dhcpd: 
Oct 30 19:13:26 mafia dhcpd: Not configured to listen on any interfaces!
Oct 30 22:02:00 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 22:02:00 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 22:02:00 mafia dhcpd: All rights reserved.
Oct 30 22:02:00 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 22:02:02 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 22:02:02 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 22:02:02 mafia dhcpd: All rights reserved.
Oct 30 22:02:02 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 22:02:02 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 22:02:02 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 22:02:02 mafia dhcpd: All rights reserved.
Oct 30 22:02:02 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 22:02:02 mafia dhcpd: Wrote 0 leases to leases file.
Oct 30 22:02:02 mafia dhcpd: 
Oct 30 22:02:02 mafia dhcpd: No subnet declaration for eth1 (no IPv4 addresses).
Oct 30 22:02:02 mafia dhcpd: ** Ignoring requests on eth1.  If this is not what
Oct 30 22:02:02 mafia dhcpd:    you want, please write a subnet declaration
Oct 30 22:02:02 mafia dhcpd:    in your dhcpd.conf file for the network segment
Oct 30 22:02:02 mafia dhcpd:    to which interface eth1 is attached. **
Oct 30 22:02:02 mafia dhcpd: 
Oct 30 22:02:02 mafia dhcpd: 
Oct 30 22:02:02 mafia dhcpd: No subnet declaration for eth0 (10.0.0.1).
Oct 30 22:02:02 mafia dhcpd: ** Ignoring requests on eth0.  If this is not what
Oct 30 22:02:02 mafia dhcpd:    you want, please write a subnet declaration
Oct 30 22:02:02 mafia dhcpd:    in your dhcpd.conf file for the network segment
Oct 30 22:02:02 mafia dhcpd:    to which interface eth0 is attached. **
Oct 30 22:02:02 mafia dhcpd: 
Oct 30 22:02:02 mafia dhcpd: 
Oct 30 22:02:02 mafia dhcpd: Not configured to listen on any interfaces!
Oct 30 22:02:13 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 22:02:13 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 22:02:13 mafia dhcpd: All rights reserved.
Oct 30 22:02:13 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 22:02:15 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 22:02:15 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 22:02:15 mafia dhcpd: All rights reserved.
Oct 30 22:02:15 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 22:02:15 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 22:02:15 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 22:02:15 mafia dhcpd: All rights reserved.
Oct 30 22:02:15 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 22:02:15 mafia dhcpd: Wrote 0 leases to leases file.
Oct 30 22:02:15 mafia dhcpd: 
Oct 30 22:02:15 mafia dhcpd: No subnet declaration for eth1 (no IPv4 addresses).
Oct 30 22:02:15 mafia dhcpd: ** Ignoring requests on eth1.  If this is not what
Oct 30 22:02:15 mafia dhcpd:    you want, please write a subnet declaration
Oct 30 22:02:15 mafia dhcpd:    in your dhcpd.conf file for the network segment
Oct 30 22:02:15 mafia dhcpd:    to which interface eth1 is attached. **
Oct 30 22:02:15 mafia dhcpd: 
Oct 30 22:02:15 mafia dhcpd: 
Oct 30 22:02:15 mafia dhcpd: No subnet declaration for eth0 (10.0.0.1).
Oct 30 22:02:15 mafia dhcpd: ** Ignoring requests on eth0.  If this is not what
Oct 30 22:02:15 mafia dhcpd:    you want, please write a subnet declaration
Oct 30 22:02:15 mafia dhcpd:    in your dhcpd.conf file for the network segment
Oct 30 22:02:15 mafia dhcpd:    to which interface eth0 is attached. **
Oct 30 22:02:15 mafia dhcpd: 
Oct 30 22:02:15 mafia dhcpd: 
Oct 30 22:02:15 mafia dhcpd: Not configured to listen on any interfaces!
Oct 30 22:04:17 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 22:04:17 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 22:04:17 mafia dhcpd: All rights reserved.
Oct 30 22:04:17 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 22:04:19 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 22:04:19 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 22:04:19 mafia dhcpd: All rights reserved.
Oct 30 22:04:19 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 22:04:19 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 22:04:19 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 22:04:19 mafia dhcpd: All rights reserved.
Oct 30 22:04:19 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 22:04:19 mafia dhcpd: Wrote 0 leases to leases file.
Oct 30 22:04:19 mafia dhcpd: 
Oct 30 22:04:19 mafia dhcpd: No subnet declaration for eth1 (no IPv4 addresses).
Oct 30 22:04:19 mafia dhcpd: ** Ignoring requests on eth1.  If this is not what
Oct 30 22:04:19 mafia dhcpd:    you want, please write a subnet declaration
Oct 30 22:04:19 mafia dhcpd:    in your dhcpd.conf file for the network segment
Oct 30 22:04:19 mafia dhcpd:    to which interface eth1 is attached. **
Oct 30 22:04:19 mafia dhcpd: 
Oct 30 22:04:19 mafia dhcpd: 
Oct 30 22:04:19 mafia dhcpd: No subnet declaration for eth0 (10.0.0.1).
Oct 30 22:04:19 mafia dhcpd: ** Ignoring requests on eth0.  If this is not what
Oct 30 22:04:19 mafia dhcpd:    you want, please write a subnet declaration
Oct 30 22:04:19 mafia dhcpd:    in your dhcpd.conf file for the network segment
Oct 30 22:04:19 mafia dhcpd:    to which interface eth0 is attached. **
Oct 30 22:04:19 mafia dhcpd: 
Oct 30 22:04:19 mafia dhcpd: 
Oct 30 22:04:19 mafia dhcpd: Not configured to listen on any interfaces!
Oct 30 22:04:30 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 22:04:30 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 22:04:30 mafia dhcpd: All rights reserved.
Oct 30 22:04:30 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 22:04:32 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 22:04:32 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 22:04:32 mafia dhcpd: All rights reserved.
Oct 30 22:04:32 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 22:04:32 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 22:04:32 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 22:04:32 mafia dhcpd: All rights reserved.
Oct 30 22:04:32 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 22:04:32 mafia dhcpd: Wrote 0 leases to leases file.
Oct 30 22:04:32 mafia dhcpd: 
Oct 30 22:04:32 mafia dhcpd: No subnet declaration for eth1 (no IPv4 addresses).
Oct 30 22:04:32 mafia dhcpd: ** Ignoring requests on eth1.  If this is not what
Oct 30 22:04:32 mafia dhcpd:    you want, please write a subnet declaration
Oct 30 22:04:32 mafia dhcpd:    in your dhcpd.conf file for the network segment
Oct 30 22:04:32 mafia dhcpd:    to which interface eth1 is attached. **
Oct 30 22:04:32 mafia dhcpd: 
Oct 30 22:04:32 mafia dhcpd: 
Oct 30 22:04:32 mafia dhcpd: No subnet declaration for eth0 (10.0.0.1).
Oct 30 22:04:32 mafia dhcpd: ** Ignoring requests on eth0.  If this is not what
Oct 30 22:04:32 mafia dhcpd:    you want, please write a subnet declaration
Oct 30 22:04:32 mafia dhcpd:    in your dhcpd.conf file for the network segment
Oct 30 22:04:32 mafia dhcpd:    to which interface eth0 is attached. **
Oct 30 22:04:32 mafia dhcpd: 
Oct 30 22:04:32 mafia dhcpd: 
Oct 30 22:04:32 mafia dhcpd: Not configured to listen on any interfaces!
Oct 30 23:14:08 mafia NetworkManager[745]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 2216
Oct 30 23:14:11 mafia NetworkManager[745]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct 30 23:14:11 mafia dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct 30 23:14:11 mafia dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 23:14:11 mafia dhclient: /var/lib/dhcp/dhclient-5ba6801d-1c98-456e-86fc-512fee3e7a90-wlan0.lease line 12: semicolon expected.
Oct 30 23:14:11 mafia dhclient: /var/lib/dhcp/dhclient-5ba6801d-1c98-456e-86fc-512fee3e7a90-wlan0.lease line 14: semicolon expected.
Oct 30 23:14:11 mafia dhclient: /var/lib/dhcp/dhclient-5ba6801d-1c98-456e-86fc-512fee3e7a90-wlan0.lease line 14: unterminated lease declaration.
Oct 30 23:14:11 mafia NetworkManager[745]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Oct 30 23:14:11 mafia dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 30 23:14:11 mafia dhclient: DHCPOFFER of 192.168.2.4 from 192.168.2.1
Oct 30 23:14:11 mafia dhclient: DHCPREQUEST of 192.168.2.4 on wlan0 to 255.255.255.255 port 67
Oct 30 23:14:13 mafia dhclient: DHCPREQUEST of 192.168.2.4 on wlan0 to 255.255.255.255 port 67
Oct 30 23:14:14 mafia dhclient: DHCPACK of 192.168.2.4 from 192.168.2.1
Oct 30 23:14:14 mafia NetworkManager[745]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Oct 30 23:14:15 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 23:14:15 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 23:14:15 mafia dhcpd: All rights reserved.
Oct 30 23:14:15 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 23:14:17 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 23:14:17 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 23:14:17 mafia dhcpd: All rights reserved.
Oct 30 23:14:17 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 23:14:18 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 23:14:18 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 23:14:18 mafia dhcpd: All rights reserved.
Oct 30 23:14:18 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 23:14:18 mafia dhcpd: Wrote 0 leases to leases file.
Oct 30 23:14:18 mafia dhcpd: 
Oct 30 23:14:18 mafia dhcpd: No subnet declaration for eth1 (no IPv4 addresses).
Oct 30 23:14:18 mafia dhcpd: ** Ignoring requests on eth1.  If this is not what
Oct 30 23:14:18 mafia dhcpd:    you want, please write a subnet declaration
Oct 30 23:14:18 mafia dhcpd:    in your dhcpd.conf file for the network segment
Oct 30 23:14:18 mafia dhcpd:    to which interface eth1 is attached. **
Oct 30 23:14:18 mafia dhcpd: 
Oct 30 23:14:18 mafia dhcpd: 
Oct 30 23:14:18 mafia dhcpd: No subnet declaration for eth0 (10.0.0.1).
Oct 30 23:14:18 mafia dhcpd: ** Ignoring requests on eth0.  If this is not what
Oct 30 23:14:18 mafia dhcpd:    you want, please write a subnet declaration
Oct 30 23:14:18 mafia dhcpd:    in your dhcpd.conf file for the network segment
Oct 30 23:14:18 mafia dhcpd:    to which interface eth0 is attached. **
Oct 30 23:14:18 mafia dhcpd: 
Oct 30 23:14:18 mafia dhcpd: 
Oct 30 23:14:18 mafia dhcpd: Not configured to listen on any interfaces!
Oct 30 23:15:39 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 23:15:39 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 23:15:39 mafia dhcpd: All rights reserved.
Oct 30 23:15:39 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 23:15:41 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 23:15:41 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 23:15:41 mafia dhcpd: All rights reserved.
Oct 30 23:15:41 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 23:15:41 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 23:15:41 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 23:15:41 mafia dhcpd: All rights reserved.
Oct 30 23:15:41 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 23:15:41 mafia dhcpd: Wrote 0 leases to leases file.
Oct 30 23:15:41 mafia dhcpd: 
Oct 30 23:15:41 mafia dhcpd: No subnet declaration for eth1 (no IPv4 addresses).
Oct 30 23:15:41 mafia dhcpd: ** Ignoring requests on eth1.  If this is not what
Oct 30 23:15:41 mafia dhcpd:    you want, please write a subnet declaration
Oct 30 23:15:41 mafia dhcpd:    in your dhcpd.conf file for the network segment
Oct 30 23:15:41 mafia dhcpd:    to which interface eth1 is attached. **
Oct 30 23:15:41 mafia dhcpd: 
Oct 30 23:15:41 mafia dhcpd: 
Oct 30 23:15:41 mafia dhcpd: No subnet declaration for eth0 (10.0.0.1).
Oct 30 23:15:41 mafia dhcpd: ** Ignoring requests on eth0.  If this is not what
Oct 30 23:15:41 mafia dhcpd:    you want, please write a subnet declaration
Oct 30 23:15:41 mafia dhcpd:    in your dhcpd.conf file for the network segment
Oct 30 23:15:41 mafia dhcpd:    to which interface eth0 is attached. **
Oct 30 23:15:41 mafia dhcpd: 
Oct 30 23:15:41 mafia dhcpd: 
Oct 30 23:15:41 mafia dhcpd: Not configured to listen on any interfaces!
Oct 30 23:18:35 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 23:18:35 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 23:18:35 mafia dhcpd: All rights reserved.
Oct 30 23:18:35 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 23:18:37 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 23:18:37 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 23:18:37 mafia dhcpd: All rights reserved.
Oct 30 23:18:37 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 23:18:37 mafia dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct 30 23:18:37 mafia dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct 30 23:18:37 mafia dhcpd: All rights reserved.
Oct 30 23:18:37 mafia dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct 30 23:18:37 mafia dhcpd: Wrote 0 leases to leases file.
Oct 30 23:18:37 mafia dhcpd: 
Oct 30 23:18:37 mafia dhcpd: No subnet declaration for eth1 (no IPv4 addresses).
Oct 30 23:18:37 mafia dhcpd: ** Ignoring requests on eth1.  If this is not what
Oct 30 23:18:37 mafia dhcpd:    you want, please write a subnet declaration
Oct 30 23:18:37 mafia dhcpd:    in your dhcpd.conf file for the network segment
Oct 30 23:18:37 mafia dhcpd:    to which interface eth1 is attached. **
Oct 30 23:18:37 mafia dhcpd: 
Oct 30 23:18:37 mafia dhcpd: 
Oct 30 23:18:37 mafia dhcpd: No subnet declaration for eth0 (10.0.0.1).
Oct 30 23:18:37 mafia dhcpd: ** Ignoring requests on eth0.  If this is not what
Oct 30 23:18:37 mafia dhcpd:    you want, please write a subnet declaration
Oct 30 23:18:37 mafia dhcpd:    in your dhcpd.conf file for the network segment
Oct 30 23:18:37 mafia dhcpd:    to which interface eth0 is attached. **
Oct 30 23:18:37 mafia dhcpd: 
Oct 30 23:18:37 mafia dhcpd: 
Oct 30 23:18:37 mafia dhcpd: Not configured to listen on any interfaces!
tamps@mafia:~$ [/PHP][PHP]tamps@mafia:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:27:13:68:05:75  
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::227:13ff:fe68:575/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:90899 errors:0 dropped:0 overruns:0 frame:0
          TX packets:546478 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7431459 (7.4 MB)  TX bytes:808620855 (808.6 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64795 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64795 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7753205 (7.7 MB)  TX bytes:7753205 (7.7 MB)

wlan0     Link encap:Ethernet  HWaddr 00:26:c6:82:b7:4a  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::226:c6ff:fe82:b74a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:596843 errors:0 dropped:0 overruns:0 frame:0
          TX packets:852973 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:151463835 (151.4 MB)  TX bytes:824938495 (824.9 MB)

tamps@mafia:~$[/PHP]

---

### Post by mafi127 on 2011-10-31
some1?

---

### Post by mafi127 on 2011-10-31
I think I have problem whit my dhcp, here is the output

[PHP]tamps@mafia:/etc/default$ sudo /etc/init.d/isc-dhcp-server start
 * Starting ISC DHCP server dhcpd                                                                                                            * check syslog for diagnostics.
                                                                                                                                     [fail]
tamps@mafia:/etc/default$ tail /var/log/syslog
Oct 31 20:29:04 mafia dhcpd: ** Ignoring requests on eth0.  If this is not what
Oct 31 20:29:04 mafia dhcpd:    you want, please write a subnet declaration
Oct 31 20:29:04 mafia dhcpd:    in your dhcpd.conf file for the network segment
Oct 31 20:29:04 mafia dhcpd:    to which interface eth0 is attached. **
Oct 31 20:29:04 mafia dhcpd: 
Oct 31 20:29:04 mafia dhcpd: 
Oct 31 20:29:04 mafia dhcpd: Not configured to listen on any interfaces!
Oct 31 20:29:15 mafia kernel: [91233.138721] Inbound IN=wlan0 OUT= MAC= SRC=192.168.2.4 DST=255.255.255.255 LEN=139 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=17500 DPT=17500 LEN=119 
Oct 31 20:29:15 mafia kernel: [91233.139030] Inbound IN=eth0 OUT= MAC= SRC=10.42.43.1 DST=10.42.43.255 LEN=139 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=17500 DPT=17500 LEN=119 
Oct 31 20:29:15 mafia kernel: [91233.139140] Inbound IN=wlan0 OUT= MAC= SRC=192.168.2.4 DST=192.168.2.255 LEN=139 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=17500 DPT=17500 LEN=119 
tamps@mafia:/etc/default$ 
[/PHP]

My /etc/dhcp/dhcpd.conf file is 

[PHP]#/etc/dhcp3/dhcpd.conf
option subnet-mask 255.255.255.0;
default-lease-time 600;
max-lease-time 7200;

subnet 192.168.27.0 netmask 255.255.255.0 {
  range 192.168.27.10 192.168.27.20;
  option broadcast-address 192.168.27.255;
  option routers 192.168.27.1;
}[/PHP]

---

### Post by mafi127 on 2011-11-01
some1?:confused:

---

