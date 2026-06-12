---
title: "PPTP VPN disconnect when working"
date: 2010-03-28
forum: Networking &amp; Wireless
---

### Post by ravindika on 2010-03-28
I'm using ADSL connection to connect for my Office PPTP VPN from home.can anyone tell me why PPTP VPN disconnect when working with RDP, HTTP or SFTP? It is not disconnect when using SSH connections.

Here is the debug info of network manager.


NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 3105
NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
NetworkManager: <info>  VPN plugin state changed: 1
NetworkManager: <info>  VPN plugin state changed: 3
** Message: <info>  pppd started with pid 3108

NetworkManager: <info>  VPN connection 'Office' (Connect) reply received.
Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
** Message: nm-pptp-ppp-plugin: (plugin_init): initializing
** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 3 / phase 'serial connection'
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 5 / phase 'establish'
NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 6 / phase 'authenticate'
** Message: nm-pptp-ppp-plugin: (get_credentials): passwd-hook, requesting 
credentials...
** Message: nm-pptp-ppp-plugin: (get_credentials): got credentials from NetworkManager-pptp
CHAP authentication succeeded
** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 8 / phase 'network'
MPPE 128-bit stateless compression enabled
Cannot determine ethernet address for proxy ARP
local  IP address xxx.xxx.xxx.xxx
remote IP address xxx.xxx.xxx.xxx
primary   DNS address xxx.xxx.xxx.xxx
secondary DNS address xxx.xxx.xxx.xxx
** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 9 / phase 'running'
** Message: nm-pptp-ppp-plugin: (nm_ip_up): ip-up event
** Message: nm-pptp-ppp-plugin: (nm_ip_up): sending Ip4Config to NetworkManager-pptp...
** Message: <info>  PPTP service (IP Config Get) reply received.

NetworkManager: <info>  VPN connection 'Office' (IP Config Get) reply received.
NetworkManager: <info>  VPN Gateway: xxx.xxx.xxx.xxx
NetworkManager: <info>  Tunnel Device: ppp0
NetworkManager: <info>  Internal IP4 Address: xxx.xxx.xxx.xxx
NetworkManager: <info>  Internal IP4 Prefix: 32
NetworkManager: <info>  Internal IP4 Point-to-Point Address: xxx.xxx.xxx.xxx
NetworkManager: <info>  Maximum Segment Size (MSS): 0
NetworkManager: <info>  Internal IP4 DNS: xxx.xxx.xxx.xxx
NetworkManager: <info>  Internal IP4 DNS: xxx.xxx.xxx.xxx
NetworkManager: <info>  DNS Domain: '(none)'
NetworkManager: <info>  Login Banner:
NetworkManager: <info>  -----------------------------------------
NetworkManager: <info>  (null)
NetworkManager: <info>  -----------------------------------------
NetworkManager: <info>  (ppp0): writing resolv.conf to /sbin/resolvconf
resolvconf: Error: /etc/resolv.conf must be a symlink
NetworkManager: <info>  VPN connection 'Office' (IP Config Get) complete.
NetworkManager: <info>  (ppp0): writing resolv.conf to /sbin/resolvconf
resolvconf: Error: /etc/resolv.conf must be a symlink
NetworkManager: <info>  Policy set 'Office' (ppp0) as default for routing and DNS.
NetworkManager: <info>  VPN plugin state changed: 4

Modem hangup
** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 8 / phase 'network'
Connect time 1.0 minutes.
Sent 39747 bytes, received 154835 bytes.
MPPE disabled
** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 10 / phase 'terminate'
** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 5 / phase 'establish'
** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 5 / phase 'establish'
** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 11 / phase 'disconnect'
Connection terminated.
** Message: <info>  Terminated ppp daemon with PID 3108.

NetworkManager: <info>  VPN plugin state changed: 5
NetworkManager: <info>  VPN plugin state changed: 6
NetworkManager: <info>  VPN plugin state change reason: 0
NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 1 / phase 'dead'
NetworkManager: flush_routes: assertion `iface_idx >= 0' failed
NetworkManager: flush_addresses: assertion `iface_idx >= 0' failed
NetworkManager: <info>  (ppp0): writing resolv.conf to /sbin/resolvconf
Terminating on signal 15
** Message: nm-pptp-ppp-plugin: (nm_exit_notify): cleaning up

** (process:3105): WARNING **: <WARN>  pppd_watch_cb(): pppd exited with error code 5

resolvconf: Error: /etc/resolv.conf must be a symlink
NetworkManager: <info>  (eth0): writing resolv.conf to /sbin/resolvconf
resolvconf: Error: /etc/resolv.conf must be a symlink
NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
NetworkManager: <debug> [1269764623.002240] ensure_killed(): waiting for vpn service pid 3105 to exit
NetworkManager: <debug> [1269764623.002383] ensure_killed(): vpn service pid 3105 cleaned u


Thanks.

---

### Post by gmoraes on 2011-05-13
Hi,
Have you figured it out your issue?
I'm also having an issue (getting disconnected) when trying to access the network, but from the network I can access the remote machine and is vpn'ed.

Thanks,

---

