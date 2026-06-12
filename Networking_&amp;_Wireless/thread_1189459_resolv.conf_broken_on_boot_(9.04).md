---
title: "resolv.conf broken on boot (9.04)"
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by Joshua Swink on 2009-06-16
When I first boot up the system, eth0 does get configured, but DNS is broken. The reason: /etc/resolv.conf does not contain the proper information (it contains only a comment).

If I then manually take down eth0 and bring it back up, /etc/resolv.conf will then contain the name servers and all works well.

Entering the following commands fixes the situation. But I must perform them every time the system is booted:

$ sudo ifdown eth0
$ sudo ifup eth0

I suspect network-manager is interfering with the proper operation of dhcp3-client, but don't know how to confirm this.

Here is /etc/network/interfaces:
================================================
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
================================================

Here is some information from /var/log/syslog. In it, we see the kernel recognize eth0. Then dhclient brings up the interface via DHCP. We can see that things are working, because ntpdate successfully updates the clock.

A little bit later, NetworkManager starts up and makes a few log entries regarding eth0. This is why I suspect it is interfering, and may be responsible for the empty /etc/resolv.conf.

My network configuration is entirely vanilla.

(Below: syslog showing the kernel recognizing eth0, dhclient bringing it up, and ntpdate updating the clock.)
================================================================
Jun 16 15:35:19 polecat kernel: [   40.069212] e1000e 0000:00:19.0: irq 2298 for MSI/MSI-X
Jun 16 15:35:19 polecat kernel: [   40.125101] e1000e 0000:00:19.0: irq 2298 for MSI/MSI-X
Jun 16 15:35:19 polecat kernel: [   40.125541] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 16 15:35:20 polecat dhclient: wmaster0: unknown hardware address type 801
Jun 16 15:35:20 polecat dhclient: Listening on LPF/eth0/00:1e:ec:76:41:b2
Jun 16 15:35:20 polecat dhclient: Sending on   LPF/eth0/00:1e:ec:76:41:b2
Jun 16 15:35:20 polecat dhclient: Sending on   Socket/fallback
Jun 16 15:35:21 polecat kernel: [   41.740306] input: PS/2 Generic Mouse as /devices/platform/i8042/serio4/serio5/input/input11
Jun 16 15:35:21 polecat kernel: [   42.426563] 0000:00:19.0: eth0: Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
Jun 16 15:35:21 polecat kernel: [   42.426925] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jun 16 15:35:22 polecat mysqld_safe[3258]: started
Jun 16 15:35:22 polecat mysqld[3261]: 090616 15:35:22  InnoDB: Started; log sequence number 0 361138
Jun 16 15:35:22 polecat mysqld[3261]: 090616 15:35:22 [Note] /usr/sbin/mysqld: ready for connections.
Jun 16 15:35:22 polecat mysqld[3261]: Version: '5.0.75-0ubuntu10.2'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
Jun 16 15:35:23 polecat /etc/mysql/debian-start[3300]: Upgrading MySQL tables if necessary.
Jun 16 15:35:23 polecat /etc/mysql/debian-start[3305]: Looking for 'mysql' as: /usr/bin/mysql
Jun 16 15:35:23 polecat /etc/mysql/debian-start[3305]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Jun 16 15:35:23 polecat /etc/mysql/debian-start[3305]: This installation of MySQL is already upgraded to 5.0.75, use --force if you still need to run mysql_upgrad
e
Jun 16 15:35:23 polecat /etc/mysql/debian-start[3322]: Checking for insecure root accounts.
Jun 16 15:35:23 polecat /etc/mysql/debian-start[3326]: Triggering myisam-recover for all MyISAM tables
Jun 16 15:35:24 polecat dhclient: DHCPREQUEST of 169.236.9.80 on eth0 to 255.255.255.255 port 67
Jun 16 15:35:24 polecat dhclient: DHCPACK of 169.236.9.80 from 169.236.11.100
Jun 16 15:35:24 polecat dhclient: bound to 169.236.9.80 -- renewal in 13776 seconds.
Jun 16 15:35:27 polecat ntpdate[3497]: adjust time server 91.189.94.4 offset -0.043265 sec
================================================================



