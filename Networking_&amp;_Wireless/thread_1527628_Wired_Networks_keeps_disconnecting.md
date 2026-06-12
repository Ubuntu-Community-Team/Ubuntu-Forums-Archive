---
title: "Wired Networks keeps disconnecting"
date: 2010-07-09
forum: Networking &amp; Wireless
---

### Post by AlexPraem on 2010-07-09
Every time I try to connect another computer by cable it finds the network, but after trying to connect to it for 30 secs or so it just says "Wired network Disconnected". I've tried finding answers for hours but I've had no luck so far.
I am running ubuntu 10.04 on my Acer Aspire 4810T and my ethernet controller according to my memory is Atheros AR 8131.

Any help would be appreciated.

---

### Post by fdrsde on 2010-08-24
Hi everybody,
i have a similar problem with my ubuntu 10.4, while i attempt to run backup for my macbook(time machine), my ubuntu begin to disconnect continuosly the wired network connection.
I've tryed to change my router (from Dlink DIR-300 to Sitecom wl340 v2 001) but it was unsuccessfull.
my home network is composed by:
1 NAS in wired connection: Linux NAS-ubuntu 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:38:40 UTC 2010 x86_64 GNU/Linux
1 mediaplayer: Qnap nmp-1000 in wired connection
1 macbook in wireless connection

