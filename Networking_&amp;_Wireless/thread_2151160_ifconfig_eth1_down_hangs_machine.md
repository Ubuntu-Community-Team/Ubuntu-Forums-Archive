---
title: "ifconfig eth1 down hangs machine"
date: 2013-06-03
forum: Networking &amp; Wireless
---

### Post by sanosuke001 on 2013-06-03
I tried to search for similar issue but didn't find anything; if there's another thread somewhere I apologize.

So, I am writing an application where I need to support socket disconnects so I was planning on disconnecting my network adapter via "ifconfig eth1 down" but when I do so, the system hangs. Attached is my syslog from the disconnect request to my system interrupt (which rebooted the system). I don't see anything that would cause my system to hang (mouse still moves but all UI objects are unresponsive). I'm not new to linux but by no means an expert (I know there's a log file I should be looking at or a way to determine if it's just gnome that's crashed).

Any help would be appreciated; thanks!

System is running Ubuntu 13.04 with Gnome 3

[HTML]
<pre>
Jun  3 14:17:01 HOSTNAME CRON[10493]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun  3 14:17:23 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: activated -> disconnected (reason 'user-requested') [100 30 39]
Jun  3 14:17:23 HOSTNAME NetworkManager[1780]: <info> (eth1): deactivating device (reason 'user-requested') [39]
Jun  3 14:17:23 HOSTNAME avahi-daemon[1777]: Withdrawing address record for fe80::e2cb:4eff:feab:26d3 on eth1.
Jun  3 14:17:23 HOSTNAME avahi-daemon[1777]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::e2cb:4eff:feab:26d3.
Jun  3 14:17:23 HOSTNAME avahi-daemon[1777]: Interface eth1.IPv6 no longer relevant for mDNS.
Jun  3 14:17:23 HOSTNAME avahi-daemon[1777]: Withdrawing address record for 192.168.12.12 on eth1.
Jun  3 14:17:23 HOSTNAME avahi-daemon[1777]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.12.12.
Jun  3 14:17:23 HOSTNAME avahi-daemon[1777]: Interface eth1.IPv4 no longer relevant for mDNS.
Jun  3 14:17:23 HOSTNAME NetworkManager[1780]: <warn> DNS: plugin dnsmasq update failed
Jun  3 14:17:23 HOSTNAME NetworkManager[1780]: <info> Removing DNS information from /sbin/resolvconf
Jun  3 14:17:23 HOSTNAME dnsmasq[3302]: setting upstream servers from DBus
Jun  3 14:17:23 HOSTNAME dbus[1707]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun  3 14:17:23 HOSTNAME NetworkManager[1780]: <info> Auto-activating connection 'Wired connection 2'.
Jun  3 14:17:23 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) starting connection 'Wired connection 2'
Jun  3 14:17:23 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun  3 14:17:23 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jun  3 14:17:23 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Jun  3 14:17:23 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jun  3 14:17:23 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jun  3 14:17:23 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jun  3 14:17:23 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Jun  3 14:17:23 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Jun  3 14:17:23 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  3 14:17:23 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jun  3 14:17:23 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Jun  3 14:17:23 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun  3 14:17:23 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun  3 14:17:23 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Beginning IP6 addrconf.
Jun  3 14:17:23 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Jun  3 14:17:23 HOSTNAME dbus[1707]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun  3 14:17:23 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) started...
Jun  3 14:17:23 HOSTNAME avahi-daemon[1777]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.12.12.
Jun  3 14:17:23 HOSTNAME avahi-daemon[1777]: New relevant interface eth1.IPv4 for mDNS.
Jun  3 14:17:23 HOSTNAME avahi-daemon[1777]: Registering new address record for 192.168.12.12 on eth1.IPv4.
Jun  3 14:17:24 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jun  3 14:17:24 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) complete.
Jun  3 14:17:24 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jun  3 14:17:24 HOSTNAME NetworkManager[1780]: <info> Policy set 'Wired connection 2' (eth1) as default for IPv4 routing and DNS.
Jun  3 14:17:24 HOSTNAME NetworkManager[1780]: <info> Writing DNS information to /sbin/resolvconf
Jun  3 14:17:24 HOSTNAME dnsmasq[3302]: setting upstream servers from DBus
Jun  3 14:17:24 HOSTNAME dnsmasq[3302]: using nameserver 192.168.129.9#53
Jun  3 14:17:24 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) successful, device activated.
Jun  3 14:17:25 HOSTNAME avahi-daemon[1777]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::e2cb:4eff:feab:26d3.
Jun  3 14:17:25 HOSTNAME avahi-daemon[1777]: New relevant interface eth1.IPv6 for mDNS.
Jun  3 14:17:25 HOSTNAME avahi-daemon[1777]: Registering new address record for fe80::e2cb:4eff:feab:26d3 on eth1.*.
Jun  3 14:17:28 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: activated -> disconnected (reason 'user-requested') [100 30 39]
Jun  3 14:17:28 HOSTNAME NetworkManager[1780]: <info> (eth1): deactivating device (reason 'user-requested') [39]
Jun  3 14:17:28 HOSTNAME avahi-daemon[1777]: Withdrawing address record for fe80::e2cb:4eff:feab:26d3 on eth1.
Jun  3 14:17:28 HOSTNAME avahi-daemon[1777]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::e2cb:4eff:feab:26d3.
Jun  3 14:17:28 HOSTNAME avahi-daemon[1777]: Interface eth1.IPv6 no longer relevant for mDNS.
Jun  3 14:17:28 HOSTNAME avahi-daemon[1777]: Withdrawing address record for 192.168.12.12 on eth1.
Jun  3 14:17:28 HOSTNAME avahi-daemon[1777]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.12.12.
Jun  3 14:17:28 HOSTNAME avahi-daemon[1777]: Interface eth1.IPv4 no longer relevant for mDNS.
Jun  3 14:17:28 HOSTNAME NetworkManager[1780]: <warn> DNS: plugin dnsmasq update failed
Jun  3 14:17:28 HOSTNAME NetworkManager[1780]: <info> Removing DNS information from /sbin/resolvconf
Jun  3 14:17:28 HOSTNAME dnsmasq[3302]: setting upstream servers from DBus
Jun  3 14:17:28 HOSTNAME NetworkManager[1780]: <info> Auto-activating connection 'Wired connection 2'.
Jun  3 14:17:28 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) starting connection 'Wired connection 2'
Jun  3 14:17:28 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun  3 14:17:28 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jun  3 14:17:28 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Jun  3 14:17:28 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jun  3 14:17:28 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jun  3 14:17:28 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jun  3 14:17:28 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Jun  3 14:17:28 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Jun  3 14:17:28 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  3 14:17:28 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jun  3 14:17:28 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Jun  3 14:17:28 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun  3 14:17:28 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun  3 14:17:28 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Beginning IP6 addrconf.
Jun  3 14:17:28 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Jun  3 14:17:28 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) started...
Jun  3 14:17:28 HOSTNAME avahi-daemon[1777]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.12.12.
Jun  3 14:17:28 HOSTNAME avahi-daemon[1777]: New relevant interface eth1.IPv4 for mDNS.
Jun  3 14:17:28 HOSTNAME avahi-daemon[1777]: Registering new address record for 192.168.12.12 on eth1.IPv4.
Jun  3 14:17:28 HOSTNAME ntpdate[10621]: sendto(91.189.94.4): Connection timed out
Jun  3 14:17:29 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jun  3 14:17:29 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) complete.
Jun  3 14:17:29 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jun  3 14:17:29 HOSTNAME NetworkManager[1780]: <info> Policy set 'Wired connection 2' (eth1) as default for IPv4 routing and DNS.
Jun  3 14:17:29 HOSTNAME NetworkManager[1780]: <info> Writing DNS information to /sbin/resolvconf
Jun  3 14:17:29 HOSTNAME dnsmasq[3302]: setting upstream servers from DBus
Jun  3 14:17:29 HOSTNAME dnsmasq[3302]: using nameserver 192.168.129.9#53
Jun  3 14:17:29 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) successful, device activated.
Jun  3 14:17:30 HOSTNAME avahi-daemon[1777]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::e2cb:4eff:feab:26d3.
Jun  3 14:17:30 HOSTNAME avahi-daemon[1777]: New relevant interface eth1.IPv6 for mDNS.
Jun  3 14:17:30 HOSTNAME avahi-daemon[1777]: Registering new address record for fe80::e2cb:4eff:feab:26d3 on eth1.*.
Jun  3 14:17:31 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: activated -> disconnected (reason 'user-requested') [100 30 39]
Jun  3 14:17:31 HOSTNAME NetworkManager[1780]: <info> (eth1): deactivating device (reason 'user-requested') [39]
Jun  3 14:17:31 HOSTNAME avahi-daemon[1777]: Withdrawing address record for fe80::e2cb:4eff:feab:26d3 on eth1.
Jun  3 14:17:31 HOSTNAME avahi-daemon[1777]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::e2cb:4eff:feab:26d3.
Jun  3 14:17:31 HOSTNAME avahi-daemon[1777]: Interface eth1.IPv6 no longer relevant for mDNS.
Jun  3 14:17:31 HOSTNAME avahi-daemon[1777]: Withdrawing address record for 192.168.12.12 on eth1.
Jun  3 14:17:31 HOSTNAME avahi-daemon[1777]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.12.12.
Jun  3 14:17:31 HOSTNAME avahi-daemon[1777]: Interface eth1.IPv4 no longer relevant for mDNS.
Jun  3 14:17:31 HOSTNAME NetworkManager[1780]: <warn> DNS: plugin dnsmasq update failed
Jun  3 14:17:31 HOSTNAME NetworkManager[1780]: <info> Removing DNS information from /sbin/resolvconf
Jun  3 14:17:31 HOSTNAME dnsmasq[3302]: setting upstream servers from DBus
Jun  3 14:17:31 HOSTNAME NetworkManager[1780]: <info> Auto-activating connection 'Wired connection 2'.
Jun  3 14:17:31 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) starting connection 'Wired connection 2'
Jun  3 14:17:31 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun  3 14:17:31 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jun  3 14:17:31 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Jun  3 14:17:31 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jun  3 14:17:31 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jun  3 14:17:31 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jun  3 14:17:31 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Jun  3 14:17:31 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Jun  3 14:17:31 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  3 14:17:31 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jun  3 14:17:31 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Jun  3 14:17:31 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun  3 14:17:31 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun  3 14:17:31 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Beginning IP6 addrconf.
Jun  3 14:17:31 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Jun  3 14:17:31 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) started...
Jun  3 14:17:31 HOSTNAME avahi-daemon[1777]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.12.12.
Jun  3 14:17:31 HOSTNAME avahi-daemon[1777]: New relevant interface eth1.IPv4 for mDNS.
Jun  3 14:17:31 HOSTNAME avahi-daemon[1777]: Registering new address record for 192.168.12.12 on eth1.IPv4.
Jun  3 14:17:32 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jun  3 14:17:32 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) complete.
Jun  3 14:17:32 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jun  3 14:17:32 HOSTNAME NetworkManager[1780]: <info> Policy set 'Wired connection 2' (eth1) as default for IPv4 routing and DNS.
Jun  3 14:17:32 HOSTNAME NetworkManager[1780]: <info> Writing DNS information to /sbin/resolvconf
Jun  3 14:17:32 HOSTNAME dnsmasq[3302]: setting upstream servers from DBus
Jun  3 14:17:32 HOSTNAME dnsmasq[3302]: using nameserver 192.168.129.9#53
Jun  3 14:17:32 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) successful, device activated.
Jun  3 14:17:32 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: activated -> disconnected (reason 'user-requested') [100 30 39]
Jun  3 14:17:32 HOSTNAME NetworkManager[1780]: <info> (eth1): deactivating device (reason 'user-requested') [39]
Jun  3 14:17:32 HOSTNAME avahi-daemon[1777]: Withdrawing address record for 192.168.12.12 on eth1.
Jun  3 14:17:32 HOSTNAME avahi-daemon[1777]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.12.12.
Jun  3 14:17:32 HOSTNAME avahi-daemon[1777]: Interface eth1.IPv4 no longer relevant for mDNS.
Jun  3 14:17:32 HOSTNAME NetworkManager[1780]: <warn> DNS: plugin dnsmasq update failed
Jun  3 14:17:32 HOSTNAME NetworkManager[1780]: <info> Removing DNS information from /sbin/resolvconf
Jun  3 14:17:32 HOSTNAME dnsmasq[3302]: setting upstream servers from DBus
Jun  3 14:17:32 HOSTNAME NetworkManager[1780]: <info> Auto-activating connection 'Wired connection 2'.
Jun  3 14:17:32 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) starting connection 'Wired connection 2'
Jun  3 14:17:32 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun  3 14:17:32 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jun  3 14:17:32 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Jun  3 14:17:32 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jun  3 14:17:32 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jun  3 14:17:32 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jun  3 14:17:32 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Jun  3 14:17:32 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Jun  3 14:17:32 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  3 14:17:32 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jun  3 14:17:32 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Jun  3 14:17:32 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun  3 14:17:32 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun  3 14:17:32 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Beginning IP6 addrconf.
Jun  3 14:17:32 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Jun  3 14:17:32 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) started...
Jun  3 14:17:32 HOSTNAME avahi-daemon[1777]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.12.12.
Jun  3 14:17:32 HOSTNAME avahi-daemon[1777]: New relevant interface eth1.IPv4 for mDNS.
Jun  3 14:17:32 HOSTNAME avahi-daemon[1777]: Registering new address record for 192.168.12.12 on eth1.IPv4.
Jun  3 14:17:32 HOSTNAME ntpdate[10621]: no server suitable for synchronization found
Jun  3 14:17:33 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jun  3 14:17:33 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) complete.
Jun  3 14:17:33 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jun  3 14:17:33 HOSTNAME NetworkManager[1780]: <info> Policy set 'Wired connection 2' (eth1) as default for IPv4 routing and DNS.
Jun  3 14:17:33 HOSTNAME NetworkManager[1780]: <info> Writing DNS information to /sbin/resolvconf
Jun  3 14:17:33 HOSTNAME dnsmasq[3302]: setting upstream servers from DBus
Jun  3 14:17:33 HOSTNAME dnsmasq[3302]: using nameserver 192.168.129.9#53
Jun  3 14:17:33 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) successful, device activated.
Jun  3 14:17:33 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: activated -> disconnected (reason 'user-requested') [100 30 39]
Jun  3 14:17:33 HOSTNAME NetworkManager[1780]: <info> (eth1): deactivating device (reason 'user-requested') [39]
Jun  3 14:17:33 HOSTNAME avahi-daemon[1777]: Withdrawing address record for 192.168.12.12 on eth1.
Jun  3 14:17:33 HOSTNAME avahi-daemon[1777]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.12.12.
Jun  3 14:17:33 HOSTNAME avahi-daemon[1777]: Interface eth1.IPv4 no longer relevant for mDNS.
Jun  3 14:17:33 HOSTNAME NetworkManager[1780]: <warn> DNS: plugin dnsmasq update failed
Jun  3 14:17:33 HOSTNAME NetworkManager[1780]: <info> Removing DNS information from /sbin/resolvconf
Jun  3 14:17:33 HOSTNAME dnsmasq[3302]: setting upstream servers from DBus
Jun  3 14:17:33 HOSTNAME NetworkManager[1780]: <info> Auto-activating connection 'Wired connection 2'.
Jun  3 14:17:33 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) starting connection 'Wired connection 2'
Jun  3 14:17:33 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun  3 14:17:33 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jun  3 14:17:33 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Jun  3 14:17:33 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jun  3 14:17:33 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jun  3 14:17:33 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jun  3 14:17:33 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Jun  3 14:17:33 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Jun  3 14:17:33 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  3 14:17:33 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jun  3 14:17:33 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Jun  3 14:17:33 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun  3 14:17:33 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun  3 14:17:33 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Beginning IP6 addrconf.
Jun  3 14:17:33 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Jun  3 14:17:33 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) started...
Jun  3 14:17:33 HOSTNAME avahi-daemon[1777]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.12.12.
Jun  3 14:17:33 HOSTNAME avahi-daemon[1777]: New relevant interface eth1.IPv4 for mDNS.
Jun  3 14:17:33 HOSTNAME avahi-daemon[1777]: Registering new address record for 192.168.12.12 on eth1.IPv4.
Jun  3 14:17:34 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jun  3 14:17:34 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) complete.
Jun  3 14:17:34 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jun  3 14:17:34 HOSTNAME NetworkManager[1780]: <info> Policy set 'Wired connection 2' (eth1) as default for IPv4 routing and DNS.
Jun  3 14:17:34 HOSTNAME NetworkManager[1780]: <info> Writing DNS information to /sbin/resolvconf
Jun  3 14:17:34 HOSTNAME dnsmasq[3302]: setting upstream servers from DBus
Jun  3 14:17:34 HOSTNAME dnsmasq[3302]: using nameserver 192.168.129.9#53
Jun  3 14:17:34 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) successful, device activated.
Jun  3 14:17:35 HOSTNAME avahi-daemon[1777]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::e2cb:4eff:feab:26d3.
Jun  3 14:17:35 HOSTNAME avahi-daemon[1777]: New relevant interface eth1.IPv6 for mDNS.
Jun  3 14:17:35 HOSTNAME avahi-daemon[1777]: Registering new address record for fe80::e2cb:4eff:feab:26d3 on eth1.*.
Jun  3 14:17:41 HOSTNAME ntpdate[10957]: no server suitable for synchronization found
Jun  3 14:17:52 HOSTNAME ntpdate[11089]: no server suitable for synchronization found
Jun  3 14:17:53 HOSTNAME NetworkManager[1780]: <info> (eth1): IP6 addrconf timed out or failed.
Jun  3 14:17:53 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jun  3 14:17:53 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jun  3 14:17:53 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jun  3 14:17:59 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: activated -> disconnected (reason 'user-requested') [100 30 39]
Jun  3 14:17:59 HOSTNAME NetworkManager[1780]: <info> (eth1): deactivating device (reason 'user-requested') [39]
Jun  3 14:17:59 HOSTNAME avahi-daemon[1777]: Withdrawing address record for fe80::e2cb:4eff:feab:26d3 on eth1.
Jun  3 14:17:59 HOSTNAME avahi-daemon[1777]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::e2cb:4eff:feab:26d3.
Jun  3 14:17:59 HOSTNAME avahi-daemon[1777]: Interface eth1.IPv6 no longer relevant for mDNS.
Jun  3 14:17:59 HOSTNAME avahi-daemon[1777]: Withdrawing address record for 192.168.12.12 on eth1.
Jun  3 14:17:59 HOSTNAME avahi-daemon[1777]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.12.12.
Jun  3 14:17:59 HOSTNAME avahi-daemon[1777]: Interface eth1.IPv4 no longer relevant for mDNS.
Jun  3 14:17:59 HOSTNAME NetworkManager[1780]: <warn> DNS: plugin dnsmasq update failed
Jun  3 14:17:59 HOSTNAME NetworkManager[1780]: <info> Removing DNS information from /sbin/resolvconf
Jun  3 14:17:59 HOSTNAME dnsmasq[3302]: setting upstream servers from DBus
Jun  3 14:17:59 HOSTNAME dbus[1707]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun  3 14:17:59 HOSTNAME NetworkManager[1780]: <info> Auto-activating connection 'Wired connection 2'.
Jun  3 14:17:59 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) starting connection 'Wired connection 2'
Jun  3 14:17:59 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun  3 14:17:59 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jun  3 14:17:59 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Jun  3 14:17:59 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jun  3 14:17:59 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jun  3 14:17:59 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jun  3 14:17:59 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Jun  3 14:17:59 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Jun  3 14:17:59 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  3 14:17:59 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jun  3 14:17:59 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Jun  3 14:17:59 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun  3 14:17:59 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun  3 14:17:59 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Beginning IP6 addrconf.
Jun  3 14:17:59 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Jun  3 14:17:59 HOSTNAME dbus[1707]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun  3 14:17:59 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) started...
Jun  3 14:17:59 HOSTNAME avahi-daemon[1777]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.12.12.
Jun  3 14:17:59 HOSTNAME avahi-daemon[1777]: New relevant interface eth1.IPv4 for mDNS.
Jun  3 14:17:59 HOSTNAME avahi-daemon[1777]: Registering new address record for 192.168.12.12 on eth1.IPv4.
Jun  3 14:18:00 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jun  3 14:18:00 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) complete.
Jun  3 14:18:00 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jun  3 14:18:00 HOSTNAME NetworkManager[1780]: <info> Policy set 'Wired connection 2' (eth1) as default for IPv4 routing and DNS.
Jun  3 14:18:00 HOSTNAME NetworkManager[1780]: <info> Writing DNS information to /sbin/resolvconf
Jun  3 14:18:00 HOSTNAME dnsmasq[3302]: setting upstream servers from DBus
Jun  3 14:18:00 HOSTNAME dnsmasq[3302]: using nameserver 192.168.129.9#53
Jun  3 14:18:00 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) successful, device activated.
Jun  3 14:18:01 HOSTNAME avahi-daemon[1777]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::e2cb:4eff:feab:26d3.
Jun  3 14:18:01 HOSTNAME avahi-daemon[1777]: New relevant interface eth1.IPv6 for mDNS.
Jun  3 14:18:01 HOSTNAME avahi-daemon[1777]: Registering new address record for fe80::e2cb:4eff:feab:26d3 on eth1.*.
Jun  3 14:18:08 HOSTNAME ntpdate[11210]: no server suitable for synchronization found
Jun  3 14:18:19 HOSTNAME NetworkManager[1780]: <info> (eth1): IP6 addrconf timed out or failed.
Jun  3 14:18:19 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jun  3 14:18:19 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jun  3 14:18:19 HOSTNAME NetworkManager[1780]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jun  3 14:18:30 HOSTNAME ntpdate[11248]: no server suitable for synchronization found
Jun  3 14:18:58 HOSTNAME ntpdate[11321]: no server suitable for synchronization found
Jun  3 14:19:17 HOSTNAME kernel: [ 5441.008678] device eth1 left promiscuous mode
Jun  3 14:19:17 HOSTNAME avahi-daemon[1777]: Interface eth1.IPv6 no longer relevant for mDNS.
Jun  3 14:19:17 HOSTNAME NetworkManager[1780]: <info> (eth1): carrier now OFF (device state 100, deferring action for 4 seconds)
Jun  3 14:19:17 HOSTNAME avahi-daemon[1777]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::e2cb:4eff:feab:26d3.
Jun  3 14:19:17 HOSTNAME avahi-daemon[1777]: Interface eth1.IPv4 no longer relevant for mDNS.
Jun  3 14:19:17 HOSTNAME avahi-daemon[1777]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.12.12.
Jun  3 14:19:17 HOSTNAME avahi-daemon[1777]: Withdrawing address record for fe80::e2cb:4eff:feab:26d3 on eth1.
Jun  3 14:19:17 HOSTNAME avahi-daemon[1777]: Withdrawing address record for 192.168.12.12 on eth1.
Jun  3 14:19:21 HOSTNAME NetworkManager[1780]: <info> (eth1): device state change: activated -> unavailable (reason 'carrier-changed') [100 20 40]
Jun  3 14:19:21 HOSTNAME NetworkManager[1780]: <info> (eth1): deactivating device (reason 'carrier-changed') [40]
Jun  3 14:19:21 HOSTNAME NetworkManager[1780]: <warn> DNS: plugin dnsmasq update failed
Jun  3 14:19:21 HOSTNAME NetworkManager[1780]: <info> Removing DNS information from /sbin/resolvconf
Jun  3 14:19:21 HOSTNAME dnsmasq[3302]: setting upstream servers from DBus
Jun  3 14:19:21 HOSTNAME kernel: [ 5445.766096] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun  3 14:19:22 HOSTNAME dbus[1707]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun  3 14:19:22 HOSTNAME dbus[1707]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun  3 14:20:12 HOSTNAME kernel: [ 5496.601636] SysRq : Emergency Sync
Jun  3 14:20:13 HOSTNAME kernel: [ 5496.856836] Emergency Sync complete
Jun  3 14:20:13 HOSTNAME kernel: [ 5497.170397] SysRq : Emergency Remount R/O
Jun  3 14:21:13 HOSTNAME kernel: imklog 5.8.11, log source = /proc/kmsg started.
Jun  3 14:21:13 HOSTNAME rsyslogd: [origin software="rsyslogd" swVersion="5.8.11" x-pid="1753" x-info="http://www.rsyslog.com"] start
Jun  3 14:21:13 HOSTNAME rsyslogd: rsyslogd's groupid changed to 103
Jun  3 14:21:13 HOSTNAME rsyslogd: rsyslogd's userid changed to 101
Jun  3 14:21:13 HOSTNAME rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
</pre>
[/HTML]

(Note: IP addresses and hostnames were changed)

---

### Post by sanosuke001 on 2013-06-03
Nevermind; apparently the System Monitor plugin I had for gnome had a bug and there was an update available which fixed the issue.

---

