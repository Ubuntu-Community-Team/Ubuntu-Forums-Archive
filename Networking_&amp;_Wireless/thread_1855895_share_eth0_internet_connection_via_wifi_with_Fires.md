---
title: "share eth0 internet connection via wifi with Firestarter"
date: 2011-10-07
forum: Networking &amp; Wireless
---

### Post by CryptKeeper777 on 2011-10-07
I've been trying to share my ethernet internet connection with my Android phone via wifi, i.e. setting up a wifi network "fed" by my eth0 connection. I've tormented google and myself with this problem for days now without any result. Now I found this guide ([http://ubuntuforums.org/showthread.php?t=1655454](http://ubuntuforums.org/showthread.php?t=1655454) post #4) and tried it out. I started Firestarter, clicked [Forward], chose "Ethernet device (eth0)" and clicked [Forward] again. Now I'm asked for the "Local area network device", that would be the wifi device, I suppose. But the only detected devices are eth0 and eth1. Wifi works perfectly fine though, I have no problems connecting to existing wifi networks.

My setup: Ubuntu 11.04 (freshly reinstalled some days ago) on a MacBook4 (dualboot). BTW: Under OS X, internet sharing works perfectly fine, so I have at least all the hardware needed...

In the other thread, the thread starter got asked to post the output to following commands:
```

ifconfig -a 
cat /etc/dhcp3/dhcpd.conf 
sudo ufw show raw 
sudo grep -i dhcp /var/log/syslog

```Here's my output to them (I suppose that could be useful for you to help me):
```

> ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:22:41:3c:f2:c1  
          inet addr:213.196.161.226  Bcast:213.196.161.255  Mask:255.255.255.0
          inet6 addr: fe80::222:41ff:fe3c:f2c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:132105 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98426 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:120999306 (120.9 MB)  TX bytes:11630325 (11.6 MB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:23:12:05:20:a0  
          inet6 addr: fe80::223:12ff:fe05:20a0/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:205996 errors:0 dropped:0 overruns:0 frame:243473
          TX packets:73427 errors:854 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:124307603 (124.3 MB)  TX bytes:13788954 (13.7 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:63310 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63310 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10540855 (10.5 MB)  TX bytes:10540855 (10.5 MB)


> cat /etc/dhcp3/dhcpd.conf
cat: /etc/dhcp3/dhcpd.conf: No such file or directory

> sudo ufw show raw
IPV4 (raw):
Chain INPUT (policy ACCEPT 18968 packets, 18668621 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 18649 packets, 1808053 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
Chain PREROUTING (policy ACCEPT 227 packets, 11404 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain INPUT (policy ACCEPT 227 packets, 11404 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 747 packets, 47735 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 747 packets, 47735 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
Chain PREROUTING (policy ACCEPT 18968 packets, 18668621 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain INPUT (policy ACCEPT 18968 packets, 18668621 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 18649 packets, 1808053 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 18710 packets, 1816960 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
Chain PREROUTING (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         


IPV6:
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
Chain PREROUTING (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
Chain PREROUTING (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         


> sudo grep -i dhcp /var/log/syslog
Oct  5 12:31:15 ubuntuMB kernel: [    7.111915] type=1400 audit(1317810671.629:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=480 comm="apparmor_parser"
Oct  5 12:31:15 ubuntuMB kernel: [    7.111940] type=1400 audit(1317810671.629:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=460 comm="apparmor_parser"
Oct  5 12:31:19 ubuntuMB kernel: [   15.163767] type=1400 audit(1317810679.681:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=825 comm="apparmor_parser"
Oct  5 12:31:24 ubuntuMB NetworkManager[839]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  5 12:31:24 ubuntuMB dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct  5 12:31:24 ubuntuMB dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  5 12:31:24 ubuntuMB NetworkManager[839]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Oct  5 12:31:24 ubuntuMB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Oct  5 12:31:24 ubuntuMB dhclient: DHCPOFFER of 192.168.7.2 from 192.168.7.1
Oct  5 12:31:24 ubuntuMB dhclient: DHCPREQUEST of 192.168.7.2 on eth0 to 255.255.255.255 port 67
Oct  5 12:31:24 ubuntuMB dhclient: DHCPACK of 192.168.7.2 from 192.168.7.1
Oct  5 12:31:24 ubuntuMB NetworkManager[839]: <info> (eth0): DHCPv4 state changed preinit -> bound
Oct  5 12:37:12 ubuntuMB NetworkManager[839]: <info> (eth0): canceled DHCP transaction, DHCP client pid 1036
Oct  5 13:00:43 ubuntuMB NetworkManager[839]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  5 13:00:43 ubuntuMB dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct  5 13:00:43 ubuntuMB dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  5 13:00:43 ubuntuMB NetworkManager[839]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Oct  5 13:00:43 ubuntuMB dhclient: DHCPREQUEST of 192.168.7.2 on eth0 to 255.255.255.255 port 67
Oct  5 13:00:43 ubuntuMB dhclient: DHCPACK of 192.168.7.2 from 192.168.7.1
Oct  5 13:00:43 ubuntuMB NetworkManager[839]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Oct  5 13:18:41 ubuntuMB NetworkManager[839]: <info> (eth0): canceled DHCP transaction, DHCP client pid 2333
Oct  5 13:20:58 ubuntuMB NetworkManager[839]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  5 13:20:58 ubuntuMB dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct  5 13:20:58 ubuntuMB dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  5 13:20:58 ubuntuMB NetworkManager[839]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Oct  5 13:20:58 ubuntuMB dhclient: DHCPREQUEST of 192.168.7.2 on eth0 to 255.255.255.255 port 67
Oct  5 13:20:58 ubuntuMB dhclient: DHCPACK of 192.168.7.2 from 192.168.7.1
Oct  5 13:20:58 ubuntuMB NetworkManager[839]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Oct  5 15:40:06 ubuntuMB kernel: [   11.507147] type=1400 audit(1317822006.031:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=491 comm="apparmor_parser"
Oct  5 15:40:06 ubuntuMB kernel: [   11.813075] type=1400 audit(1317822006.339:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=671 comm="apparmor_parser"
Oct  5 15:40:08 ubuntuMB NetworkManager[653]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  5 15:40:08 ubuntuMB dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct  5 15:40:08 ubuntuMB dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  5 15:40:08 ubuntuMB NetworkManager[653]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Oct  5 15:40:08 ubuntuMB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Oct  5 15:40:08 ubuntuMB dhclient: DHCPOFFER of 192.168.7.2 from 192.168.7.1
Oct  5 15:40:08 ubuntuMB dhclient: DHCPREQUEST of 192.168.7.2 on eth0 to 255.255.255.255 port 67
Oct  5 15:40:08 ubuntuMB dhclient: DHCPACK of 192.168.7.2 from 192.168.7.1
Oct  5 15:40:08 ubuntuMB NetworkManager[653]: <info> (eth0): DHCPv4 state changed preinit -> bound
Oct  5 16:32:16 ubuntuMB kernel: [ 3141.556844] type=1400 audit(1317825136.675:22): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=19763 comm="apparmor_parser"
Oct  5 16:48:41 ubuntuMB kernel: [   13.288595] type=1400 audit(1317826121.812:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=519 comm="apparmor_parser"
Oct  5 16:48:41 ubuntuMB kernel: [   13.288654] type=1400 audit(1317826121.812:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=532 comm="apparmor_parser"
Oct  5 16:48:51 ubuntuMB kernel: [   22.723093] type=1400 audit(1317826131.244:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=870 comm="apparmor_parser"
Oct  5 16:48:51 ubuntuMB NetworkManager[776]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  5 16:48:52 ubuntuMB dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct  5 16:48:52 ubuntuMB dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  5 16:48:53 ubuntuMB NetworkManager[776]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Oct  5 16:48:53 ubuntuMB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Oct  5 16:48:53 ubuntuMB dhclient: DHCPOFFER of 192.168.7.2 from 192.168.7.1
Oct  5 16:48:53 ubuntuMB dhclient: DHCPREQUEST of 192.168.7.2 on eth0 to 255.255.255.255 port 67
Oct  5 16:48:53 ubuntuMB dhclient: DHCPACK of 192.168.7.2 from 192.168.7.1
Oct  5 16:48:53 ubuntuMB NetworkManager[776]: <info> (eth0): DHCPv4 state changed preinit -> bound
Oct  5 18:41:15 ubuntuMB dnsmasq[4858]: compile time options: IPv6 GNU-getopt DBus I18N DHCP TFTP IDN
Oct  5 18:43:39 ubuntuMB kernel: [    6.585622] type=1400 audit(1317833016.103:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=423 comm="apparmor_parser"
Oct  5 18:43:39 ubuntuMB kernel: [    6.587656] type=1400 audit(1317833016.103:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=440 comm="apparmor_parser"
Oct  5 18:43:45 ubuntuMB kernel: [   16.310267] type=1400 audit(1317833025.827:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=772 comm="apparmor_parser"
Oct  5 18:43:49 ubuntuMB NetworkManager[843]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  5 18:43:49 ubuntuMB dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct  5 18:43:49 ubuntuMB dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  5 18:43:49 ubuntuMB NetworkManager[843]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Oct  5 18:43:49 ubuntuMB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Oct  5 18:43:49 ubuntuMB dhclient: DHCPOFFER of 192.168.7.2 from 192.168.7.1
Oct  5 18:43:49 ubuntuMB dhclient: DHCPREQUEST of 192.168.7.2 on eth0 to 255.255.255.255 port 67
Oct  5 18:43:51 ubuntuMB dnsmasq[968]: compile time options: IPv6 GNU-getopt DBus I18N DHCP TFTP IDN
Oct  5 18:43:52 ubuntuMB dhclient: DHCPREQUEST of 192.168.7.2 on eth0 to 255.255.255.255 port 67
Oct  5 18:43:52 ubuntuMB dhclient: DHCPACK of 192.168.7.2 from 192.168.7.1
Oct  5 18:43:52 ubuntuMB NetworkManager[843]: <info> (eth0): DHCPv4 state changed preinit -> bound
Oct  5 19:18:20 ubuntuMB NetworkManager[843]: <info> (eth0): canceled DHCP transaction, DHCP client pid 884
Oct  5 20:54:17 ubuntuMB NetworkManager[843]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  5 20:54:17 ubuntuMB dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct  5 20:54:17 ubuntuMB dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  5 20:54:17 ubuntuMB NetworkManager[843]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Oct  5 20:54:17 ubuntuMB dhclient: DHCPREQUEST of 192.168.7.2 on eth0 to 255.255.255.255 port 67
Oct  5 20:54:20 ubuntuMB dhclient: DHCPREQUEST of 192.168.7.2 on eth0 to 255.255.255.255 port 67
Oct  5 20:54:20 ubuntuMB dhclient: DHCPACK of 192.168.7.2 from 192.168.7.1
Oct  5 20:54:20 ubuntuMB NetworkManager[843]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Oct  5 20:58:36 ubuntuMB NetworkManager[843]: <info> (eth0): canceled DHCP transaction, DHCP client pid 3075
Oct  5 20:58:39 ubuntuMB NetworkManager[843]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  5 20:58:39 ubuntuMB dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct  5 20:58:39 ubuntuMB dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  5 20:58:39 ubuntuMB NetworkManager[843]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Oct  5 20:58:39 ubuntuMB dhclient: DHCPREQUEST of 192.168.7.2 on eth0 to 255.255.255.255 port 67
Oct  5 20:58:42 ubuntuMB dhclient: DHCPREQUEST of 192.168.7.2 on eth0 to 255.255.255.255 port 67
Oct  5 20:58:50 ubuntuMB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Oct  5 20:58:50 ubuntuMB dhclient: DHCPOFFER of 192.168.7.2 from 192.168.7.1
Oct  5 20:58:50 ubuntuMB dhclient: DHCPREQUEST of 192.168.7.2 on eth0 to 255.255.255.255 port 67
Oct  5 20:58:50 ubuntuMB dhclient: DHCPACK of 192.168.7.2 from 192.168.7.1
Oct  5 20:58:50 ubuntuMB NetworkManager[843]: <info> (eth0): DHCPv4 state changed preinit -> bound
Oct  5 21:17:24 ubuntuMB NetworkManager[843]: <info> (eth0): canceled DHCP transaction, DHCP client pid 3373
Oct  5 21:17:54 ubuntuMB NetworkManager[843]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  5 21:17:54 ubuntuMB dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct  5 21:17:54 ubuntuMB dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  5 21:17:54 ubuntuMB NetworkManager[843]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Oct  5 21:17:54 ubuntuMB dhclient: DHCPREQUEST of 192.168.7.2 on eth0 to 255.255.255.255 port 67
Oct  5 21:17:54 ubuntuMB dhclient: DHCPACK of 192.168.7.2 from 192.168.7.1
Oct  5 21:17:54 ubuntuMB NetworkManager[843]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Oct  5 21:23:50 ubuntuMB NetworkManager[843]: <info> (eth0): canceled DHCP transaction, DHCP client pid 5019
Oct  5 21:26:33 ubuntuMB NetworkManager[843]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  5 21:26:33 ubuntuMB dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct  5 21:26:33 ubuntuMB dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  5 21:26:33 ubuntuMB NetworkManager[843]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Oct  5 21:26:33 ubuntuMB dhclient: DHCPREQUEST of 192.168.7.2 on eth0 to 255.255.255.255 port 67
Oct  5 21:26:33 ubuntuMB dhclient: DHCPACK of 192.168.7.2 from 192.168.7.1
Oct  5 21:26:33 ubuntuMB NetworkManager[843]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Oct  5 22:58:21 ubuntuMB NetworkManager[843]: <info> (eth0): canceled DHCP transaction, DHCP client pid 5801
Oct  6 07:15:35 ubuntuMB NetworkManager[843]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  6 07:15:36 ubuntuMB dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct  6 07:15:36 ubuntuMB dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  6 07:15:36 ubuntuMB NetworkManager[843]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Oct  6 07:15:36 ubuntuMB dhclient: DHCPREQUEST of 192.168.7.2 on eth0 to 255.255.255.255 port 67
Oct  6 07:15:36 ubuntuMB dhclient: DHCPACK of 192.168.7.2 from 192.168.7.1
Oct  6 07:15:36 ubuntuMB NetworkManager[843]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Oct  6 07:31:13 ubuntuMB NetworkManager[843]: <info> (eth0): canceled DHCP transaction, DHCP client pid 16079
Oct  6 07:59:21 ubuntuMB NetworkManager[843]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  6 07:59:21 ubuntuMB dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct  6 07:59:21 ubuntuMB dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  6 07:59:21 ubuntuMB NetworkManager[843]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Oct  6 07:59:21 ubuntuMB dhclient: DHCPREQUEST of 192.168.7.2 on eth0 to 255.255.255.255 port 67
Oct  6 07:59:21 ubuntuMB dhclient: DHCPACK of 192.168.7.2 from 192.168.7.1
Oct  6 07:59:21 ubuntuMB NetworkManager[843]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Oct  6 08:01:05 ubuntuMB NetworkManager[843]: <info> (eth0): canceled DHCP transaction, DHCP client pid 24457
Oct  6 08:55:34 ubuntuMB NetworkManager[843]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  6 08:55:34 ubuntuMB dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct  6 08:55:34 ubuntuMB dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  6 08:55:34 ubuntuMB NetworkManager[843]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Oct  6 08:55:34 ubuntuMB dhclient: DHCPREQUEST of 192.168.7.2 on eth0 to 255.255.255.255 port 67
Oct  6 08:55:34 ubuntuMB dhclient: DHCPACK of 192.168.7.2 from 192.168.7.1
Oct  6 08:55:34 ubuntuMB NetworkManager[843]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Oct  6 09:03:31 ubuntuMB NetworkManager[843]: <info> (eth0): canceled DHCP transaction, DHCP client pid 25486
Oct  6 10:09:12 ubuntuMB NetworkManager[843]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  6 10:09:12 ubuntuMB dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct  6 10:09:12 ubuntuMB dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  6 10:09:13 ubuntuMB NetworkManager[843]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Oct  6 10:09:13 ubuntuMB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Oct  6 10:09:15 ubuntuMB dhclient: DHCPOFFER of 10.43.18.114 from 10.43.18.1
Oct  6 10:09:15 ubuntuMB dhclient: DHCPREQUEST of 10.43.18.114 on eth1 to 255.255.255.255 port 67
Oct  6 10:09:15 ubuntuMB dhclient: DHCPACK of 10.43.18.114 from 10.43.18.1
Oct  6 10:09:15 ubuntuMB NetworkManager[843]: <info> (eth1): DHCPv4 state changed preinit -> bound
Oct  6 10:10:30 ubuntuMB dhclient: DHCPREQUEST of 10.43.18.114 on eth1 to 10.43.18.1 port 67
Oct  6 10:10:30 ubuntuMB dhclient: DHCPACK of 10.43.18.114 from 10.43.18.1
Oct  6 10:10:30 ubuntuMB NetworkManager[843]: <info> (eth1): DHCPv4 state changed bound -> renew
Oct  6 10:10:46 ubuntuMB NetworkManager[843]: <info> (eth1): canceled DHCP transaction, DHCP client pid 28510
Oct  6 11:14:33 ubuntuMB NetworkManager[843]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  6 11:14:33 ubuntuMB dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct  6 11:14:33 ubuntuMB dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  6 11:14:33 ubuntuMB NetworkManager[843]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Oct  6 11:14:33 ubuntuMB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Oct  6 11:14:34 ubuntuMB dhclient: DHCPOFFER of 172.30.82.46 from 172.30.80.1
Oct  6 11:14:34 ubuntuMB dhclient: DHCPREQUEST of 172.30.82.46 on eth1 to 255.255.255.255 port 67
Oct  6 11:14:34 ubuntuMB dhclient: DHCPACK of 172.30.82.46 from 172.30.80.1
Oct  6 11:14:34 ubuntuMB NetworkManager[843]: <info> (eth1): DHCPv4 state changed preinit -> bound
Oct  6 11:20:30 ubuntuMB dhclient: DHCPREQUEST of 172.30.82.46 on eth1 to 129.132.128.135 port 67
Oct  6 11:21:46 ubuntuMB dhclient: DHCPREQUEST of 172.30.82.46 on eth1 to 129.132.128.135 port 67
Oct  6 11:21:55 ubuntuMB dhclient: DHCPREQUEST of 172.30.82.46 on eth1 to 129.132.128.135 port 67
Oct  6 11:25:16 ubuntuMB dhclient: DHCPREQUEST of 172.30.82.46 on eth1 to 129.132.128.135 port 67
Oct  6 11:25:31 ubuntuMB NetworkManager[843]: <info> (eth1): canceled DHCP transaction, DHCP client pid 29776
Oct  6 12:25:38 ubuntuMB NetworkManager[843]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  6 12:25:38 ubuntuMB dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct  6 12:25:38 ubuntuMB dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  6 12:25:38 ubuntuMB NetworkManager[843]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Oct  6 12:25:38 ubuntuMB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Oct  6 12:25:39 ubuntuMB dhclient: DHCPOFFER of 172.30.82.46 from 172.30.80.1
Oct  6 12:25:39 ubuntuMB dhclient: DHCPREQUEST of 172.30.82.46 on eth1 to 255.255.255.255 port 67
Oct  6 12:25:39 ubuntuMB dhclient: DHCPACK of 172.30.82.46 from 172.30.80.1
Oct  6 12:25:39 ubuntuMB NetworkManager[843]: <info> (eth1): DHCPv4 state changed preinit -> bound
Oct  6 12:31:44 ubuntuMB dhclient: DHCPREQUEST of 172.30.82.46 on eth1 to 129.132.128.135 port 67
Oct  6 12:32:33 ubuntuMB dhclient: DHCPREQUEST of 172.30.82.46 on eth1 to 129.132.128.135 port 67
Oct  6 12:33:22 ubuntuMB dhclient: DHCPREQUEST of 172.30.82.46 on eth1 to 129.132.128.135 port 67
Oct  6 12:38:19 ubuntuMB dhclient: DHCPREQUEST of 172.30.82.46 on eth1 to 255.255.255.255 port 67
Oct  6 12:38:19 ubuntuMB dhclient: DHCPACK of 172.30.82.46 from 172.30.80.1
Oct  6 12:38:19 ubuntuMB NetworkManager[843]: <info> (eth1): DHCPv4 state changed bound -> renew
Oct  6 12:45:11 ubuntuMB dhclient: DHCPREQUEST of 172.30.82.46 on eth1 to 129.132.128.199 port 67
Oct  6 12:46:33 ubuntuMB dhclient: DHCPREQUEST of 172.30.82.46 on eth1 to 129.132.128.199 port 67
Oct  6 12:46:54 ubuntuMB dhclient: DHCPREQUEST of 172.30.82.46 on eth1 to 129.132.128.199 port 67
Oct  6 12:47:48 ubuntuMB dhclient: DHCPREQUEST of 172.30.82.46 on eth1 to 129.132.128.199 port 67
Oct  6 12:50:02 ubuntuMB dhclient: DHCPREQUEST of 172.30.82.46 on eth1 to 129.132.128.199 port 67
Oct  6 12:50:12 ubuntuMB dhclient: DHCPREQUEST of 172.30.82.46 on eth1 to 129.132.128.199 port 67
Oct  6 12:50:25 ubuntuMB dhclient: DHCPREQUEST of 172.30.82.46 on eth1 to 129.132.128.199 port 67
Oct  6 12:50:45 ubuntuMB dhclient: DHCPREQUEST of 172.30.82.46 on eth1 to 129.132.128.199 port 67
Oct  6 12:51:04 ubuntuMB dhclient: DHCPREQUEST of 172.30.82.46 on eth1 to 255.255.255.255 port 67
Oct  6 12:51:04 ubuntuMB dhclient: DHCPACK of 172.30.82.46 from 172.30.80.1
Oct  6 12:57:26 ubuntuMB dhclient: DHCPREQUEST of 172.30.82.46 on eth1 to 129.132.128.199 port 67
Oct  6 12:58:36 ubuntuMB dhclient: DHCPREQUEST of 172.30.82.46 on eth1 to 129.132.128.199 port 67
Oct  6 12:59:07 ubuntuMB dhclient: DHCPREQUEST of 172.30.82.46 on eth1 to 129.132.128.199 port 67
Oct  6 12:59:07 ubuntuMB dhclient: DHCPACK of 172.30.82.46 from 129.132.128.199
Oct  6 13:05:52 ubuntuMB dhclient: DHCPREQUEST of 172.30.82.46 on eth1 to 129.132.128.199 port 67
Oct  6 13:06:07 ubuntuMB dhclient: DHCPREQUEST of 172.30.82.46 on eth1 to 129.132.128.199 port 67
Oct  6 13:06:22 ubuntuMB dhclient: DHCPREQUEST of 172.30.82.46 on eth1 to 129.132.128.199 port 67
Oct  6 13:06:22 ubuntuMB dhclient: DHCPACK of 172.30.82.46 from 129.132.128.199
Oct  6 13:12:37 ubuntuMB dhclient: DHCPREQUEST of 172.30.82.46 on eth1 to 129.132.128.199 port 67
Oct  6 13:13:50 ubuntuMB dhclient: DHCPREQUEST of 172.30.82.46 on eth1 to 129.132.128.199 port 67
Oct  6 13:14:59 ubuntuMB dhclient: DHCPREQUEST of 172.30.82.46 on eth1 to 129.132.128.199 port 67
Oct  6 13:15:58 ubuntuMB dhclient: DHCPREQUEST of 172.30.82.46 on eth1 to 129.132.128.199 port 67
Oct  6 13:16:37 ubuntuMB NetworkManager[843]: <info> (eth1): canceled DHCP transaction, DHCP client pid 31300
Oct  6 14:56:38 ubuntuMB NetworkManager[843]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  6 14:56:38 ubuntuMB dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct  6 14:56:38 ubuntuMB dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  6 14:56:38 ubuntuMB NetworkManager[843]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Oct  6 14:56:38 ubuntuMB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Oct  6 14:56:39 ubuntuMB dhclient: DHCPOFFER of 172.30.66.67 from 172.30.64.1
Oct  6 14:56:39 ubuntuMB dhclient: DHCPREQUEST of 172.30.66.67 on eth1 to 255.255.255.255 port 67
Oct  6 14:56:39 ubuntuMB dhclient: DHCPACK of 172.30.66.67 from 172.30.64.1
Oct  6 14:56:39 ubuntuMB NetworkManager[843]: <info> (eth1): DHCPv4 state changed preinit -> bound
Oct  6 14:59:15 ubuntuMB NetworkManager[843]: <info> (eth1): canceled DHCP transaction, DHCP client pid 1663
Oct  6 14:59:54 ubuntuMB NetworkManager[843]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  6 14:59:54 ubuntuMB dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct  6 14:59:54 ubuntuMB dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  6 14:59:54 ubuntuMB NetworkManager[843]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Oct  6 14:59:54 ubuntuMB dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Oct  6 14:59:55 ubuntuMB dhclient: DHCPOFFER of 82.130.78.154 from 82.130.78.1
Oct  6 14:59:55 ubuntuMB dhclient: DHCPREQUEST of 82.130.78.154 on eth1 to 255.255.255.255 port 67
Oct  6 14:59:56 ubuntuMB dhclient: DHCPACK of 82.130.78.154 from 82.130.78.1
Oct  6 14:59:56 ubuntuMB NetworkManager[843]: <info> (eth1): DHCPv4 state changed preinit -> bound
Oct  6 14:59:58 ubuntuMB NetworkManager[843]: <info> (eth1): canceled DHCP transaction, DHCP client pid 2146
Oct  6 15:00:32 ubuntuMB NetworkManager[843]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  6 15:00:32 ubuntuMB dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct  6 15:00:32 ubuntuMB dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  6 15:00:32 ubuntuMB NetworkManager[843]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Oct  6 15:00:32 ubuntuMB dhclient: DHCPREQUEST of 172.30.66.67 on eth1 to 255.255.255.255 port 67
Oct  6 15:00:32 ubuntuMB dhclient: DHCPACK of 172.30.66.67 from 172.30.64.1
Oct  6 15:00:32 ubuntuMB NetworkManager[843]: <info> (eth1): DHCPv4 state changed preinit -> reboot
Oct  6 15:02:53 ubuntuMB NetworkManager[843]: <info> (eth1): canceled DHCP transaction, DHCP client pid 2484
Oct  6 15:03:28 ubuntuMB NetworkManager[843]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  6 15:03:28 ubuntuMB dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct  6 15:03:28 ubuntuMB dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  6 15:03:28 ubuntuMB NetworkManager[843]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Oct  6 15:03:28 ubuntuMB dhclient: DHCPREQUEST of 82.130.78.154 on eth1 to 255.255.255.255 port 67
Oct  6 15:03:29 ubuntuMB dhclient: DHCPACK of 82.130.78.154 from 82.130.78.1
Oct  6 15:03:29 ubuntuMB NetworkManager[843]: <info> (eth1): DHCPv4 state changed preinit -> reboot
Oct  6 15:04:28 ubuntuMB NetworkManager[843]: <info> (eth1): canceled DHCP transaction, DHCP client pid 2861
Oct  6 15:05:16 ubuntuMB NetworkManager[843]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  6 15:05:16 ubuntuMB dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct  6 15:05:16 ubuntuMB dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  6 15:05:16 ubuntuMB NetworkManager[843]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Oct  6 15:05:16 ubuntuMB dhclient: DHCPREQUEST of 82.130.78.154 on eth1 to 255.255.255.255 port 67
Oct  6 15:05:16 ubuntuMB dhclient: DHCPACK of 82.130.78.154 from 82.130.78.1
Oct  6 15:05:16 ubuntuMB NetworkManager[843]: <info> (eth1): DHCPv4 state changed preinit -> reboot
Oct  6 15:06:22 ubuntuMB NetworkManager[843]: <info> (eth1): canceled DHCP transaction, DHCP client pid 3262
Oct  6 15:06:56 ubuntuMB NetworkManager[843]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  6 15:06:56 ubuntuMB dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct  6 15:06:56 ubuntuMB dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  6 15:06:56 ubuntuMB NetworkManager[843]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Oct  6 15:06:56 ubuntuMB dhclient: DHCPREQUEST of 172.30.66.67 on eth1 to 255.255.255.255 port 67
Oct  6 15:06:56 ubuntuMB dhclient: DHCPACK of 172.30.66.67 from 172.30.64.1
Oct  6 15:06:56 ubuntuMB NetworkManager[843]: <info> (eth1): DHCPv4 state changed preinit -> reboot
Oct  6 15:07:56 ubuntuMB NetworkManager[843]: <info> (eth1): canceled DHCP transaction, DHCP client pid 3538
Oct  6 15:09:18 ubuntuMB NetworkManager[843]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  6 15:09:18 ubuntuMB dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct  6 15:09:18 ubuntuMB dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  6 15:09:18 ubuntuMB NetworkManager[843]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Oct  6 15:09:18 ubuntuMB dhclient: DHCPREQUEST of 82.130.78.154 on eth1 to 255.255.255.255 port 67
Oct  6 15:09:18 ubuntuMB dhclient: DHCPACK of 82.130.78.154 from 82.130.78.1
Oct  6 15:09:18 ubuntuMB NetworkManager[843]: <info> (eth1): DHCPv4 state changed preinit -> reboot
Oct  6 15:13:49 ubuntuMB dhclient: DHCPREQUEST of 82.130.78.154 on eth1 to 129.132.128.199 port 67
Oct  6 15:13:49 ubuntuMB dhclient: DHCPACK of 82.130.78.154 from 129.132.128.199
Oct  6 15:13:49 ubuntuMB NetworkManager[843]: <info> (eth1): DHCPv4 state changed reboot -> renew
Oct  6 15:18:46 ubuntuMB dhclient: DHCPREQUEST of 82.130.78.154 on eth1 to 129.132.128.199 port 67
Oct  6 15:18:46 ubuntuMB dhclient: DHCPACK of 82.130.78.154 from 129.132.128.199
Oct  6 15:23:04 ubuntuMB dhclient: DHCPREQUEST of 82.130.78.154 on eth1 to 129.132.128.199 port 67
Oct  6 15:23:04 ubuntuMB dhclient: DHCPACK of 82.130.78.154 from 129.132.128.199
Oct  6 15:27:04 ubuntuMB dhclient: DHCPREQUEST of 82.130.78.154 on eth1 to 129.132.128.199 port 67
Oct  6 15:27:04 ubuntuMB dhclient: DHCPACK of 82.130.78.154 from 129.132.128.199
Oct  6 15:30:52 ubuntuMB dhclient: DHCPREQUEST of 82.130.78.154 on eth1 to 129.132.128.199 port 67
Oct  6 15:30:52 ubuntuMB dhclient: DHCPACK of 82.130.78.154 from 129.132.128.199
Oct  6 15:34:54 ubuntuMB dhclient: DHCPREQUEST of 82.130.78.154 on eth1 to 129.132.128.199 port 67
Oct  6 15:34:54 ubuntuMB dhclient: DHCPACK of 82.130.78.154 from 129.132.128.199
Oct  6 15:38:58 ubuntuMB dhclient: DHCPREQUEST of 82.130.78.154 on eth1 to 129.132.128.199 port 67
Oct  6 15:38:58 ubuntuMB dhclient: DHCPACK of 82.130.78.154 from 129.132.128.199
Oct  6 15:43:11 ubuntuMB dhclient: DHCPREQUEST of 82.130.78.154 on eth1 to 129.132.128.199 port 67
Oct  6 15:43:11 ubuntuMB dhclient: DHCPACK of 82.130.78.154 from 129.132.128.199
Oct  6 15:47:55 ubuntuMB dhclient: DHCPREQUEST of 82.130.78.154 on eth1 to 129.132.128.199 port 67
Oct  6 15:47:55 ubuntuMB dhclient: DHCPACK of 82.130.78.154 from 129.132.128.199
Oct  6 15:52:53 ubuntuMB dhclient: DHCPREQUEST of 82.130.78.154 on eth1 to 129.132.128.199 port 67
Oct  6 15:52:53 ubuntuMB dhclient: DHCPACK of 82.130.78.154 from 129.132.128.199
Oct  6 15:57:20 ubuntuMB dhclient: DHCPREQUEST of 82.130.78.154 on eth1 to 129.132.128.199 port 67
Oct  6 15:57:20 ubuntuMB dhclient: DHCPACK of 82.130.78.154 from 129.132.128.199
Oct  6 16:01:23 ubuntuMB dhclient: DHCPREQUEST of 82.130.78.154 on eth1 to 129.132.128.199 port 67
Oct  6 16:01:23 ubuntuMB dhclient: DHCPACK of 82.130.78.154 from 129.132.128.199
Oct  6 16:06:18 ubuntuMB dhclient: DHCPREQUEST of 82.130.78.154 on eth1 to 129.132.128.199 port 67
Oct  6 16:06:18 ubuntuMB dhclient: DHCPACK of 82.130.78.154 from 129.132.128.199
Oct  6 16:10:53 ubuntuMB dhclient: DHCPREQUEST of 82.130.78.154 on eth1 to 129.132.128.199 port 67
Oct  6 16:10:53 ubuntuMB dhclient: DHCPACK of 82.130.78.154 from 129.132.128.199
Oct  6 16:15:42 ubuntuMB dhclient: DHCPREQUEST of 82.130.78.154 on eth1 to 129.132.128.199 port 67
Oct  6 16:15:42 ubuntuMB dhclient: DHCPACK of 82.130.78.154 from 129.132.128.199
Oct  6 16:19:45 ubuntuMB dhclient: DHCPREQUEST of 82.130.78.154 on eth1 to 129.132.128.199 port 67
Oct  6 16:19:45 ubuntuMB dhclient: DHCPACK of 82.130.78.154 from 129.132.128.199
Oct  6 16:23:43 ubuntuMB dhclient: DHCPREQUEST of 82.130.78.154 on eth1 to 129.132.128.199 port 67
Oct  6 16:23:43 ubuntuMB dhclient: DHCPACK of 82.130.78.154 from 129.132.128.199
Oct  6 16:28:34 ubuntuMB dhclient: DHCPREQUEST of 82.130.78.154 on eth1 to 129.132.128.199 port 67
Oct  6 16:28:34 ubuntuMB dhclient: DHCPACK of 82.130.78.154 from 129.132.128.199
Oct  6 16:32:36 ubuntuMB dhclient: DHCPREQUEST of 82.130.78.154 on eth1 to 129.132.128.199 port 67
Oct  6 16:32:36 ubuntuMB dhclient: DHCPACK of 82.130.78.154 from 129.132.128.199
Oct  6 16:37:29 ubuntuMB dhclient: DHCPREQUEST of 82.130.78.154 on eth1 to 129.132.128.199 port 67
Oct  6 16:37:29 ubuntuMB dhclient: DHCPACK of 82.130.78.154 from 129.132.128.199
Oct  6 16:41:54 ubuntuMB dhclient: DHCPREQUEST of 82.130.78.154 on eth1 to 129.132.128.199 port 67
Oct  6 16:41:54 ubuntuMB dhclient: DHCPACK of 82.130.78.154 from 129.132.128.199
Oct  6 16:46:12 ubuntuMB dhclient: DHCPREQUEST of 82.130.78.154 on eth1 to 129.132.128.199 port 67
Oct  6 16:46:12 ubuntuMB dhclient: DHCPACK of 82.130.78.154 from 129.132.128.199
Oct  6 16:50:35 ubuntuMB dhclient: DHCPREQUEST of 82.130.78.154 on eth1 to 129.132.128.199 port 67
Oct  6 16:50:35 ubuntuMB dhclient: DHCPACK of 82.130.78.154 from 129.132.128.199
Oct  6 16:52:54 ubuntuMB NetworkManager[843]: <info> (eth1): canceled DHCP transaction, DHCP client pid 4494
Oct  7 10:07:17 ubuntuMB NetworkManager[843]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  7 10:07:18 ubuntuMB dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct  7 10:07:18 ubuntuMB dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  7 10:07:19 ubuntuMB NetworkManager[843]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Oct  7 10:07:19 ubuntuMB dhclient: DHCPREQUEST of 192.168.7.2 on eth0 to 255.255.255.255 port 67
Oct  7 10:07:19 ubuntuMB dhclient: DHCPNAK from 213.196.149.72
Oct  7 10:07:19 ubuntuMB NetworkManager[843]: <info> (eth0): DHCPv4 state changed preinit -> expire
Oct  7 10:07:19 ubuntuMB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Oct  7 10:07:19 ubuntuMB NetworkManager[843]: <info> (eth0): DHCPv4 state changed expire -> preinit
Oct  7 10:07:20 ubuntuMB dhclient: DHCPOFFER of 213.196.161.226 from 213.196.149.72
Oct  7 10:07:20 ubuntuMB dhclient: DHCPREQUEST of 213.196.161.226 on eth0 to 255.255.255.255 port 67
Oct  7 10:07:20 ubuntuMB dhclient: DHCPACK of 213.196.161.226 from 213.196.149.72
Oct  7 10:07:20 ubuntuMB NetworkManager[843]: <info> (eth0): DHCPv4 state changed preinit -> bound
Oct  7 11:02:30 ubuntuMB dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct  7 11:02:30 ubuntuMB dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct  7 11:02:30 ubuntuMB dhcpd: All rights reserved.
Oct  7 11:02:30 ubuntuMB dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct  7 11:02:30 ubuntuMB dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Oct  7 11:02:30 ubuntuMB dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Oct  7 11:02:30 ubuntuMB dhcpd: All rights reserved.
Oct  7 11:02:30 ubuntuMB dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Oct  7 11:02:30 ubuntuMB dhcpd: Wrote 0 leases to leases file.
Oct  7 11:02:30 ubuntuMB dhcpd: 
Oct  7 11:02:30 ubuntuMB dhcpd: No subnet declaration for eth0 (213.196.161.226).
Oct  7 11:02:30 ubuntuMB dhcpd: ** Ignoring requests on eth0.  If this is not what
Oct  7 11:02:30 ubuntuMB dhcpd:    you want, please write a subnet declaration
Oct  7 11:02:30 ubuntuMB dhcpd:    in your dhcpd.conf file for the network segment
Oct  7 11:02:30 ubuntuMB dhcpd:    to which interface eth0 is attached. **
Oct  7 11:02:30 ubuntuMB dhcpd: 
Oct  7 11:02:30 ubuntuMB dhcpd: 
Oct  7 11:02:30 ubuntuMB dhcpd: Not configured to listen on any interfaces!
Oct  7 11:02:32 ubuntuMB kernel: [26297.106280] type=1400 audit(1317978152.954:20): apparmor="STATUS" operation="profile_load" name="/usr/sbin/dhcpd" pid=19756 comm="apparmor_parser"

```

PS: I've also tried this solution [https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless](https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless) which actually explains exactly what I want, but again, the problem is that the wifi device doesn't seem to be detected. It's neither listed in the file /etc/network/interfaces nor in the output to iwconfig...

---

### Post by jwcalla on 2011-10-07
I just went through this the past week and I'm now hairless.

I did give Firestarter a try and just went "meh".

This is the strategy I used to finally get my Android sharing Internet from my Ubuntu machine; I can't say it's the best, but it seems to work.  Since you have a later distro, you may be able to skip getting the latest drivers and hostapd and just stick with what comes pre-installed.

1) You need a wifi device that supports master mode / soft AP.
2) Determine which driver you should use for your device.  This will help you get started:  [http://linuxwireless.org/en/users/Devices](http://linuxwireless.org/en/users/Devices) .  Then go here: [http://linuxwireless.org/en/users/Drivers](http://linuxwireless.org/en/users/Drivers) and determine if the driver you need supports AP mode.  (Note that some drivers have been deprecated and replaced by newer drivers.)
3) Once the appropriate driver is found, click on the driver link and download the latest firmware.  Copy to /lib/firmware (you might want to make a backup copy if there is a pre-existing version in that directory).
3) Get, compile, and install the latest (stable) compat-wireless driver, which can be downloaded here: [http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/)
4) After installing the driver, reboot and then login and verify that the driver you want is loaded with first priority for your wireless device (use lsmod for this).  If an older driver is loaded or given first priority because your kernel is being a doodyhead, then you'll have to manually blacklist that driver in /etc/modprobe.d/blacklist.conf and reboot.
5) Install the iw and libnl-dev packages from the Ubuntu repositories.
6) You're going to need hostapd to put the device into master mode / AP and handle authentication.  You can try installing the one from the repo, or get the "latest stable release (0.7.3)" from here: [http://w1.fi/hostapd/](http://w1.fi/hostapd/) .  Directions for compiling and installing are here: [http://linuxwireless.org/en/users/Documentation/hostapd](http://linuxwireless.org/en/users/Documentation/hostapd) .
7) You'll need a hostapd configuration file.  Copy the one included in the source (hostapd.conf) and modify to your liking.  The link above explains some of the options.  I'll attach mine at the end so you can get an idea of a working config.  Copy it to /etc/hostapd/hostapd.conf.
8) Even if your Android can connect and authenticate with the wifi device, it won't be able to do jack without an IP address.  So I use a package called dhcp3-server to dole out IP addresses.  Install the one from the repo.  You'll need to set up the configuration file to define your network.  An existing one is in /etc/dhcp3/dhcpd.conf.  I'll attach mine at the end as a sample.
9) Even if your Android has an IP address, it isn't going to be able to do jack if it can't find teh interwebz.  I used iptables to route traffic from / to the wlan0 interface to / from my eth0 interface (if you're using different interfaces, adjust accordingly).  Some people like to create a bridge interface to do this, but hey -- I was desperate.  So if you already have an existing /etc/iptables.rules, make a backup copy... then do the following as root:

```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -A FORWARD -i wlan0 -j ACCEPT
iptables-save > /etc/iptables.rules
```10) You have to convince the kernel to IP forward... so as root:
    ```
echo 1 > /proc/sys/net/ipv4/ip_forward
```
Make this permanent by editing the file /etc/sysctl.conf and uncomment / add the following lines (you probably don't need them all, but I was desperate so I threw everything at it):

```
net.ipv4.ip_forward=1
net.ipv4.conf.default.forwarding=1
net.ipv4.conf.all.forwarding=1

```11) You're now ready to give it a try and see what breaks first.  Use the IP address that you defined in dhcpd.conf for your wlan0 interface.  Bring it up, then hostapd, then restart dhcp3:

