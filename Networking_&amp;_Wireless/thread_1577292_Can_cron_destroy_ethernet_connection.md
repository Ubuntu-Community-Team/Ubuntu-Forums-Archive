---
title: "Can cron destroy ethernet connection?"
date: 2010-09-18
forum: Networking &amp; Wireless
---

### Post by hg21 on 2010-09-18
When I boot up I have internet for a time then it disappears after a few minutes.

Looking at syslog it seems to happen after cron.daily runs (may be coincidence).

On reboot cron.daily didn't run and the ethernet connection is OK.

syslog: from ethernet start up to where cron.daily runs and loss of connection is:-
{I have replaced actual addresses by ****** in case there is a security risk}
==================================================================
Sep 18 09:54:11 hg21-Lucid dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67
interval 3
Sep 18 09:54:11 hg21-Lucid dhclient: DHCPOFFER of ***** from *******
Sep 18 09:54:11 hg21-Lucid dhclient: DHCPREQUEST of ********* on eth0 to 255.255.
255.255 port 67
Sep 18 09:54:11 hg21-Lucid dhclient: DHCPACK of ******* from *******
Sep 18 09:54:11 hg21-Lucid dhclient: bound to ******* -- renewal in 132919 seco
nds.
Sep 18 09:54:11 hg21-Lucid NetworkManager: <info> DHCP: device eth0 state changed pr
einit -> bound
Sep 18 09:54:11 hg21-Lucid NetworkManager: <info> Activation (eth0) Stage 4 of 5 (IP
4 Configure Get) scheduled...
Sep 18 09:54:11 hg21-Lucid NetworkManager: <info> Activation (eth0) Stage 4 of 5 (IP
4 Configure Get) started...
Sep 18 09:54:11 hg21-Lucid NetworkManager: <info> address **************
Sep 18 09:54:11 hg21-Lucid NetworkManager: <info> prefix 22 (255.255.252.0)
Sep 18 09:54:11 hg21-Lucid NetworkManager: <info> gateway *********
Sep 18 09:54:11 hg21-Lucid NetworkManager: <info> hostname 'hg21-Lucid'
Sep 18 09:54:11 hg21-Lucid NetworkManager: <info> nameserver '**********'
Sep 18 09:54:11 hg21-Lucid NetworkManager: <info> nameserver '**********'
Sep 18 09:54:11 hg21-Lucid NetworkManager: <info> domain name 'cable.virginmedia.net'
Sep 18 09:54:11 hg21-Lucid NetworkManager: <info> Activation (eth0) Stage 5 of 5 (IP
Configure Commit) scheduled...
Sep 18 09:54:11 hg21-Lucid NetworkManager: <info> Activation (eth0) Stage 4 of 5 (IP
4 Configure Get) complete.
Sep 18 09:54:11 hg21-Lucid NetworkManager: <info> Activation (eth0) Stage 5 of 5 (IP
Configure Commit) started...
Sep 18 09:54:11 hg21-Lucid avahi-daemon[1094]: Joining mDNS multicast group on interf
ace eth0.IPv4 with address **************.
Sep 18 09:54:11 hg21-Lucid avahi-daemon[1094]: New relevant interface eth0.IPv4 for m
DNS.
Sep 18 09:54:11 hg21-Lucid avahi-daemon[1094]: Registering new address record for ********* on eth0.IPv4.
Sep 18 09:54:12 hg21-Lucid NetworkManager: <info> (eth0): device state change: 7 ->
8 (reason 0)
Sep 18 09:54:12 hg21-Lucid NetworkManager: <info> Policy set 'Auto eth0' (eth0) as default for routing and DNS
Sep 18 09:54:12 hg21-Lucid NetworkManager: <info> Activation (eth0) successful, device activated.
Sep 18 09:54:12 hg21-Lucid NetworkManager: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Sep 18 09:54:12 hg21-Lucid postfix/master[1299]: reload -- version 2.7.0, configuration /etc/postfix
Sep 18 09:54:13 hg21-Lucid ntpdate[1458]: step time server ******** offset 1.277531 sec
Sep 18 09:54:15 hg21-Lucid acpid: client connected from **********]
Sep 18 09:54:15 hg21-Lucid acpid: 1 client rule loaded
Sep 18 09:54:15 hg21-Lucid kernel: [ 23.339610] CPUFREQ: Per core ondemand sysfs interface is deprecated - up_threshold
Sep 18 09:54:15 hg21-Lucid kernel: [ 23.450892] CPU0 attaching NULL sched-domain.
Sep 18 09:54:15 hg21-Lucid kernel: [ 23.450906] CPU1 attaching NULL sched-domain.
Sep 18 09:54:15 hg21-Lucid kernel: [ 23.520201] CPU0 attaching sched-domain:
Sep 18 09:54:15 hg21-Lucid kernel: [ 23.520210] domain 0: span 0-1 level MC
Sep 18 09:54:15 hg21-Lucid kernel: [ 23.520217] groups: 0 1
Sep 18 09:54:15 hg21-Lucid kernel: [ 23.520229] CPU1 attaching sched-domain:
Sep 18 09:54:15 hg21-Lucid kernel: [ 23.520234] domain 0: span 0-1 level MC
Sep 18 09:54:15 hg21-Lucid kernel: [ 23.520239] groups: 1 0
Sep 18 09:54:18 hg21-Lucid kernel: [ 26.700014] eth0: no IPv6 routers present
Sep 18 09:54:27 hg21-Lucid polkitd[1818]: started daemon version 0.96 using authority implementation `local' version `0.96'
Sep 18 09:59:08 hg21-Lucid anacron[1213]: Job `cron.daily' started
Sep 18 09:59:08 hg21-Lucid anacron[1980]: Updated timestamp for job `cron.daily' to 2010-09-18
===============================================================

