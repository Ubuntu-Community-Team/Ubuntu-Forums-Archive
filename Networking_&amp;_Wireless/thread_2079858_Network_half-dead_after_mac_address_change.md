---
title: "Network half-dead after mac address change"
date: 2012-11-02
forum: Networking &amp; Wireless
---

### Post by pvravi on 2012-11-02
Searched, but couldn't find anything. 

Running 12.04 

I change my mac address like so (the prescribed way): 

service network-manager stop
ifconfig eth0 hw ether XX:XX:XX:XX:XX:XX
service network-manager restart

After this change, this machine cannot access the external network. 
Weirdly enough, it gets a DHCP IP from my local intranet. 
Also weirdly enough I can ping this machine from another. But ping is not consistent 5 out of 10 fail with 'host unreachable' 
However on this machine, the network is dead. Pinging another live machine on the same subnet returns "Destination host unreachable", by IP. Pinging by name returns host unknown (or equivalent). 

If I revert the mac with no other change, the network is up and all is well again. 

It is as if that old mac is somewhere else as well and needs to be taken care of. 

Any help in this fixing this is greatly appreciated.  

TIA

---

### Post by pvravi on 2012-11-02
Logs with mac change and revert: 

The differences seem to be towards the bottom with ypbind. 

Mac change: 
```

test NetworkManager[27628]: <info> caught signal 15, shutting down normally.
test NetworkManager[27628]: <warn> quit request received, terminating...
test NetworkManager[27628]: <info> (eth0): now unmanaged
test NetworkManager[27628]: <info> (eth0): device state change: activated -> unmanaged (reason 'removed') [100 10 36]
test NetworkManager[27628]: <info> (eth0): deactivating device (reason 'removed') [36]
test NetworkManager[27628]: <info> (eth0): canceled DHCP transaction, DHCP client pid 27632
test avahi-daemon[778]: Withdrawing address record for 10.1.1.146 on eth0.
test avahi-daemon[778]: Leaving mDNS multicast group on interface eth0.IPv4 with address 10.1.1.146.
test avahi-daemon[778]: Interface eth0.IPv4 no longer relevant for mDNS.
test NetworkManager[27628]: <info> DNS: starting dnsmasq...
test dnsmasq[27641]: exiting on receipt of SIGTERM
test NetworkManager[27628]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
test dnsmasq[27859]: started, version 2.59 cache disabled
test dnsmasq[27859]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
test dnsmasq[27859]: warning: no upstream servers configured
test NetworkManager[27628]: <info> (eth0): cleaning up...
test NetworkManager[27628]: <info> (eth0): taking down device.
test NetworkManager[27628]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
test dbus[715]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
test dnsmasq[27859]: exiting on receipt of SIGTERM
test NetworkManager[27628]: <info> (eth0): removing resolv.conf from /sbin/resolvconf
test dbus[715]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
test NetworkManager[27628]: <info> exiting (success)
test modem-manager[27626]: <info>  Caught signal 15, shutting down...
test modem-manager[27932]: <info>  ModemManager (version 0.5.2.0) starting...
test modem-manager[27932]: <info>  Loaded plugin Option High-Speed
test modem-manager[27932]: <info>  Loaded plugin Gobi
test modem-manager[27932]: <info>  Loaded plugin Generic
test modem-manager[27932]: <info>  Loaded plugin Samsung
test modem-manager[27932]: <info>  Loaded plugin Ericsson MBM
test modem-manager[27932]: <info>  Loaded plugin Nokia
test modem-manager[27932]: <info>  Loaded plugin Huawei
test modem-manager[27932]: <info>  Loaded plugin X22X
test modem-manager[27932]: <info>  Loaded plugin AnyData
test modem-manager[27932]: <info>  Loaded plugin Wavecom
test modem-manager[27932]: <info>  Loaded plugin Novatel
test modem-manager[27932]: <info>  Loaded plugin MotoC
test modem-manager[27932]: <info>  Loaded plugin ZTE
test modem-manager[27932]: <info>  Loaded plugin Linktop
test modem-manager[27932]: <info>  Loaded plugin Option
test modem-manager[27932]: <info>  Loaded plugin Sierra
test modem-manager[27932]: <info>  Loaded plugin SimTech
test modem-manager[27932]: <info>  Loaded plugin Longcheer
test NetworkManager[27934]: <info> NetworkManager (version 0.9.4.0) is starting...
test NetworkManager[27934]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
test NetworkManager[27934]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
test NetworkManager[27934]: <info> DNS: loaded plugin dnsmasq
test NetworkManager[27934]:    SCPlugin-Ifupdown: init!
test NetworkManager[27934]:    SCPlugin-Ifupdown: update_system_hostname
test NetworkManager[27934]:    SCPluginIfupdown: management mode: unmanaged
test NetworkManager[27934]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:02.0/0000:02:1d.0/0000:03:0e.0/net/eth0, iface: eth0)
test NetworkManager[27934]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:02.0/0000:02:1d.0/0000:03:0e.0/net/eth0, iface: eth0): no ifupdown configuration found.
test NetworkManager[27934]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
test NetworkManager[27934]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
test NetworkManager[27934]:    SCPlugin-Ifupdown: end _init.
test NetworkManager[27934]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
test NetworkManager[27934]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
test NetworkManager[27934]:    Ifupdown: get unmanaged devices count: 0
test NetworkManager[27934]:    SCPlugin-Ifupdown: (167797832) ... get_connections.
test NetworkManager[27934]:    SCPlugin-Ifupdown: (167797832) ... get_connections (managed=false): return empty list.
test NetworkManager[27934]:    keyfile: parsing Wired connection 1 ... 
test NetworkManager[27934]:    keyfile:     read connection 'Wired connection 1'
test NetworkManager[27934]:    Ifupdown: get unmanaged devices count: 0
test NetworkManager[27934]: <info> modem-manager is now available
test NetworkManager[27934]: <info> monitoring kernel firmware directory '/lib/firmware'.
test NetworkManager[27934]: <info> WiFi enabled by radio killswitch; enabled by state file
test NetworkManager[27934]: <info> WWAN enabled by radio killswitch; enabled by state file
test NetworkManager[27934]: <info> WiMAX enabled by radio killswitch; enabled by state file
test NetworkManager[27934]: <info> Networking is enabled by state file
test NetworkManager[27934]: <warn> failed to allocate link cache: (-10) Operation not supported
test NetworkManager[27934]: <info> (eth0): carrier is OFF
test NetworkManager[27934]: <info> (eth0): new Ethernet device (driver: 'e1000' ifindex: 2)
test NetworkManager[27934]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
test NetworkManager[27934]: <info> (eth0): now managed
test NetworkManager[27934]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
test NetworkManager[27934]: <info> (eth0): bringing up device.
test NetworkManager[27934]: <info> (eth0): preparing device.
test NetworkManager[27934]: <info> (eth0): deactivating device (reason 'managed') [2]
test kernel: [148362.292352] ADDRCONF(NETDEV_UP): eth0: link is not ready
test ypbind[27243]: broadcast: RPC: Timed out.
test NetworkManager[27934]: <info> (eth0): carrier now ON (device state 20)
test NetworkManager[27934]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
test NetworkManager[27934]: <info> Auto-activating connection 'Wired connection 1'.
test NetworkManager[27934]: <info> Activation (eth0) starting connection 'Wired connection 1'
test NetworkManager[27934]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
test NetworkManager[27934]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
test NetworkManager[27934]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
test NetworkManager[27934]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
test NetworkManager[27934]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
test NetworkManager[27934]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
test NetworkManager[27934]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
test NetworkManager[27934]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
test NetworkManager[27934]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
test NetworkManager[27934]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
test kernel: [148364.296383] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
test kernel: [148364.296625] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
test NetworkManager[27934]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
test NetworkManager[27934]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
test NetworkManager[27934]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
test NetworkManager[27934]: <info> dhclient started with pid 27938
test NetworkManager[27934]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
test dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
test dhclient: Copyright 2004-2011 Internet Systems Consortium.
test dhclient: All rights reserved.
test dhclient: For info, please visit https://www.isc.org/software/dhcp/
test dhclient: 
test NetworkManager[27934]: <info> (eth0): DHCPv4 state changed nbi -> preinit
test dhclient: Listening on LPF/eth0/f0:4d:a2:08:34:0c
test dhclient: Sending on   LPF/eth0/f0:4d:a2:08:34:0c
test dhclient: Sending on   Socket/fallback
test dhclient: DHCPREQUEST of 10.1.1.146 on eth0 to 255.255.255.255 port 67
test dhclient: DHCPNAK from 10.1.1.10
test NetworkManager[27934]: <info> (eth0): DHCPv4 state changed preinit -> expire
test dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
test NetworkManager[27934]: <info> (eth0): DHCPv4 state changed expire -> preinit
test dhclient: DHCPREQUEST of 10.1.1.134 on eth0 to 255.255.255.255 port 67
test dhclient: DHCPOFFER of 10.1.1.134 from 10.1.1.10
test dhclient: DHCPACK of 10.1.1.134 from 10.1.1.10
test dhclient: bound to 10.1.1.134 -- renewal in 297504 seconds.
test NetworkManager[27934]: <info> (eth0): DHCPv4 state changed preinit -> bound
test NetworkManager[27934]: <info>   address 10.1.1.134
test NetworkManager[27934]: <info>   prefix 24 (255.255.255.0)
test NetworkManager[27934]: <info>   gateway 10.1.1.1
test NetworkManager[27934]: <info>   nameserver '10.1.1.10'
test NetworkManager[27934]: <info>   domain name 'koolchip.local'
test NetworkManager[27934]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
test NetworkManager[27934]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
test avahi-daemon[778]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.1.1.134.
test avahi-daemon[778]: New relevant interface eth0.IPv4 for mDNS.
test avahi-daemon[778]: Registering new address record for 10.1.1.134 on eth0.IPv4.
test NetworkManager[27934]: <info> DNS: starting dnsmasq...
test NetworkManager[27934]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
test dnsmasq[27945]: started, version 2.59 cache disabled
test dnsmasq[27945]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
test dnsmasq[27945]: using nameserver 10.1.1.10#53
test NetworkManager[27934]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
test NetworkManager[27934]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
test NetworkManager[27934]: <info> Activation (eth0) successful, device activated.
test NetworkManager[27934]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
test dbus[715]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
test dbus[715]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
test ypbind[27243]: broadcast: RPC: Timed out.
test ntpdate[28016]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
test ntpdate[28016]: no servers can be used, exiting
test ypbind[27243]: broadcast: RPC: Timed out.
```


