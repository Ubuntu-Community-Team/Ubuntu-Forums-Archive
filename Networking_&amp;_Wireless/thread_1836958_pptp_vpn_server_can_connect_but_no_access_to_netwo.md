---
title: "pptp vpn server can connect but no access to network services"
date: 2011-08-31
forum: Networking &amp; Wireless
---

### Post by kpholmes on 2011-08-31
im trying to setup a vpn server on a ddwrt router, i know this isn't the ddwrt forums but i cant seem to find ANY help there; and my question has to do with networking and the ubuntuforums has some smart people so i figured there might be someone here who can help me,


ive set up a pptp vpn server on the router, using this how-to [http://www.dd-wrt.com/wiki/index.php/PPTP_Server_Configuration#Outgoing_PPTP_Connections](http://www.dd-wrt.com/wiki/index.php/PPTP_Server_Configuration#Outgoing_PPTP_Connections)

ive forward the ports 1723 and 1792 to the router (not the pptp server)

i can connect from my ubuntu desktop and phone, but i cant reach any of the services in the network im connected to. has anyone had this problem or know of a solution?

could it be a DNS issue?

thanks in advance!


edit: heres my ifconfig when im connected to the vpn.

ubuntu@ubuntu:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:21:9b:24:50:2f
inet addr:192.168.1.100 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::221:9bff:fe24:502f/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:118995 errors:0 dropped:0 overruns:0 frame:0
TX packets:106538 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:104942381 (104.9 MB) TX bytes:15820794 (15.8 MB)
Interrupt:27 Base address:0xa000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:106 errors:0 dropped:0 overruns:0 frame:0
TX packets:106 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:12200 (12.2 KB) TX bytes:12200 (12.2 KB)

ppp0 Link encap:Point-to-Point Protocol
inet addr:192.168.1.140 P-t-P:192.168.1.102 Mask:255.255.255.255
UP POINTOPOINT RUNNING NOARP MULTICAST MTU:1400 Metric:1
RX packets:24 errors:0 dropped:0 overruns:0 frame:0
TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:3
RX bytes:10618 (10.6 KB) TX bytes:2373 (2.3 KB)

edit #2: heres a ifconfig on a computer on the network in which i am trying to connect to, note that the mask address is not the same, should they be???

eth0 Link encap:Ethernet HWaddr 00:22:68:3f:46:a5
inet addr:192.168.1.103 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::222:68ff:fe3f:46a5/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:753524 errors:0 dropped:0 overruns:0 frame:0
TX packets:973866 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:96531348 (96.5 MB) TX bytes:548959594 (548.9 MB)
Interrupt:40 Base address:0xa000

edit 3: so i've changed the server ip in ddwrt pptp server setting to the routers ip of 192.168.1.1 which is not recommended by the guide that i used and listed above, but while connected with the new server ip i can inside my browser go to 192.168.1.1 and hit my ddwrt router and not the one that im behind at my remote location. after a while it will disconnect me, so i check /var/log/messages and here was the output:

Sep 1 01:52:44 ubuntu pppd[5898]: Using interface ppp0
Sep 1 01:52:44 ubuntu pppd[5898]: Connect: ppp0 <--> /dev/pts/0
Sep 1 01:52:49 ubuntu pppd[5898]: CHAP authentication succeeded
Sep 1 01:52:50 ubuntu pppd[5898]: MPPE 128-bit stateless compression enabled
Sep 1 01:52:50 ubuntu pppd[5898]: found interface eth0 for proxy arp
Sep 1 01:52:50 ubuntu pppd[5898]: local IP address 192.168.1.140
Sep 1 01:52:50 ubuntu pppd[5898]: remote IP address 192.168.1.1
Sep 1 01:52:50 ubuntu pppd[5898]: primary DNS address 192.168.1.1
Sep 1 01:52:50 ubuntu pppd[5898]: secondary DNS address 192.168.1.1
Sep 1 01:54:46 ubuntu pppd[5898]: Modem hangup
Sep 1 01:54:46 ubuntu pppd[5898]: Connect time 2.0 minutes.
Sep 1 01:54:46 ubuntu pppd[5898]: Sent 48902 bytes, received 457479 bytes.
Sep 1 01:54:46 ubuntu pppd[5898]: Connection terminated.
Sep 1 01:54:47 ubuntu pppd[5898]: Exit.


whats causing the modem hang up? and is my remote computer confused on which dns server to use?

any help would be appreciated...

---

