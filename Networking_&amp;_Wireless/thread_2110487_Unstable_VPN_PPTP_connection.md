---
title: "Unstable VPN PPTP connection"
date: 2013-01-30
forum: Networking &amp; Wireless
---

### Post by radzish on 2013-01-30
Hi,

I have problem using VPN PPTP connection to my home network.
Connection is being established successfully, but in a few seconds (usually 30-40) it stops working.
I was using standard VPN client through Cinnamon Network Settings.
My friends were using the same my VPN server successfully for half of the day (on their Windows 7).

I am using Linux Mint 14 x64 (Linux kernel-mint 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux).
VPN Server is running on (Asus RT-AC66U [Linux RT-AC66U 2.6.22.19 #1 Tue Nov 6 23:19:25 CST 2012 mips GNU/Linux]). I checked and it seems like it is:
accel-pptpd v0.8.5 compiled for pppd-2.4.5, linux-2.6.22.19

Logs from Mint:

> 
Jan 30 16:36:25 radzish-mint NetworkManager[886]: <info> Starting VPN service 'pptp'...
Jan 30 16:36:25 radzish-mint NetworkManager[886]: <info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 22209
Jan 30 16:36:25 radzish-mint NetworkManager[886]: <info> VPN service 'pptp' appeared; activating connections
Jan 30 16:36:25 radzish-mint NetworkManager[886]: <info> VPN plugin state changed: starting (3)
Jan 30 16:36:25 radzish-mint NetworkManager[886]: <info> VPN connection 'test vpn' (Connect) reply received.
Jan 30 16:36:25 radzish-mint pppd[22212]: Plugin /usr/lib/pppd/2.4.5/nm-pptp-pppd-plugin.so loaded.
Jan 30 16:36:25 radzish-mint pppd[22212]: pppd 2.4.5 started by root, uid 0
Jan 30 16:36:25 radzish-mint pppd[22212]: Using interface ppp0
Jan 30 16:36:25 radzish-mint pppd[22212]: Connect: ppp0 <--> /dev/pts/6
Jan 30 16:36:25 radzish-mint NetworkManager[886]: SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan 30 16:36:25 radzish-mint NetworkManager[886]: SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jan 30 16:36:25 radzish-mint pptp[22215]: nm-pptp-service-22209 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Jan 30 16:36:25 radzish-mint NetworkManager[886]: <warn> /sys/devices/virtual/net/ppp0: couldn't determine device driver; ignoring...
Jan 30 16:36:25 radzish-mint pptp[22223]: nm-pptp-service-22209 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Jan 30 16:36:25 radzish-mint pptp[22223]: nm-pptp-service-22209 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Jan 30 16:36:25 radzish-mint pptp[22223]: nm-pptp-service-22209 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Jan 30 16:36:26 radzish-mint pptp[22223]: nm-pptp-service-22209 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Jan 30 16:36:26 radzish-mint pptp[22223]: nm-pptp-service-22209 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Jan 30 16:36:26 radzish-mint pptp[22223]: nm-pptp-service-22209 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 120).
Jan 30 16:36:30 radzish-mint pppd[22212]: CHAP authentication succeeded
Jan 30 16:36:30 radzish-mint pppd[22212]: local IP address 192.168.10.2
Jan 30 16:36:30 radzish-mint pppd[22212]: remote IP address 192.168.1.1
Jan 30 16:36:30 radzish-mint pppd[22212]: primary DNS address 192.168.1.1
Jan 30 16:36:30 radzish-mint pppd[22212]: secondary DNS address 192.168.1.1
Jan 30 16:36:30 radzish-mint NetworkManager[886]: <info> VPN connection 'test vpn' (IP4 Config Get) reply received from old-style plugin.
Jan 30 16:36:30 radzish-mint NetworkManager[886]: <info> VPN Gateway: 176.104.184.185
Jan 30 16:36:30 radzish-mint NetworkManager[886]: <info> Tunnel Device: ppp0
Jan 30 16:36:30 radzish-mint NetworkManager[886]: <info> IPv4 configuration:
Jan 30 16:36:30 radzish-mint NetworkManager[886]: <info> Internal Address: 192.168.10.2
Jan 30 16:36:30 radzish-mint NetworkManager[886]: <info> Internal Prefix: 32
Jan 30 16:36:30 radzish-mint NetworkManager[886]: <info> Internal Point-to-Point Address: 192.168.1.1
Jan 30 16:36:30 radzish-mint NetworkManager[886]: <info> Maximum Segment Size (MSS): 0
Jan 30 16:36:30 radzish-mint NetworkManager[886]: <info> Forbid Default Route: no
Jan 30 16:36:30 radzish-mint NetworkManager[886]: <info> Internal DNS: 192.168.1.1
Jan 30 16:36:30 radzish-mint NetworkManager[886]: <info> DNS Domain: '(none)'
Jan 30 16:36:30 radzish-mint NetworkManager[886]: <info> No IPv6 configuration
Jan 30 16:36:31 radzish-mint NetworkManager[886]: <info> VPN connection 'test vpn' (IP Config Get) complete.
Jan 30 16:36:31 radzish-mint NetworkManager[886]: <info> Policy set 'test vpn' (ppp0) as default for IPv4 routing and DNS.
Jan 30 16:36:31 radzish-mint NetworkManager[886]: <info> ((null)): writing resolv.conf to /sbin/resolvconf
Jan 30 16:36:31 radzish-mint dnsmasq[2492]: setting upstream servers from DBus
Jan 30 16:36:31 radzish-mint dnsmasq[2492]: using nameserver 192.168.1.1#53
Jan 30 16:36:31 radzish-mint dbus[538]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jan 30 16:36:31 radzish-mint NetworkManager[886]: <info> VPN plugin state changed: started (4)
Jan 30 16:36:31 radzish-mint dbus[538]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jan 30 16:36:57 radzish-mint ntpdate[22280]: adjust time server 91.189.94.4 offset 0.003858 sec
Jan 30 16:38:26 radzish-mint pptp[22223]: nm-pptp-service-22209 log[pptp_handle_timer:pptp_ctrl.c:1050]: closing control connection due to missing echo reply
Jan 30 16:38:26 radzish-mint pptp[22223]: nm-pptp-service-22209 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Jan 30 16:38:26 radzish-mint pptp[22223]: nm-pptp-service-22209 log[pptp_conn_close:pptp_ctrl.c:430]: Closing PPTP connection
Jan 30 16:38:26 radzish-mint pptp[22223]: nm-pptp-service-22209 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 3 'Stop-Control-Connection-Request'
Jan 30 16:38:26 radzish-mint pptp[22223]: nm-pptp-service-22209 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Jan 30 16:38:26 radzish-mint pppd[22212]: Modem hangup
Jan 30 16:38:26 radzish-mint pppd[22212]: Connect time 2.0 minutes.
Jan 30 16:38:26 radzish-mint pppd[22212]: Sent 134396 bytes, received 173934 bytes.
Jan 30 16:38:26 radzish-mint NetworkManager[886]: <info> VPN plugin state changed: stopping (5)
Jan 30 16:38:26 radzish-mint NetworkManager[886]: <info> VPN plugin state changed: stopped (6)
Jan 30 16:38:26 radzish-mint NetworkManager[886]: <info> VPN plugin state change reason: 0
Jan 30 16:38:26 radzish-mint avahi-daemon[581]: Withdrawing address record for 192.168.1.142 on wlan0.
Jan 30 16:38:26 radzish-mint avahi-daemon[581]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.142.
Jan 30 16:38:26 radzish-mint pppd[22212]: Connection terminated.
Jan 30 16:38:26 radzish-mint avahi-daemon[581]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jan 30 16:38:26 radzish-mint avahi-daemon[581]: Withdrawing workstation service for ppp0.
Jan 30 16:38:26 radzish-mint avahi-daemon[581]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.142.
Jan 30 16:38:26 radzish-mint avahi-daemon[581]: New relevant interface wlan0.IPv4 for mDNS.
Jan 30 16:38:26 radzish-mint avahi-daemon[581]: Registering new address record for 192.168.1.142 on wlan0.IPv4.
Jan 30 16:38:27 radzish-mint NetworkManager[886]: <info> Policy set 'Auto enreach' (wlan0) as default for IPv4 routing and DNS.
Jan 30 16:38:27 radzish-mint NetworkManager[886]: <info> ((null)): writing resolv.conf to /sbin/resolvconf
Jan 30 16:38:27 radzish-mint dnsmasq[2492]: setting upstream servers from DBus
Jan 30 16:38:27 radzish-mint dnsmasq[2492]: using nameserver 192.168.1.1#53
Jan 30 16:38:27 radzish-mint dbus[538]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jan 30 16:38:27 radzish-mint NetworkManager[886]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Jan 30 16:38:27 radzish-mint NetworkManager[886]: <warn> (118) failed to find interface name for index
Jan 30 16:38:27 radzish-mint NetworkManager[886]: nm_system_iface_flush_routes: assertion `iface != NULL' failed
Jan 30 16:38:27 radzish-mint NetworkManager[886]: <warn> (118) failed to find interface name for index
Jan 30 16:38:27 radzish-mint NetworkManager[886]: SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan 30 16:38:27 radzish-mint dbus[538]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jan 30 16:38:28 radzish-mint pppd[22212]: Exit.
Jan 30 16:38:32 radzish-mint NetworkManager[886]: <info> VPN service 'pptp' disappeared


Logs from SERVER:
> 
Jan 30 16:36:25 pptpd[14901]: CTRL: Client 194.44.22.67 control connection started
Jan 30 16:36:26 pptpd[14901]: CTRL: Starting call (launching pppd, opening GRE)
Jan 30 16:36:26 pptp[14909]: Plugin pptp.so loaded.
Jan 30 16:36:26 pptp[14909]: PPTP plugin version 0.8.5 compiled for pppd-2.4.5, linux-2.6.22.19
Jan 30 16:36:26 pptp[14909]: pppd 2.4.5 started by admin, uid 0
Jan 30 16:36:26 pptp[14909]: Using interface ppp10
Jan 30 16:36:26 pptp[14909]: Connect: ppp10 <--> pptp (194.44.22.67)
Jan 30 16:36:30 pptp[14909]: Cannot determine ethernet address for proxy ARP
Jan 30 16:36:30 pptp[14909]: local IP address 192.168.1.1
Jan 30 16:36:30 pptp[14909]: remote IP address 192.168.10.2
Jan 30 16:37:54 pptpd[14901]: CTRL: EOF or bad error reading ctrl packet length.
Jan 30 16:37:54 pptpd[14901]: CTRL: couldn't read packet header (exit)
Jan 30 16:37:54 pptpd[14901]: CTRL: CTRL read failed
Jan 30 16:37:54 pptpd[14901]: CTRL: Client pppd TERM sending
Jan 30 16:37:54 pptpd[14901]: CTRL: Client pppd finish wait
Jan 30 16:37:54 pptp[14909]: Terminating on signal 15
Jan 30 16:37:54 pptp[14909]: Connect time 1.4 minutes.
Jan 30 16:37:54 pptp[14909]: Sent 223042 bytes, received 120723 bytes.
Jan 30 16:38:00 pptp[14909]: Connection terminated.
Jan 30 16:38:01 pptp[14909]: Modem hangup
Jan 30 16:38:01 pptp[14909]: Exit.
Jan 30 16:38:01 pptpd[14901]: CTRL: Client 194.44.22.67 control connection finished


---

### Post by jdthood on 2013-01-30
> **radzish said:**
> ```

HJan 30 16:38:26 radzish-mint pptp[22223]: nm-pptp-service-22209 log[pptp_handle_timer:pptp_ctrl.c:1050]: closing control connection due to missing echo reply

```

Please add your information to the existing bug report: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/991666](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/991666)

---