Mac Revert: 
```

test NetworkManager[27934]: <info> caught signal 15, shutting down normally.
test NetworkManager[27934]: <warn> quit request received, terminating...
test NetworkManager[27934]: <info> (eth0): now unmanaged
test NetworkManager[27934]: <info> (eth0): device state change: activated -> unmanaged (reason 'removed') [100 10 36]
test NetworkManager[27934]: <info> (eth0): deactivating device (reason 'removed') [36]
test NetworkManager[27934]: <info> (eth0): canceled DHCP transaction, DHCP client pid 27938
test avahi-daemon[778]: Withdrawing address record for 10.1.1.134 on eth0.
test avahi-daemon[778]: Leaving mDNS multicast group on interface eth0.IPv4 with address 10.1.1.134.
test avahi-daemon[778]: Interface eth0.IPv4 no longer relevant for mDNS.
test dnsmasq[27945]: exiting on receipt of SIGTERM
test NetworkManager[27934]: <info> DNS: starting dnsmasq...
test NetworkManager[27934]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
test dnsmasq[28052]: started, version 2.59 cache disabled
test dnsmasq[28052]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
test dnsmasq[28052]: warning: no upstream servers configured
test NetworkManager[27934]: <info> (eth0): cleaning up...
test NetworkManager[27934]: <info> (eth0): taking down device.
test NetworkManager[27934]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
test dbus[715]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
test dnsmasq[28052]: exiting on receipt of SIGTERM
test NetworkManager[27934]: <info> (eth0): removing resolv.conf from /sbin/resolvconf
test dbus[715]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
test NetworkManager[27934]: <info> exiting (success)
test modem-manager[27932]: <info>  Caught signal 15, shutting down...
test modem-manager[28125]: <info>  ModemManager (version 0.5.2.0) starting...
test modem-manager[28125]: <info>  Loaded plugin Option High-Speed
test modem-manager[28125]: <info>  Loaded plugin Gobi
test modem-manager[28125]: <info>  Loaded plugin Generic
test modem-manager[28125]: <info>  Loaded plugin Samsung
test NetworkManager[28127]: <info> NetworkManager (version 0.9.4.0) is starting...
test NetworkManager[28127]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
test modem-manager[28125]: <info>  Loaded plugin Ericsson MBM
test modem-manager[28125]: <info>  Loaded plugin Nokia
test modem-manager[28125]: <info>  Loaded plugin Huawei
test modem-manager[28125]: <info>  Loaded plugin X22X
test modem-manager[28125]: <info>  Loaded plugin AnyData
test modem-manager[28125]: <info>  Loaded plugin Wavecom
test modem-manager[28125]: <info>  Loaded plugin Novatel
test modem-manager[28125]: <info>  Loaded plugin MotoC
test modem-manager[28125]: <info>  Loaded plugin ZTE
test modem-manager[28125]: <info>  Loaded plugin Linktop
test modem-manager[28125]: <info>  Loaded plugin Option
test NetworkManager[28127]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
test modem-manager[28125]: <info>  Loaded plugin Sierra
test NetworkManager[28127]: <info> DNS: loaded plugin dnsmasq
test modem-manager[28125]: <info>  Loaded plugin SimTech
test modem-manager[28125]: <info>  Loaded plugin Longcheer
test NetworkManager[28127]:    SCPlugin-Ifupdown: init!
test NetworkManager[28127]:    SCPlugin-Ifupdown: update_system_hostname
test NetworkManager[28127]:    SCPluginIfupdown: management mode: unmanaged
test NetworkManager[28127]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:02.0/0000:02:1d.0/0000:03:0e.0/net/eth0, iface: eth0)
test NetworkManager[28127]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:02.0/0000:02:1d.0/0000:03:0e.0/net/eth0, iface: eth0): no ifupdown configuration found.
test NetworkManager[28127]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
test NetworkManager[28127]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
test NetworkManager[28127]:    SCPlugin-Ifupdown: end _init.
test NetworkManager[28127]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
test NetworkManager[28127]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
test NetworkManager[28127]:    Ifupdown: get unmanaged devices count: 0
test NetworkManager[28127]:    SCPlugin-Ifupdown: (164451912) ... get_connections.
test NetworkManager[28127]:    SCPlugin-Ifupdown: (164451912) ... get_connections (managed=false): return empty list.
test NetworkManager[28127]:    keyfile: parsing Wired connection 1 ... 
test NetworkManager[28127]:    keyfile:     read connection 'Wired connection 1'
test NetworkManager[28127]:    Ifupdown: get unmanaged devices count: 0
test NetworkManager[28127]: <info> modem-manager is now available
test NetworkManager[28127]: <info> monitoring kernel firmware directory '/lib/firmware'.
test NetworkManager[28127]: <info> WiFi enabled by radio killswitch; enabled by state file
test NetworkManager[28127]: <info> WWAN enabled by radio killswitch; enabled by state file
test NetworkManager[28127]: <info> WiMAX enabled by radio killswitch; enabled by state file
test NetworkManager[28127]: <info> Networking is enabled by state file
test NetworkManager[28127]: <warn> failed to allocate link cache: (-10) Operation not supported
test NetworkManager[28127]: <info> (eth0): carrier is OFF
test NetworkManager[28127]: <info> (eth0): new Ethernet device (driver: 'e1000' ifindex: 2)
test NetworkManager[28127]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
test NetworkManager[28127]: <info> (eth0): now managed
test NetworkManager[28127]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
test NetworkManager[28127]: <info> (eth0): bringing up device.
test NetworkManager[28127]: <info> (eth0): preparing device.
test NetworkManager[28127]: <info> (eth0): deactivating device (reason 'managed') [2]
test kernel: [148489.448141] ADDRCONF(NETDEV_UP): eth0: link is not ready
test ypbind[27243]: broadcast: RPC: Unable to send.
test NetworkManager[28127]: <info> (eth0): carrier now ON (device state 20)
test NetworkManager[28127]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
test kernel: [148491.452390] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
test kernel: [148491.452632] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
test NetworkManager[28127]: <info> Auto-activating connection 'Wired connection 1'.
test NetworkManager[28127]: <info> Activation (eth0) starting connection 'Wired connection 1'
test NetworkManager[28127]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
test NetworkManager[28127]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
test NetworkManager[28127]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
test NetworkManager[28127]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
test NetworkManager[28127]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
test NetworkManager[28127]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
test NetworkManager[28127]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
test NetworkManager[28127]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
test NetworkManager[28127]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
test NetworkManager[28127]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
test NetworkManager[28127]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
test NetworkManager[28127]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
test NetworkManager[28127]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
test NetworkManager[28127]: <info> dhclient started with pid 28131
test dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
test dhclient: Copyright 2004-2011 Internet Systems Consortium.
test dhclient: All rights reserved.
test dhclient: For info, please visit https://www.isc.org/software/dhcp/
test dhclient: 
test NetworkManager[28127]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
test NetworkManager[28127]: <info> (eth0): DHCPv4 state changed nbi -> preinit
test dhclient: Listening on LPF/eth0/00:0d:56:c7:cc:19
test dhclient: Sending on   LPF/eth0/00:0d:56:c7:cc:19
test dhclient: Sending on   Socket/fallback
test dhclient: DHCPREQUEST of 10.1.1.134 on eth0 to 255.255.255.255 port 67
test dhclient: DHCPNAK from 10.1.1.10
test NetworkManager[28127]: <info> (eth0): DHCPv4 state changed preinit -> expire
test dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
test NetworkManager[28127]: <info> (eth0): DHCPv4 state changed expire -> preinit
test dhclient: DHCPREQUEST of 10.1.1.146 on eth0 to 255.255.255.255 port 67
test dhclient: DHCPOFFER of 10.1.1.146 from 10.1.1.10
test dhclient: DHCPACK of 10.1.1.146 from 10.1.1.10
test dhclient: bound to 10.1.1.146 -- renewal in 294315 seconds.
test NetworkManager[28127]: <info> (eth0): DHCPv4 state changed preinit -> bound
test NetworkManager[28127]: <info>   address 10.1.1.146
test NetworkManager[28127]: <info>   prefix 24 (255.255.255.0)
test NetworkManager[28127]: <info>   gateway 10.1.1.1
test NetworkManager[28127]: <info>   nameserver '10.1.1.10'
test NetworkManager[28127]: <info>   domain name 'koolchip.local'
test NetworkManager[28127]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
test NetworkManager[28127]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
test avahi-daemon[778]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.1.1.146.
test avahi-daemon[778]: New relevant interface eth0.IPv4 for mDNS.
test avahi-daemon[778]: Registering new address record for 10.1.1.146 on eth0.IPv4.
test NetworkManager[28127]: <info> DNS: starting dnsmasq...
test NetworkManager[28127]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
test dnsmasq[28138]: started, version 2.59 cache disabled
test dnsmasq[28138]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
test dnsmasq[28138]: using nameserver 10.1.1.10#53
test NetworkManager[28127]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
test NetworkManager[28127]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
test NetworkManager[28127]: <info> Activation (eth0) successful, device activated.
test NetworkManager[28127]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
test ntpdate[28204]: adjust time server 91.189.94.4 offset 0.031426 sec
```

---