I have the same problem also when i try to see a movie(resident on ubuntu) with my mediaplayer.
Please help me to resolve this problem.
Thanks in advance
Federico
In detail this is the partial log of daemon.log:
Aug 24 19:48:14 NAS-ubuntu afpd[7762]: ASIP session:548(4) from 192.168.0.105:49199(7)
Aug 24 19:48:14 NAS-ubuntu afpd[7762]: DHX2 login: federico
Aug 24 19:48:16 NAS-ubuntu NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Aug 24 19:48:18 NAS-ubuntu NetworkManager: <info>  (eth0): carrier now ON (device state 8)
Aug 24 19:48:19 NAS-ubuntu afpd[7762]: DHX2: logincont2 alive!
Aug 24 19:48:19 NAS-ubuntu afpd[7762]: PAM DHX2: PAM Success
Aug 24 19:48:19 NAS-ubuntu afpd[7762]: DHX2: PAM Auth OK!
Aug 24 19:48:19 NAS-ubuntu afpd[7762]: login federico (uid 1000, gid 1000) AFP3.1
Aug 24 19:48:27 NAS-ubuntu afpd[7762]: Warning: No CNID scheme for volume /media/NAS. Using default.
Aug 24 19:48:27 NAS-ubuntu afpd[7762]: Setting uid/gid to 1000/1000
Aug 24 19:48:27 NAS-ubuntu afpd[7762]: CNID DB initialized using Berkeley DB 4.8.24: (August 14, 2009)
Aug 24 19:48:27 NAS-ubuntu afpd[7762]: ipc_write: command: 2, pid: 7762, msglen: 24
Aug 24 19:48:27 NAS-ubuntu afpd[1525]: ipc_read: command: 2, pid: 7762, len: 24
Aug 24 19:48:27 NAS-ubuntu afpd[1525]: Setting clientid (len 16) for 7762, boottime 4C73F292
Aug 24 19:48:27 NAS-ubuntu afpd[1525]: ipc_get_session: len: 24, idlen 16, time 4c73f292
Aug 24 19:48:27 NAS-ubuntu afpd[7762]: Setting uid/gid to 1000/1000
Aug 24 19:48:27 NAS-ubuntu afpd[7766]: ASIP session:548(4) from 192.168.0.105:49200(7)
Aug 24 19:48:27 NAS-ubuntu afpd[7762]: ipc_write: command: 2, pid: 7762, msglen: 24
Aug 24 19:48:27 NAS-ubuntu afpd[1525]: ipc_read: command: 2, pid: 7762, len: 24
Aug 24 19:48:27 NAS-ubuntu afpd[1525]: Setting clientid (len 16) for 7762, boottime 4C73F292
Aug 24 19:48:27 NAS-ubuntu afpd[1525]: ipc_get_session: len: 24, idlen 16, time 4c73f292
Aug 24 19:48:27 NAS-ubuntu afpd[1525]: server_child[1] 7766 done
Aug 24 19:48:27 NAS-ubuntu afpd[7762]: Warning: No CNID scheme for volume /home/federico. Using default.
Aug 24 19:48:27 NAS-ubuntu afpd[7762]: Setting uid/gid to 1000/1000
Aug 24 19:48:27 NAS-ubuntu afpd[7767]: ASIP session:548(4) from 192.168.0.105:49201(7)
Aug 24 19:48:27 NAS-ubuntu afpd[1525]: server_child[1] 7767 done
Aug 24 19:48:27 NAS-ubuntu afpd[7768]: ASIP session:548(4) from 192.168.0.105:49202(7)
Aug 24 19:48:27 NAS-ubuntu afpd[1525]: server_child[1] 7768 done
Aug 24 19:48:27 NAS-ubuntu afpd[7762]: ipc_write: command: 2, pid: 7762, msglen: 24
Aug 24 19:48:27 NAS-ubuntu afpd[1525]: ipc_read: command: 2, pid: 7762, len: 24
Aug 24 19:48:27 NAS-ubuntu afpd[1525]: Setting clientid (len 16) for 7762, boottime 4C73F292
Aug 24 19:48:27 NAS-ubuntu afpd[1525]: ipc_get_session: len: 24, idlen 16, time 4c73f292
Aug 24 19:48:27 NAS-ubuntu afpd[7769]: ASIP session:548(4) from 192.168.0.105:49203(7)
Aug 24 19:48:27 NAS-ubuntu afpd[1525]: server_child[1] 7769 done
Aug 24 19:48:27 NAS-ubuntu afpd[7770]: ASIP session:548(4) from 192.168.0.105:49204(7)
Aug 24 19:48:27 NAS-ubuntu afpd[1525]: server_child[1] 7770 done
Aug 24 19:48:27 NAS-ubuntu afpd[7771]: ASIP session:548(4) from 192.168.0.105:49205(7)
Aug 24 19:48:27 NAS-ubuntu afpd[1525]: server_child[1] 7771 done
Aug 24 19:48:27 NAS-ubuntu afpd[7772]: ASIP session:548(4) from 192.168.0.105:49206(7)
Aug 24 19:48:27 NAS-ubuntu afpd[1525]: server_child[1] 7772 done
Aug 24 19:48:27 NAS-ubuntu afpd[7773]: ASIP session:548(4) from 192.168.0.105:49207(7)
Aug 24 19:48:27 NAS-ubuntu afpd[1525]: server_child[1] 7773 done
Aug 24 19:48:27 NAS-ubuntu afpd[7774]: ASIP session:548(4) from 192.168.0.105:49208(7)
Aug 24 19:48:27 NAS-ubuntu afpd[1525]: server_child[1] 7774 done
Aug 24 19:48:31 NAS-ubuntu NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Aug 24 19:48:35 NAS-ubuntu NetworkManager: <info>  (eth0): device state change: 8 -> 2 (reason 40)
Aug 24 19:48:35 NAS-ubuntu NetworkManager: <info>  (eth0): deactivating device (reason: 40).
Aug 24 19:48:35 NAS-ubuntu NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 7561
Aug 24 19:48:35 NAS-ubuntu NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess#012
Aug 24 19:48:35 NAS-ubuntu avahi-daemon[911]: Withdrawing address record for 192.168.0.102 on eth0.
Aug 24 19:48:35 NAS-ubuntu avahi-daemon[911]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.102.
Aug 24 19:48:35 NAS-ubuntu avahi-daemon[911]: Interface eth0.IPv4 no longer relevant for mDNS.
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>  Activation (eth0) starting connection 'eth0'
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>  dhclient started with pid 7811
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Aug 24 19:48:37 NAS-ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.3
Aug 24 19:48:37 NAS-ubuntu dhclient: Copyright 2004-2009 Internet Systems Consortium.
Aug 24 19:48:37 NAS-ubuntu dhclient: All rights reserved.
Aug 24 19:48:37 NAS-ubuntu dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Aug 24 19:48:37 NAS-ubuntu dhclient: 
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Aug 24 19:48:37 NAS-ubuntu dhclient: Listening on LPF/eth0/00:27:0e:02:b3:a9
Aug 24 19:48:37 NAS-ubuntu dhclient: Sending on   LPF/eth0/00:27:0e:02:b3:a9
Aug 24 19:48:37 NAS-ubuntu dhclient: Sending on   Socket/fallback
Aug 24 19:48:37 NAS-ubuntu dhclient: DHCPREQUEST of 192.168.0.102 on eth0 to 255.255.255.255 port 67
Aug 24 19:48:37 NAS-ubuntu dhclient: DHCPACK of 192.168.0.102 from 192.168.0.1
Aug 24 19:48:37 NAS-ubuntu dhclient: bound to 192.168.0.102 -- renewal in 139285745 seconds.
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>  DHCP: device eth0 state changed preinit -> reboot
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>    address 192.168.0.102
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>    prefix 24 (255.255.255.0)
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>    gateway 192.168.0.1
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>    nameserver '192.168.0.1'
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>    domain name 'casa'
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>    wins '192.168.0.1'
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Aug 24 19:48:37 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Aug 24 19:48:37 NAS-ubuntu avahi-daemon[911]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.102.
Aug 24 19:48:37 NAS-ubuntu avahi-daemon[911]: New relevant interface eth0.IPv4 for mDNS.
Aug 24 19:48:37 NAS-ubuntu avahi-daemon[911]: Registering new address record for 192.168.0.102 on eth0.IPv4.
Aug 24 19:48:38 NAS-ubuntu NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Aug 24 19:48:38 NAS-ubuntu NetworkManager: <info>  Policy set 'eth0' (eth0) as default for routing and DNS.
Aug 24 19:48:38 NAS-ubuntu NetworkManager: <info>  Activation (eth0) successful, device activated.
Aug 24 19:48:38 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Aug 24 19:48:39 NAS-ubuntu ntpdate[7863]: adjust time server 91.189.94.4 offset 0.042084 sec
Aug 24 19:48:44 NAS-ubuntu NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Aug 24 19:48:49 NAS-ubuntu NetworkManager: <info>  (eth0): device state change: 8 -> 2 (reason 40)
Aug 24 19:48:49 NAS-ubuntu NetworkManager: <info>  (eth0): deactivating device (reason: 40).
Aug 24 19:48:49 NAS-ubuntu NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 7811
Aug 24 19:48:49 NAS-ubuntu NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess#012
Aug 24 19:48:49 NAS-ubuntu avahi-daemon[911]: Withdrawing address record for 192.168.0.102 on eth0.
Aug 24 19:48:49 NAS-ubuntu avahi-daemon[911]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.102.
Aug 24 19:48:49 NAS-ubuntu avahi-daemon[911]: Interface eth0.IPv4 no longer relevant for mDNS.
Aug 24 19:49:04 NAS-ubuntu NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Aug 24 19:49:04 NAS-ubuntu NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Aug 24 19:49:04 NAS-ubuntu NetworkManager: <info>  Activation (eth0) starting connection 'eth0'
Aug 24 19:49:04 NAS-ubuntu NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Aug 24 19:49:04 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 24 19:49:04 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Aug 24 19:49:04 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Aug 24 19:49:04 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Aug 24 19:49:04 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Aug 24 19:49:04 NAS-ubuntu NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Aug 24 19:49:04 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Aug 24 19:49:04 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 24 19:49:04 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Aug 24 19:49:04 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Aug 24 19:49:04 NAS-ubuntu NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Aug 24 19:49:04 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Aug 24 19:49:04 NAS-ubuntu NetworkManager: <info>  dhclient started with pid 7927
Aug 24 19:49:04 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Aug 24 19:49:04 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Aug 24 19:49:04 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Aug 24 19:49:04 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Aug 24 19:49:04 NAS-ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.3
Aug 24 19:49:04 NAS-ubuntu dhclient: Copyright 2004-2009 Internet Systems Consortium.
Aug 24 19:49:04 NAS-ubuntu dhclient: All rights reserved.
Aug 24 19:49:04 NAS-ubuntu dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Aug 24 19:49:04 NAS-ubuntu dhclient: 
Aug 24 19:49:04 NAS-ubuntu NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Aug 24 19:49:04 NAS-ubuntu dhclient: Listening on LPF/eth0/00:27:0e:02:b3:a9
Aug 24 19:49:04 NAS-ubuntu dhclient: Sending on   LPF/eth0/00:27:0e:02:b3:a9
Aug 24 19:49:04 NAS-ubuntu dhclient: Sending on   Socket/fallback
Aug 24 19:49:04 NAS-ubuntu dhclient: DHCPREQUEST of 192.168.0.102 on eth0 to 255.255.255.255 port 67
Aug 24 19:49:09 NAS-ubuntu dhclient: DHCPREQUEST of 192.168.0.102 on eth0 to 255.255.255.255 port 67
Aug 24 19:49:09 NAS-ubuntu dhclient: DHCPACK of 192.168.0.102 from 192.168.0.1
Aug 24 19:49:09 NAS-ubuntu dhclient: bound to 192.168.0.102 -- renewal in 143989748 seconds.
Aug 24 19:49:09 NAS-ubuntu NetworkManager: <info>  DHCP: device eth0 state changed preinit -> reboot
Aug 24 19:49:09 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Aug 24 19:49:09 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Aug 24 19:49:09 NAS-ubuntu NetworkManager: <info>    address 192.168.0.102
Aug 24 19:49:09 NAS-ubuntu NetworkManager: <info>    prefix 24 (255.255.255.0)
Aug 24 19:49:09 NAS-ubuntu NetworkManager: <info>    gateway 192.168.0.1
Aug 24 19:49:09 NAS-ubuntu NetworkManager: <info>    nameserver '192.168.0.1'
Aug 24 19:49:09 NAS-ubuntu NetworkManager: <info>    domain name 'casa'
Aug 24 19:49:09 NAS-ubuntu NetworkManager: <info>    wins '192.168.0.1'
Aug 24 19:49:09 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Aug 24 19:49:09 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Aug 24 19:49:09 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Aug 24 19:49:09 NAS-ubuntu avahi-daemon[911]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.102.
Aug 24 19:49:09 NAS-ubuntu avahi-daemon[911]: New relevant interface eth0.IPv4 for mDNS.
Aug 24 19:49:09 NAS-ubuntu avahi-daemon[911]: Registering new address record for 192.168.0.102 on eth0.IPv4.
Aug 24 19:49:10 NAS-ubuntu NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Aug 24 19:49:10 NAS-ubuntu NetworkManager: <info>  Policy set 'eth0' (eth0) as default for routing and DNS.
Aug 24 19:49:10 NAS-ubuntu NetworkManager: <info>  Activation (eth0) successful, device activated.
Aug 24 19:49:10 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Aug 24 19:49:10 NAS-ubuntu ntpdate[7984]: adjust time server 91.189.94.4 offset 0.029534 sec
Aug 24 19:49:11 NAS-ubuntu afpd[8010]: ASIP session:548(4) from 192.168.0.105:49209(7)
Aug 24 19:49:11 NAS-ubuntu afpd[1525]: server_child[1] 8010 done
Aug 24 19:49:12 NAS-ubuntu NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Aug 24 19:49:16 NAS-ubuntu NetworkManager: <info>  (eth0): device state change: 8 -> 2 (reason 40)
Aug 24 19:49:16 NAS-ubuntu NetworkManager: <info>  (eth0): deactivating device (reason: 40).
Aug 24 19:49:17 NAS-ubuntu NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 7927
Aug 24 19:49:17 NAS-ubuntu NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess#012
Aug 24 19:49:17 NAS-ubuntu avahi-daemon[911]: Withdrawing address record for 192.168.0.102 on eth0.
Aug 24 19:49:17 NAS-ubuntu avahi-daemon[911]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.102.
Aug 24 19:49:17 NAS-ubuntu avahi-daemon[911]: Interface eth0.IPv4 no longer relevant for mDNS.
Aug 24 19:49:21 NAS-ubuntu NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Aug 24 19:49:21 NAS-ubuntu NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Aug 24 19:49:21 NAS-ubuntu NetworkManager: <info>  Activation (eth0) starting connection 'eth0'
Aug 24 19:49:21 NAS-ubuntu NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Aug 24 19:49:21 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 24 19:49:21 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Aug 24 19:49:21 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Aug 24 19:49:21 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Aug 24 19:49:21 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Aug 24 19:49:21 NAS-ubuntu NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Aug 24 19:49:21 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Aug 24 19:49:21 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 24 19:49:21 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Aug 24 19:49:21 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Aug 24 19:49:21 NAS-ubuntu NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Aug 24 19:49:21 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Aug 24 19:49:21 NAS-ubuntu NetworkManager: <info>  dhclient started with pid 8043
Aug 24 19:49:21 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Aug 24 19:49:21 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Aug 24 19:49:21 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Aug 24 19:49:21 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Aug 24 19:49:21 NAS-ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.3
Aug 24 19:49:21 NAS-ubuntu dhclient: Copyright 2004-2009 Internet Systems Consortium.
Aug 24 19:49:21 NAS-ubuntu dhclient: All rights reserved.
Aug 24 19:49:21 NAS-ubuntu dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Aug 24 19:49:21 NAS-ubuntu dhclient: 
Aug 24 19:49:21 NAS-ubuntu NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Aug 24 19:49:21 NAS-ubuntu dhclient: Listening on LPF/eth0/00:27:0e:02:b3:a9
Aug 24 19:49:21 NAS-ubuntu dhclient: Sending on   LPF/eth0/00:27:0e:02:b3:a9
Aug 24 19:49:21 NAS-ubuntu dhclient: Sending on   Socket/fallback
Aug 24 19:49:23 NAS-ubuntu dhclient: DHCPREQUEST of 192.168.0.102 on eth0 to 255.255.255.255 port 67
Aug 24 19:49:23 NAS-ubuntu dhclient: DHCPACK of 192.168.0.102 from 192.168.0.1
Aug 24 19:49:23 NAS-ubuntu NetworkManager: <info>  DHCP: device eth0 state changed preinit -> reboot
Aug 24 19:49:23 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Aug 24 19:49:23 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Aug 24 19:49:23 NAS-ubuntu NetworkManager: <info>    address 192.168.0.102
Aug 24 19:49:23 NAS-ubuntu NetworkManager: <info>    prefix 24 (255.255.255.0)
Aug 24 19:49:23 NAS-ubuntu NetworkManager: <info>    gateway 192.168.0.1
Aug 24 19:49:23 NAS-ubuntu NetworkManager: <info>    nameserver '192.168.0.1'
Aug 24 19:49:23 NAS-ubuntu NetworkManager: <info>    domain name 'casa'
Aug 24 19:49:23 NAS-ubuntu NetworkManager: <info>    wins '192.168.0.1'
Aug 24 19:49:23 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Aug 24 19:49:23 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Aug 24 19:49:23 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Aug 24 19:49:23 NAS-ubuntu avahi-daemon[911]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.102.
Aug 24 19:49:23 NAS-ubuntu avahi-daemon[911]: New relevant interface eth0.IPv4 for mDNS.
Aug 24 19:49:23 NAS-ubuntu avahi-daemon[911]: Registering new address record for 192.168.0.102 on eth0.IPv4.
Aug 24 19:49:23 NAS-ubuntu dhclient: bound to 192.168.0.102 -- renewal in 134673702 seconds.
Aug 24 19:49:24 NAS-ubuntu NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Aug 24 19:49:24 NAS-ubuntu NetworkManager: <info>  Policy set 'eth0' (eth0) as default for routing and DNS.
Aug 24 19:49:24 NAS-ubuntu NetworkManager: <info>  Activation (eth0) successful, device activated.
Aug 24 19:49:24 NAS-ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Aug 24 19:49:24 NAS-ubuntu ntpdate[8095]: adjust time server 91.189.94.4 offset 0.023479 sec
Aug 24 19:49:27 NAS-ubuntu afpd[8124]: ASIP session:548(4) from 192.168.0.105:49210(7)
Aug 24 19:49:27 NAS-ubuntu afpd[8124]: DHX2 login: federico
Aug 24 19:49:33 NAS-ubuntu NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Aug 24 19:49:33 NAS-ubuntu afpd[8124]: DHX2: logincont2 alive!
Aug 24 19:49:33 NAS-ubuntu afpd[8124]: PAM DHX2: PAM Success
Aug 24 19:49:34 NAS-ubuntu afpd[8124]: DHX2: PAM Auth OK!
Aug 24 19:49:34 NAS-ubuntu afpd[8124]: login federico (uid 1000, gid 1000) AFP3.1
Aug 24 19:49:35 NAS-ubuntu NetworkManager: <info>  (eth0): carrier now ON (device state 8)
Aug 24 19:49:37 NAS-ubuntu afpd[8124]: Setting uid/gid to 1000/1000
Aug 24 19:49:37 NAS-ubuntu afpd[8124]: CNID DB initialized using Berkeley DB 4.8.24: (August 14, 2009)
Aug 24 19:49:37 NAS-ubuntu afpd[8124]: ipc_write: command: 2, pid: 8124, msglen: 24
Aug 24 19:49:37 NAS-ubuntu afpd[1525]: ipc_read: command: 2, pid: 8124, len: 24
Aug 24 19:49:37 NAS-ubuntu afpd[1525]: Setting clientid (len 16) for 8124, boottime 4C73F292
Aug 24 19:49:37 NAS-ubuntu afpd[1525]: WARNING: 2 connections (7762, 8124), boottime identical, don't know if one needs to be disconnected.
Aug 24 19:49:37 NAS-ubuntu afpd[1525]: ipc_get_session: len: 24, idlen 16, time 4c73f292
Aug 24 19:49:37 NAS-ubuntu afpd[8129]: ASIP session:548(4) from 192.168.0.105:49211(7)
Aug 24 19:49:37 NAS-ubuntu afpd[1525]: server_child[1] 8129 done
Aug 24 19:49:37 NAS-ubuntu afpd[8130]: ASIP session:548(4) from 192.168.0.105:49212(7)
Aug 24 19:49:37 NAS-ubuntu afpd[1525]: server_child[1] 8130 done
Aug 24 19:49:37 NAS-ubuntu afpd[8131]: ASIP session:548(4) from 192.168.0.105:49213(7)
Aug 24 19:49:37 NAS-ubuntu afpd[1525]: server_child[1] 8131 done
Aug 24 19:49:37 NAS-ubuntu afpd[8132]: ASIP session:548(4) from 192.168.0.105:49214(7)
Aug 24 19:49:37 NAS-ubuntu afpd[1525]: server_child[1] 8132 done
Aug 24 19:49:37 NAS-ubuntu afpd[8133]: ASIP session:548(4) from 192.168.0.105:49215(7)
Aug 24 19:49:37 NAS-ubuntu afpd[1525]: server_child[1] 8133 done
Aug 24 19:49:37 NAS-ubuntu afpd[8134]: ASIP session:548(4) from 192.168.0.105:49216(7)
Aug 24 19:49:37 NAS-ubuntu afpd[1525]: server_child[1] 8134 done
Aug 24 19:49:38 NAS-ubuntu afpd[8124]: logout federico
Aug 24 19:49:38 NAS-ubuntu afpd[8124]: 1.35KB read, 1.23KB written
Aug 24 19:49:38 NAS-ubuntu afpd[1525]: server_child[1] 8124 done
Aug 24 19:49:38 NAS-ubuntu afpd[8138]: ASIP session:548(4) from 192.168.0.105:49217(7)
Aug 24 19:49:38 NAS-ubuntu afpd[1525]: server_child[1] 8138 done
Aug 24 19:49:38 NAS-ubuntu afpd[8139]: ASIP session:548(4) from 192.168.0.105:49218(7)
Aug 24 19:49:38 NAS-ubuntu afpd[1525]: server_child[1] 8139 done
Aug 24 19:49:38 NAS-ubuntu afpd[8140]: ASIP session:548(4) from 192.168.0.105:49219(7)
Aug 24 19:49:38 NAS-ubuntu afpd[1525]: server_child[1] 8140 done
Aug 24 19:49:38 NAS-ubuntu afpd[8141]: ASIP session:548(4) from 192.168.0.105:49220(7)
Aug 24 19:49:38 NAS-ubuntu afpd[1525]: server_child[1] 8141 done
Aug 24 19:49:38 NAS-ubuntu afpd[8142]: ASIP session:548(4) from 192.168.0.105:49221(7)
Aug 24 19:49:38 NAS-ubuntu afpd[1525]: server_child[1] 8142 done
Aug 24 19:49:38 NAS-ubuntu afpd[8143]: ASIP session:548(4) from 192.168.0.105:49222(7)
Aug 24 19:49:38 NAS-ubuntu afpd[1525]: server_child[1] 8143 done
Aug 24 19:49:47 NAS-ubuntu NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Aug 24 19:49:49 NAS-ubuntu NetworkManager: <info>  (eth0): carrier now ON (device state 8)
Aug 24 19:49:50 NAS-ubuntu NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Aug 24 19:49:51 NAS-ubuntu NetworkManager: <info>  (eth0): carrier now ON (device state 8)
Aug 24 19:50:19 NAS-ubuntu NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Aug 24 19:50:20 NAS-ubuntu NetworkManager: <info>  (eth0): carrier now ON (device state 8)
Aug 24 19:50:25 NAS-ubuntu NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)