(syslog a little later, showing NetworkManager starting up and possibly doing things with eth0)
================================================================
Jun 16 15:35:35 polecat NetworkManager: <info>  starting... 
Jun 16 15:35:35 polecat NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/pci_8086_4229_rfkill_4965AGN_wlan 
Jun 16 15:35:35 polecat NetworkManager: <info>  (eth1): new Ethernet device (driver: 'rndis_host') 
Jun 16 15:35:35 polecat NetworkManager: <info>  (eth1): exported as /org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00 
Jun 16 15:35:35 polecat NetworkManager: <info>  (eth0): new Ethernet device (driver: 'e1000e') 
Jun 16 15:35:35 polecat NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_1e_ec_76_41_b2 
Jun 16 15:35:35 polecat avahi-daemon[4195]: Found user 'avahi' (UID 108) and group 'avahi' (GID 116).
Jun 16 15:35:35 polecat avahi-daemon[4195]: Successfully dropped root privileges.
Jun 16 15:35:35 polecat avahi-daemon[4195]: avahi-daemon 0.6.23 starting up.
Jun 16 15:35:35 polecat avahi-daemon[4195]: Successfully called chroot().
Jun 16 15:35:35 polecat avahi-daemon[4195]: Successfully dropped remaining capabilities.
Jun 16 15:35:35 polecat NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01). 
Jun 16 15:35:35 polecat NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'iwlagn') 
Jun 16 15:35:35 polecat NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_21_5c_36_8d_6b 
Jun 16 15:35:35 polecat NetworkManager: <info>  (ttyS0): ignoring due to lack of mobile broadband capabilties 
Jun 16 15:35:35 polecat NetworkManager: <info>  Trying to start the supplicant... 
Jun 16 15:35:35 polecat NetworkManager: <info>  Trying to start the system settings daemon... 
Jun 16 15:35:35 polecat NetworkManager: <info>  (eth0): carrier now ON (device state 1) 
Jun 16 15:35:35 polecat avahi-daemon[4195]: No service file found in /etc/avahi/services.
Jun 16 15:35:35 polecat avahi-daemon[4195]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.236.9.80.
Jun 16 15:35:35 polecat avahi-daemon[4195]: New relevant interface eth0.IPv4 for mDNS.
Jun 16 15:35:35 polecat avahi-daemon[4195]: Network interface enumeration completed.
Jun 16 15:35:35 polecat avahi-daemon[4195]: Registering new address record for fe80::21e:ecff:fe76:41b2 on eth0.*.
Jun 16 15:35:35 polecat avahi-daemon[4195]: Registering new address record for 169.236.9.80 on eth0.IPv4.
Jun 16 15:35:35 polecat avahi-daemon[4195]: Registering HINFO record with values 'X86_64'/'LINUX'.
Jun 16 15:35:35 polecat nm-system-settings:    SCPlugin-Ifupdown: init!
Jun 16 15:35:35 polecat nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Jun 16 15:35:35 polecat nm-system-settings:    SCPluginIfupdown: guessed connection type (eth0) = 802-3-ethernet
Jun 16 15:35:36 polecat nm-system-settings:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, autoconnect:0, id:Ifupdown (eth0), uuid: 681b428f-beaf-8932-0000-000000000000
Jun 16 15:35:36 polecat nm-system-settings:    SCPlugin-Ifupdown: autoconnect
Jun 16 15:35:36 polecat nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Jun 16 15:35:36 polecat nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00, iface: eth1): not well known
Jun 16 15:35:36 polecat nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_1e_ec_76_41_b2, iface: eth0): well known
Jun 16 15:35:36 polecat nm-system-settings:    Ifupdown: get unmanaged devices count: 1
Jun 16 15:35:36 polecat nm-system-settings:    SCPlugin-Ifupdown: (23663168) ... get_connections.
Jun 16 15:35:36 polecat nm-system-settings:    SCPlugin-Ifupdown: (23663168) ... get_connections (managed=false): return empty list.
Jun 16 15:35:36 polecat nm-system-settings:    Ifupdown: get unmanaged devices count: 1
Jun 16 15:35:36 polecat nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_21_5c_36_8d_6b, iface: wlan0): not well known
Jun 16 15:35:36 polecat nm-system-settings:    SCPlugin-Ifupdown: end _init.
Jun 16 15:35:36 polecat nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun 16 15:35:36 polecat nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun 16 15:35:36 polecat NetworkManager: <info>  (eth0): now unmanaged 
Jun 16 15:35:36 polecat NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle 
Jun 16 15:35:36 polecat avahi-daemon[4195]: Server startup complete. Host name is polecat.local. Local service cookie is 22039826.
================================================================

---

### Post by Iowan on 2009-06-16
Is there a reason you don't want Network Manager to handle the connection? I presume it didn't work? What happens if you comment out the eth0 entries in */etc/network/interfaces* and reboot? (I'd say restart... but dunno if it'd be networking, NetworkManager, or both)

---