```
ifconfig wlan0 inet 192.168.5.1 netmask 255.255.255.0
/usr/local/bin/hostapd -B /etc/hostapd/hostapd.conf
service dhcp3-server restart
```12) Put the knife back in the drawer and then try to connect from your Android.  Post all the errors here and we'll help you find the problem.
13) In the off-chance that this works, you can make this all happen automatically on boot by adding the following to your /etc/rc.local file (I'm still working on a solution for suspend / resume):

```
/sbin/ifconfig wlan0 inet 192.168.5.1 netmask 255.255.255.0
/sbin/iptables-restore < /etc/iptables.rules
/usr/local/bin/hostapd -B /etc/hostapd/hostapd.conf
service dhcp3-server start

```The following is a sample /etc/hostapd/hostapd.conf, using mostly default options.  You'll have to adjust for your device's peculiarities:

```

interface=wlan0
driver=nl80211
logger_syslog=-1
logger_syslog_level=2
logger_stdout=-1
logger_stdout_level=2
dump_file=/tmp/hostapd.dump
ctrl_interface=/var/run/hostapd
ctrl_interface_group=0
ssid=my_ssid
country_code=US
hw_mode=g
channel=1
beacon_int=100
dtim_period=2
max_num_sta=255
rts_threshold=2347
fragm_threshold=2346
macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wmm_enabled=1
wmm_ac_bk_cwmin=4
wmm_ac_bk_cwmax=10
wmm_ac_bk_aifs=7
wmm_ac_bk_txop_limit=0
wmm_ac_bk_acm=0
wmm_ac_be_aifs=3
wmm_ac_be_cwmin=4
wmm_ac_be_cwmax=10
wmm_ac_be_txop_limit=0
wmm_ac_be_acm=0
wmm_ac_vi_aifs=2
wmm_ac_vi_cwmin=3
wmm_ac_vi_cwmax=4
wmm_ac_vi_txop_limit=94
wmm_ac_vi_acm=0
wmm_ac_vo_aifs=2
wmm_ac_vo_cwmin=2
wmm_ac_vo_cwmax=3
wmm_ac_vo_txop_limit=47
wmm_ac_vo_acm=0
ieee80211n=1
ht_capab=[HT40+][SHORT-GI-40][DSSS_CCK-40]
eapol_key_index_workaround=0
eap_server=0
own_ip_addr=127.0.0.1
wpa=2
wpa_passphrase=mah_password
wpa_pairwise=TKIP CCMP
rsn_pairwise=CCMP
wpa_ptk_rekey=600

```Here's my /etc/dhcp3/dhcpd.conf file... you can adjust your network IP addresses however you'd like:

```

ddns-update-style none;
default-lease-time 600;
max-lease-time 7200;
log-facility local7;
subnet 192.168.5.0 netmask 255.255.255.0 {
   range 192.168.5.2 192.168.5.254;
   option routers 192.168.5.1;
   option domain-name-servers 192.168.0.1;
   option ip-forwarding off;
   option subnet-mask 255.255.255.0;
   option broadcast-address 192.168.5.255;
}

```Note that for domain name servers I'm just pointing to the address of my local router.  If you don't have a router, you could try using your ISP's DNS, or one of the public DNSs out there.  If you check /etc/resolv.conf it might provide a hint to which nameserver you're using.

Well... that's how I rolled.  It's probably not the best way to configure a wireless access point... but it works and I was getting pissed so unless someone can show me a better way, this is all I know.

Source:  [http://ubuntuforums.org/showthread.php?t=1553521](http://ubuntuforums.org/showthread.php?t=1553521)

---

### Post by jwcalla on 2011-10-07
Let me re-iterate that steps 1 through 6 -- including both steps 3 -- are most likely not needed unless you're having driver problems.  The packages out-of-box are probably going to be good enough to work.  You can check "dmesg" to see if a driver is being successfully loaded for your wifi device.

---