It was around this point I lost internet access

I did:-

$ sudo dhclient
which gave
================================================================
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:***********
Sending on LPF/eth0/00:*********
Sending on Socket/fallback
DHCPREQUEST of **************7 on eth0 to 255.255.255.255 port 67
DHCPREQUEST of ************ on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
HCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
==============================================================

ie not able to connect

The syslog output at this time was:-
==============================================================
Sep 18 10:02:52 hg21-Lucid dhclient: Internet Systems Consortium DHCP Client V3.1.3
Sep 18 10:02:52 hg21-Lucid dhclient: Copyright 2004-2009 Internet Systems Consortium.
Sep 18 10:02:52 hg21-Lucid dhclient: All rights reserved.
Sep 18 10:02:52 hg21-Lucid dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Sep 18 10:02:52 hg21-Lucid dhclient:
Sep 18 10:02:52 hg21-Lucid avahi-daemon[1094]: Withdrawing address record for *******88 on eth0.
Sep 18 10:02:52 hg21-Lucid avahi-daemon[1094]: Leaving mDNS multicast group on interface eth0.IPv4 with address *********$
Sep 18 10:02:52 hg21-Lucid avahi-daemon[1094]: Interface eth0.IPv4 no longer relevant
for mDNS.
Sep 18 10:02:52 hg21-Lucid avahi-daemon[1094]: querier.c: querier_remove() called but no querier to remove.
Sep 18 10:02:52 hg21-Lucid avahi-daemon[1094]: querier.c: querier_remove() called but no querier to remove.
Sep 18 10:02:52 hg21-Lucid dhclient: Listening on LPF/eth0/00:**********
Sep 18 10:02:52 hg21-Lucid dhclient: Sending on LPF/eth0/00:1f:16:fd:71:85
Sep 18 10:02:52 hg21-Lucid dhclient: Sending on Socket/fallback
Sep 18 10:02:52 hg21-Lucid dhclient: DHCPREQUEST of *********** on eth0 to 255.255.255.255 port 67
Sep 18 10:03:00 hg21-Lucid dhclient: DHCPREQUEST of ******* on eth0 to 255.255.255.255 port 67
Sep 18 10:03:09 hg21-Lucid dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Sep 18 10:03:17 hg21-Lucid dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Sep 18 10:03:30 hg21-Lucid dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Sep 18 10:03:38 hg21-Lucid dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
================================================================

I've not found anything in the cron.daily routines that could account for this.

Later in the day my ethernet connection dropped out just after a cron.weekly

Sorry this is so long, please help if you can.

---