---

### Post by pombe on 2010-08-24
Hi guys.  There must have been an update that screwed with the NetworkManager or something as I've been having wired connection issues as well.   I installed the new version of Network-Manager via the instructions [here]("http://ubuntuforums.org/showthread.php?t=1560027") and I'm connecting fine now.

Good luck

C

---

### Post by fdrsde on 2010-08-24
Thanks a lot for the hint!
Unfortunately the upgrade didn't resolved the problem :(.
now the log show these lines:
Aug 24 22:12:17 NAS-ubuntu NetworkManager[951]: <info> (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Aug 24 22:12:21 NAS-ubuntu NetworkManager[951]: <info> (eth0): device state change: 8 -> 2 (reason 40)
Aug 24 22:12:21 NAS-ubuntu NetworkManager[951]: <info> (eth0): deactivating device (reason: 40).
Aug 24 22:12:21 NAS-ubuntu NetworkManager[951]: <info> (eth0): canceled DHCP transaction, DHCP client pid 2861
Aug 24 22:12:21 NAS-ubuntu avahi-daemon[934]: Withdrawing address record for 192.168.0.102 on eth0.
Aug 24 22:12:21 NAS-ubuntu avahi-daemon[934]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.102.
Aug 24 22:12:21 NAS-ubuntu avahi-daemon[934]: Interface eth0.IPv4 no longer relevant for mDNS.
Aug 24 22:12:21 NAS-ubuntu NetworkManager[951]: <info> Policy set 'Auto federico' (wlan0) as default for IPv4 routing and DNS.
Aug 24 22:12:21 NAS-ubuntu NetworkManager[951]: <info> Updating /etc/hosts with new system hostname
Aug 24 22:12:21 NAS-ubuntu NetworkManager[951]: <info> Policy set 'Auto federico' (wlan0) as default for IPv4 routing and DNS.
Aug 24 22:12:21 NAS-ubuntu NetworkManager[951]: <info> (eth0): carrier now ON (device state 2)
Aug 24 22:12:21 NAS-ubuntu NetworkManager[951]: <info> (eth0): device state change: 2 -> 3 (reason 40)
Aug 24 22:12:21 NAS-ubuntu NetworkManager[951]: <info> Activation (eth0) starting connection 'eth0'
Aug 24 22:12:21 NAS-ubuntu NetworkManager[951]: <info> (eth0): device state change: 3 -> 4 (reason 0)
Aug 24 22:12:21 NAS-ubuntu NetworkManager[951]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 24 22:12:21 NAS-ubuntu NetworkManager[951]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Aug 24 22:12:21 NAS-ubuntu NetworkManager[951]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Aug 24 22:12:21 NAS-ubuntu NetworkManager[951]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Aug 24 22:12:21 NAS-ubuntu NetworkManager[951]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Aug 24 22:12:21 NAS-ubuntu NetworkManager[951]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Aug 24 22:12:21 NAS-ubuntu NetworkManager[951]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Aug 24 22:12:21 NAS-ubuntu NetworkManager[951]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 24 22:12:21 NAS-ubuntu NetworkManager[951]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Aug 24 22:12:21 NAS-ubuntu NetworkManager[951]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Aug 24 22:12:21 NAS-ubuntu NetworkManager[951]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Aug 24 22:12:21 NAS-ubuntu NetworkManager[951]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Aug 24 22:12:21 NAS-ubuntu NetworkManager[951]: <info> dhclient started with pid 3010
Aug 24 22:12:21 NAS-ubuntu NetworkManager[951]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Aug 24 22:12:21 NAS-ubuntu dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Aug 24 22:12:21 NAS-ubuntu dhclient: Copyright 2004-2010 Internet Systems Consortium.
Aug 24 22:12:21 NAS-ubuntu dhclient: All rights reserved.
Aug 24 22:12:21 NAS-ubuntu dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Aug 24 22:12:21 NAS-ubuntu dhclient: 
Aug 24 22:12:21 NAS-ubuntu nm-dispatcher.action: nm_dispatcher_action: Invalid connection: '(null)' / 'connection setting not found' invalid: 1
Aug 24 22:12:21 NAS-ubuntu nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Aug 24 22:12:21 NAS-ubuntu NetworkManager[951]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Aug 24 22:12:21 NAS-ubuntu dhclient: Listening on LPF/eth0/00:27:0e:02:b3:a9
Aug 24 22:12:21 NAS-ubuntu dhclient: Sending on   LPF/eth0/00:27:0e:02:b3:a9
Aug 24 22:12:21 NAS-ubuntu dhclient: Sending on   Socket/fallback
Aug 24 22:12:24 NAS-ubuntu dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Aug 24 22:12:24 NAS-ubuntu dhclient: DHCPACK from 192.168.0.1
Aug 24 22:12:24 NAS-ubuntu NetworkManager[951]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Aug 24 22:12:24 NAS-ubuntu NetworkManager[951]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Aug 24 22:12:24 NAS-ubuntu NetworkManager[951]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Aug 24 22:12:24 NAS-ubuntu NetworkManager[951]: <info>   address 192.168.0.102
Aug 24 22:12:24 NAS-ubuntu NetworkManager[951]: <info>   prefix 24 (255.255.255.0)
Aug 24 22:12:24 NAS-ubuntu NetworkManager[951]: <info>   gateway 192.168.0.1
Aug 24 22:12:24 NAS-ubuntu NetworkManager[951]: <info>   nameserver '192.168.0.1'
Aug 24 22:12:24 NAS-ubuntu NetworkManager[951]: <info>   domain name 'casa'
Aug 24 22:12:24 NAS-ubuntu NetworkManager[951]: <info>   wins '192.168.0.1'
Aug 24 22:12:24 NAS-ubuntu NetworkManager[951]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Aug 24 22:12:24 NAS-ubuntu NetworkManager[951]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Aug 24 22:12:24 NAS-ubuntu NetworkManager[951]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Aug 24 22:12:24 NAS-ubuntu avahi-daemon[934]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.102.
Aug 24 22:12:24 NAS-ubuntu avahi-daemon[934]: New relevant interface eth0.IPv4 for mDNS.
Aug 24 22:12:24 NAS-ubuntu avahi-daemon[934]: Registering new address record for 192.168.0.102 on eth0.IPv4.
Aug 24 22:12:24 NAS-ubuntu dhclient: bound to 192.168.0.102 -- renewal in 153400281 seconds.
Aug 24 22:12:25 NAS-ubuntu NetworkManager[951]: <info> Policy set 'Auto federico' (wlan0) as default for IPv4 routing and DNS.
Aug 24 22:12:25 NAS-ubuntu NetworkManager[951]: <info> (eth0): device state change: 7 -> 8 (reason 0)
Aug 24 22:12:25 NAS-ubuntu NetworkManager[951]: <info> Policy set 'eth0' (eth0) as default for IPv4 routing and DNS.
Aug 24 22:12:25 NAS-ubuntu NetworkManager[951]: <info> Updating /etc/hosts with new system hostname
Aug 24 22:12:25 NAS-ubuntu NetworkManager[951]: <info> Activation (eth0) successful, device activated.
Aug 24 22:12:25 NAS-ubuntu NetworkManager[951]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Aug 24 22:12:25 NAS-ubuntu nm-dispatcher.action: nm_dispatcher_action: Invalid connection: '(null)' / 'connection setting not found' invalid: 1
Aug 24 22:12:25 NAS-ubuntu nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Aug 24 22:12:25 NAS-ubuntu ntpdate[3093]: adjust time server 91.189.94.4 offset 0.001362 sec

---

