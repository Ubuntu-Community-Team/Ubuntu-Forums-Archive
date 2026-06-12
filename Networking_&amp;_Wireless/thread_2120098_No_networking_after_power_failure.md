---
title: "No networking after power failure"
date: 2013-02-25
forum: Networking &amp; Wireless
---

### Post by squigish on 2013-02-25
I have a desktop in my office at a university, running Ubuntu Lucid 10.04. I generally leave the machine running 24/7, and often access it remotely. Last Friday, while I was not in my office, a few minutes after noon, there was a power failure in the building, which took down both my desktop and (I presume) some or all of the networking infrastructure (switches/routers).  My machine rebooted itself at 12:08, but did not successfully gain network connectivity until I came into the office on Monday morning and manually troubleshooted/fixed it.  

Some more information: (In several cases, I've removed known-to-be-valid IP addresses for confidentiality/security reasons). 

Output of ifconfig eth0 on Monday morning with no network connectivity over the weekend:
```
eth0      Link encap:Ethernet  HWaddr bc:ae:c5:bd:44:d2  
          inet6 addr: fe80::beae:c5ff:febd:44d2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1998852 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:204034235 (204.0 MB)  TX bytes:2988 (2.9 KB)
          Interrupt:26 Base address:0xe000 
```

I then ran (as root) 
```
ifconfig eth0 down
ifconfig eth0 up
``` which resulted in the following being logged to /var/log/syslog, but the problem persisting
```
Feb 25 10:22:10 refrigerator kernel: [252821.646168] r8169: eth0: link down
Feb 25 10:22:10 refrigerator NetworkManager: <info>  (eth0): carrier now OFF (device state 3)
Feb 25 10:22:10 refrigerator NetworkManager: <info>  (eth0): device state change: 3 -> 2 (reason 40)
Feb 25 10:22:10 refrigerator NetworkManager: <info>  (eth0): deactivating device (reason: 40).
Feb 25 10:22:12 refrigerator NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Feb 25 10:22:12 refrigerator NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Feb 25 10:22:12 refrigerator kernel: [252823.195858] r8169: eth0: link up
Feb 25 10:23:20 refrigerator NetworkManager: <info>  (eth0): carrier now OFF (device state 3)
Feb 25 10:23:20 refrigerator NetworkManager: <info>  (eth0): device state change: 3 -> 2 (reason 40)
Feb 25 10:23:20 refrigerator NetworkManager: <info>  (eth0): deactivating device (reason: 40).
Feb 25 10:23:20 refrigerator avahi-daemon[1039]: Withdrawing address record for fe80::beae:c5ff:febd:44d2 on eth0.
Feb 25 10:23:22 refrigerator NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Feb 25 10:23:22 refrigerator NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Feb 25 10:23:22 refrigerator kernel: [252894.005601] r8169: eth0: link up
Feb 25 10:23:24 refrigerator avahi-daemon[1039]: Registering new address record for fe80::beae:c5ff:febd:44d2 on eth0.*.
Feb 25 10:23:33 refrigerator kernel: [252904.670907] eth0: no IPv6 routers present
```

I then used the network-manager GUI applet to select "auto eth0", which successfully got me a working IPv4 address, and network/internet connectivity.  This created the following syslog output:

```
Feb 25 10:27:29 refrigerator NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Feb 25 10:27:29 refrigerator NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Feb 25 10:27:29 refrigerator NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Feb 25 10:27:29 refrigerator NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Feb 25 10:27:29 refrigerator NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Feb 25 10:27:29 refrigerator NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Feb 25 10:27:29 refrigerator NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Feb 25 10:27:29 refrigerator NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Feb 25 10:27:29 refrigerator NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Feb 25 10:27:29 refrigerator NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Feb 25 10:27:29 refrigerator NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Feb 25 10:27:29 refrigerator NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Feb 25 10:27:29 refrigerator NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Feb 25 10:27:29 refrigerator NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Feb 25 10:27:29 refrigerator NetworkManager: <info>  dhclient started with pid 12144
Feb 25 10:27:29 refrigerator NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Feb 25 10:27:29 refrigerator NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Feb 25 10:27:29 refrigerator NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Feb 25 10:27:29 refrigerator NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Feb 25 10:27:29 refrigerator dhclient: Internet Systems Consortium DHCP Client V3.1.3
Feb 25 10:27:29 refrigerator dhclient: Copyright 2004-2009 Internet Systems Consortium.
Feb 25 10:27:29 refrigerator dhclient: All rights reserved.
Feb 25 10:27:29 refrigerator dhclient: For info, please visit https://www.isc.org/software/dhcp/
Feb 25 10:27:29 refrigerator dhclient: 
Feb 25 10:27:29 refrigerator NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Feb 25 10:27:29 refrigerator dhclient: Listening on LPF/eth0/bc:ae:c5:bd:44:d2
Feb 25 10:27:29 refrigerator dhclient: Sending on   LPF/eth0/bc:ae:c5:bd:44:d2
Feb 25 10:27:29 refrigerator dhclient: Sending on   Socket/fallback
Feb 25 10:27:31 refrigerator dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Feb 25 10:27:39 refrigerator dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Feb 25 10:27:39 refrigerator dhclient: DHCPOFFER of <my address> from <DHCP server address>
Feb 25 10:27:39 refrigerator dhclient: DHCPREQUEST of <my address> on eth0 to 255.255.255.255 port 67
Feb 25 10:27:39 refrigerator dhclient: DHCPACK of <my address> from <DHCP server address>
Feb 25 10:27:39 refrigerator dhclient: bound to <my address> -- renewal in 2879 seconds.
Feb 25 10:27:39 refrigerator NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Feb 25 10:27:39 refrigerator NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Feb 25 10:27:39 refrigerator NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Feb 25 10:27:39 refrigerator NetworkManager: <info>    address <my address>
Feb 25 10:27:39 refrigerator NetworkManager: <info>    prefix 22 (255.255.252.0)
Feb 25 10:27:39 refrigerator NetworkManager: <info>    gateway <gateway address>
Feb 25 10:27:39 refrigerator NetworkManager: <info>    hostname 'my-hostname'
Feb 25 10:27:39 refrigerator NetworkManager: <info>    nameserver '<nameserver address>'
Feb 25 10:27:39 refrigerator NetworkManager: <info>    nameserver '<another nameserver address>'
Feb 25 10:27:39 refrigerator NetworkManager: <info>    domain name '<domain name>'
Feb 25 10:27:39 refrigerator NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Feb 25 10:27:39 refrigerator NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Feb 25 10:27:39 refrigerator NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Feb 25 10:27:39 refrigerator avahi-daemon[1039]: Joining mDNS multicast group on interface eth0.IPv4 with address <my address>.
Feb 25 10:27:39 refrigerator avahi-daemon[1039]: New relevant interface eth0.IPv4 for mDNS.
Feb 25 10:27:39 refrigerator avahi-daemon[1039]: Registering new address record for <my address> on eth0.IPv4.
Feb 25 10:27:40 refrigerator NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Feb 25 10:27:40 refrigerator NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Feb 25 10:27:40 refrigerator NetworkManager: <info>  Activation (eth0) successful, device activated.
Feb 25 10:27:40 refrigerator NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Feb 25 10:27:40 refrigerator ntpd[1678]: ntpd exiting on signal 15
Feb 25 10:27:40 refrigerator ntpdate[12221]: can't find host wuarchive.wustl.edu
Feb 25 10:27:42 refrigerator ntpd_initres[1681]: parent died before we finished, exiting
```

Looking at older copies of my syslog, I find the following entries from when the computer was first booting up and trying to connect to the network:
```
Feb 22 12:08:39 refrigerator NetworkManager: <info>  starting...
Feb 22 12:08:39 refrigerator NetworkManager: <info>  Trying to start the modem-manager...
Feb 22 12:08:39 refrigerator NetworkManager:    SCPlugin-Ifupdown: init!
Feb 22 12:08:39 refrigerator NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Feb 22 12:08:39 refrigerator NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Feb 22 12:08:39 refrigerator NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:0a.0/0000:02:00.0/net/eth0, iface: eth0)
Feb 22 12:08:39 refrigerator NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:0a.0/0000:02:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Feb 22 12:08:39 refrigerator NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Feb 22 12:08:39 refrigerator NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Feb 22 12:08:39 refrigerator NetworkManager:    SCPlugin-Ifupdown: end _init.
Feb 22 12:08:39 refrigerator NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Feb 22 12:08:39 refrigerator NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Feb 22 12:08:39 refrigerator NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
Feb 22 12:08:39 refrigerator NetworkManager: <info>  WWAN enabled by radio killswitch; disabled by state file
Feb 22 12:08:39 refrigerator NetworkManager:    SCPlugin-Ifupdown: (40186144) ... get_connections.
Feb 22 12:08:39 refrigerator NetworkManager:    SCPlugin-Ifupdown: (40186144) ... get_connections (managed=false): return empty list.
Feb 22 12:08:39 refrigerator NetworkManager:    Ifupdown: get unmanaged devices count: 0
Feb 22 12:08:39 refrigerator NetworkManager: <info>  (eth0): carrier is OFF
Feb 22 12:08:39 refrigerator NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
Feb 22 12:08:39 refrigerator NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Feb 22 12:08:39 refrigerator NetworkManager: <info>  (eth0): now managed
Feb 22 12:08:39 refrigerator NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Feb 22 12:08:39 refrigerator NetworkManager: <info>  (eth0): bringing up device.
Feb 22 12:08:39 refrigerator NetworkManager: <info>  (eth0): preparing device.
Feb 22 12:08:39 refrigerator NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Feb 22 12:08:39 refrigerator NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:0a.0/0000:02:00.0/net/eth0
Feb 22 12:08:39 refrigerator NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Feb 22 12:08:39 refrigerator NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Feb 22 12:08:39 refrigerator kernel: [   10.376624] r8169: eth0: link up
Feb 22 12:08:39 refrigerator kernel: [   10.376629] r8169: eth0: link up
Feb 22 12:08:39 refrigerator NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Feb 22 12:08:39 refrigerator NetworkManager: <info>  Trying to start the supplicant...
Feb 22 12:08:39 refrigerator NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Feb 22 12:08:39 refrigerator NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Feb 22 12:08:39 refrigerator NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Feb 22 12:08:39 refrigerator NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Feb 22 12:08:39 refrigerator NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Feb 22 12:08:39 refrigerator NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Feb 22 12:08:39 refrigerator NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Feb 22 12:08:39 refrigerator NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Feb 22 12:08:39 refrigerator NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Feb 22 12:08:39 refrigerator NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Feb 22 12:08:39 refrigerator NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Feb 22 12:08:39 refrigerator NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Feb 22 12:08:39 refrigerator NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Feb 22 12:08:39 refrigerator NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Feb 22 12:08:39 refrigerator modem-manager: Loaded plugin MotoC
Feb 22 12:08:39 refrigerator modem-manager: Loaded plugin Gobi
Feb 22 12:08:39 refrigerator modem-manager: Loaded plugin Huawei
Feb 22 12:08:39 refrigerator modem-manager: Loaded plugin Option High-Speed
Feb 22 12:08:39 refrigerator modem-manager: Loaded plugin Option
Feb 22 12:08:39 refrigerator modem-manager: Loaded plugin Sierra
Feb 22 12:08:39 refrigerator modem-manager: Loaded plugin Novatel
Feb 22 12:08:39 refrigerator modem-manager: Loaded plugin Nokia
Feb 22 12:08:39 refrigerator modem-manager: Loaded plugin ZTE
Feb 22 12:08:39 refrigerator modem-manager: Loaded plugin Ericsson MBM
Feb 22 12:08:39 refrigerator modem-manager: Loaded plugin Longcheer
Feb 22 12:08:39 refrigerator modem-manager: Loaded plugin AnyData
Feb 22 12:08:39 refrigerator modem-manager: Loaded plugin Generic
Feb 22 12:08:39 refrigerator NetworkManager: <info>  dhclient started with pid 1071
Feb 22 12:08:39 refrigerator NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Feb 22 12:08:39 refrigerator NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Feb 22 12:08:39 refrigerator NetworkManager: <info>  modem-manager is now available
Feb 22 12:08:39 refrigerator NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Feb 22 12:08:39 refrigerator NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Feb 22 12:08:39 refrigerator dhclient: Internet Systems Consortium DHCP Client V3.1.3
Feb 22 12:08:39 refrigerator dhclient: Copyright 2004-2009 Internet Systems Consortium.
Feb 22 12:08:39 refrigerator dhclient: All rights reserved.
Feb 22 12:08:39 refrigerator dhclient: For info, please visit https://www.isc.org/software/dhcp/
Feb 22 12:08:39 refrigerator dhclient: 
Feb 22 12:08:39 refrigerator NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Feb 22 12:08:39 refrigerator dhclient: Listening on LPF/eth0/bc:ae:c5:bd:44:d2
Feb 22 12:08:39 refrigerator dhclient: Sending on   LPF/eth0/bc:ae:c5:bd:44:d2
Feb 22 12:08:39 refrigerator dhclient: Sending on   Socket/fallback
Feb 22 12:08:39 refrigerator cron[1103]: (CRON) INFO (pidfile fd = 3)
Feb 22 12:08:39 refrigerator acpid: starting up with proc fs
Feb 22 12:08:39 refrigerator cron[1126]: (CRON) STARTUP (fork ok)
Feb 22 12:08:39 refrigerator anacron[1125]: Anacron 2.3 started on 2013-02-22
Feb 22 12:08:39 refrigerator init: apport pre-start process (1097) terminated with status 1
Feb 22 12:08:39 refrigerator init: apport post-stop process (1129) terminated with status 1
Feb 22 12:08:39 refrigerator acpid: 36 rules loaded
Feb 22 12:08:39 refrigerator acpid: waiting for events: event logging is off
Feb 22 12:08:39 refrigerator anacron[1125]: Normal exit (0 jobs run)
Feb 22 12:08:39 refrigerator cron[1126]: (CRON) INFO (Running @reboot jobs)
Feb 22 12:08:40 refrigerator ez-ipupdate[1361]: version 3.0.11b8, interface eth0, host <my dyndns domain name>, server members.dyndns.org, service dyndns
Feb 22 12:08:40 refrigerator ez-ipupdate[1361]: got last update <my ip address> on 2013/02/20 07:38 from cache file
Feb 22 12:08:40 refrigerator ez-ipupdate[1361]: (<my dyndns domain name>) unable to resolve interface eth0
Feb 22 12:08:40 refrigerator gdm-binary[1508]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Feb 22 12:08:40 refrigerator gdm-simple-slave[1531]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Feb 22 12:08:40 refrigerator gdm-binary[1508]: WARNING: Unable to find users: no seat-id found
Feb 22 12:08:41 refrigerator /etc/mysql/debian-start[1537]: Upgrading MySQL tables if necessary.
Feb 22 12:08:41 refrigerator /etc/mysql/debian-start[1540]: /usr/bin/mysql_upgrade: the '--basedir' option is always ignored
Feb 22 12:08:41 refrigerator /etc/mysql/debian-start[1540]: Looking for 'mysql' as: /usr/bin/mysql
Feb 22 12:08:41 refrigerator /etc/mysql/debian-start[1540]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Feb 22 12:08:41 refrigerator /etc/mysql/debian-start[1540]: This installation of MySQL is already upgraded to 5.1.67, use --force if you still need to run mysql_upgrade
Feb 22 12:08:41 refrigerator /etc/mysql/debian-start[1556]: Checking for insecure root accounts.
Feb 22 12:08:41 refrigerator /etc/mysql/debian-start[1565]: Triggering myisam-recover for all MyISAM tables
Feb 22 12:08:41 refrigerator avahi-daemon[1039]: Registering new address record for fe80::beae:c5ff:febd:44d2 on eth0.*.
Feb 22 12:08:41 refrigerator anacron[1590]: Anacron 2.3 started on 2013-02-22
Feb 22 12:08:41 refrigerator anacron[1590]: Normal exit (0 jobs run)
Feb 22 12:08:41 refrigerator kernel: [   12.365386] CPU0 attaching NULL sched-domain.
Feb 22 12:08:41 refrigerator kernel: [   12.365390] CPU1 attaching NULL sched-domain.
Feb 22 12:08:41 refrigerator kernel: [   12.610095] CPU0 attaching sched-domain:
Feb 22 12:08:41 refrigerator kernel: [   12.610097]  domain 0: span 0-1 level MC
Feb 22 12:08:41 refrigerator kernel: [   12.610099]   groups: 0 1
Feb 22 12:08:41 refrigerator kernel: [   12.610103] CPU1 attaching sched-domain:
Feb 22 12:08:41 refrigerator kernel: [   12.610104]  domain 0: span 0-1 level MC
Feb 22 12:08:41 refrigerator kernel: [   12.610105]   groups: 1 0
Feb 22 12:08:41 refrigerator kernel: [   12.685575] ppdev: user-space parallel port driver
Feb 22 12:08:41 refrigerator ddclient[1652]: WARNING:  file /var/cache/ddclient/ddclient.cache, line 4: Invalid Value for keyword 'ip' = ''
Feb 22 12:08:41 refrigerator ddclient[1652]: WARNING:  cannot connect to whatismyip.com:80 socket: IO::Socket::INET: Bad hostname 'whatismyip.com'
Feb 22 12:08:41 refrigerator ddclient[1652]: WARNING:  cannot connect to checkip.dyndns.com:80 socket: IO::Socket::INET: Bad hostname 'checkip.dyndns.com'
Feb 22 12:08:41 refrigerator ntpd[1676]: ntpd 4.2.4p8@1.1612-o Tue Apr 19 07:08:18 UTC 2011 (1)
Feb 22 12:08:41 refrigerator ntpd[1678]: precision = 1.000 usec
Feb 22 12:08:41 refrigerator ntpd[1678]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Feb 22 12:08:41 refrigerator ntpd[1678]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Feb 22 12:08:41 refrigerator ntpd[1678]: Listening on interface #1 wildcard, ::#123 Disabled
Feb 22 12:08:41 refrigerator ntpd[1678]: Listening on interface #2 lo, 127.0.0.1#123 Enabled
Feb 22 12:08:41 refrigerator ntpd[1678]: Listening on interface #3 eth0, fe80::beae:c5ff:febd:44d2#123 Enabled
Feb 22 12:08:41 refrigerator ntpd[1678]: Listening on interface #4 lo, ::1#123 Enabled
Feb 22 12:08:41 refrigerator ntpd[1678]: kernel time sync status 2040
Feb 22 12:08:41 refrigerator ntpd[1678]: frequency initialized -57.782 PPM from /var/lib/ntp/ntp.drift
Feb 22 12:08:41 refrigerator ntpd[1681]: signal_no_reset: signal 17 had flags 4000000
```

I have a longer version of this file, syslog.3.txt, which contains some messages from before the power failure, and the entire boot sequence, but I can't attach it because of the file size limits for text attachments.  You can view the [COLOR="Blue"]_[syslog file here]("http://dl.dropbox.com/u/53384785/syslog.3.txt")_[/COLOR] and the [COLOR="Blue"]_[dmesg file here]("http://dl.dropbox.com/u/53384785/dmesg.txt")_[/COLOR]

Since the system is now working fine, my goal here is to make the system boot normally after a future power failure, and connect to the network properly, even if the networking hardware also went down in the same power failure.  It would also be nice to understand why/how this happened in the first place.

---

### Post by tgalati4 on 2013-02-25
Any switches or routers that went down will have to be rebooted in a certain order to get the IP address caching established.  Also, just because the power came back does not mean it came back cleanly.  Many times there is a power ripple which messes up the boot process of embedded devices, so they have to be rebooted as well.  

If your machine is on an UPS, you can program it to wait 10 minutes or 30 minutes after a power failure to recharge (for continued protection) and to allow the power to settle and for the routers to repopulate their routing tables.

---

### Post by squigish on 2013-02-26
Thanks for the reply.

My machine is not on a UPS. For my applications, it's not a big deal if it goes down on the rare occasions we have a power failure, but it's a problem if it then remains down until I next have physical access to the machine.  

Perhaps I could write a script that I could run at boot time that checks for network connectivity every minute until it's present, and each time it fails to find connectivity, resets the connection?  

Because I did the fix for the connectivity issue through the GUI, I don't even know what command-line commands will work to fix it.  

```
ifconfig eth0 down
ifconfig eth0 up
```
doesn't work.  

For that matter, what would be a good way to test whether the connection is up?  Perhaps 
```
if wget www.google.com >/dev/null
```
Can you think of a more elegant way to do this?

---

### Post by tgalati4 on 2013-02-26
An UPS would help.  Many network cards have firmware and maintain routing tables that get trashed during a power outage.  Sometimes you have to physically unplug the machine to get the network card chips to reset properly.  

Also, it appears that you are running dhcp, and thus you need to request an IP address once your machine boots.  Since this is a university network, I assume that the router that you are connected to has a lot of IP addresses to hand out after a power outage.  Perhaps you could work with the university IT staff and assign a fixed IP.  That might give you near-instant network connectivity after a power outage, since the router can start talking to your machine immediately.

Using ifconfig up and down won't work if the router is too busy handing out IP addresses to all the machines.  You could simply put a *sleep 120* in the boot script, but that would happen at every boot--not convenient.

As far as detecting your network presence, there are perhaps a dozen ways to do this.

*netstat -r* will give you your current routing table.  If it is empty then you won't have a network to talk to.  

You could use ping:

tgalati4@Mint14-Extensa ~/.emacs.d $ ping -c 2 [www.google.com](www.google.com)
PING [www.google.com](www.google.com) (74.125.224.242) 56(84) bytes of data.
64 bytes from lax04s08-in-f18.1e100.net (74.125.224.242): icmp_req=1 ttl=52 time=49.7 ms
64 bytes from lax04s08-in-f18.1e100.net (74.125.224.242): icmp_req=2 ttl=52 time=50.5 ms

--- [www.google.com](www.google.com) ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 49.767/50.160/50.554/0.452 ms

And an awk or perl script that picks out the transmit time.  As long as the time is below some metric (say 100 ms) in my case, then your network is up and connected.

Talk to your university IT staff for some ideas.  

I can't understand the use case of not caring if the machine goes down, but can't wait to bring it back up.  Most modern UPS's deal with this situation and you can tailor it to your needs.

1.  I don't care if it goes down and I don't care if it reboots properly unattended.  No UPS needed.
2.  I don't care if it goes down and I do care if it reboots properly unattended.  UPS would help.

3.  I do care if it goes down and I don't care if it reboots properly unattended.  UPS with no-reboot set in BIOS or set up in UPS to stay down until reset.  Good for checking for damage.
4.  I do care if it goes down and I do care if it reboots right away when unattended.  UPS with reboot set in BIOS and buffer period set in UPS configuration.

---

### Post by squigish on 2013-02-26
> **tgalati4 said:**
> 
I can't understand the use case of not caring if the machine goes down, but can't wait to bring it back up. 

Basically, the applications I have running are tolerant to occasional interruptions.  If the power cuts happened regularly, I'd definitely look into a UPS or some other solution, but there's sufficiently uncommon that they're not a large cause for worry.  When I'm not physically at the computer, the biggest thing I use it for is as a backup destination for Crashplan, a remote backup service.  Crashplan is fault tolerant in that it will re-verify whatever it was working on prior to the power outage, so there's no data loss.  Since it's only the backup copy anyways, it can always re-retrive the data from the primary copy after it comes back up.

However, the backup is relatively slow, so it's important for it to be running for most of 24/7.  In this case, even though the machine was running, it was totally unusable remotely all weekend until I physically came into the office on Monday. It's not a huge deal, but an inconvenience. 


My sysadmin found _[a launchpad bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/672562")_ that looks like exactly the problem I'm having.  Since this is a desktop machine with a fixed connection, I'm probably just going to remove network manager.

---

### Post by tgalati4 on 2013-02-26
Now that is a helpful IT staff.  Good call on finding the bug.  A lot of the convenience frameworks that we rely on tend to hinder reliability.  Nothing wrong with old-school, manual network configuration.

---

