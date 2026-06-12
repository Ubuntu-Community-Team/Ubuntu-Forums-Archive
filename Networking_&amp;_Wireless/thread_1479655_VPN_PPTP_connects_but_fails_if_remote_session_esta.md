---
title: "VPN PPTP connects but fails if remote session established on server"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by Omeil on 2010-05-10
Hi All,

I am trying to connect to a windows 2000 VPN server at work, with my current settings in DOES connect to the VPN and i can ping the domain server which is 10.1.1.2 but the first issue is i cannot ping the other computers on the network(via hostnames) can't remember the ip address of the other machines :D. second issue is when the connection is established and i RDP into 10.1.1.2 ok great i am connected to the server but any interaction in the RDP session even moving the mouse on the screen kills the session and the VPN connection fails.

Running Ubuntu 10.04 LTS 64Bit

Image of current settings in network manager:

[IMG]http://i39.tinypic.com/20tfr4g.png[/IMG]

Syslog:

```
May 11 12:08:04 oliver-desktop NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
May 11 12:08:04 oliver-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 2610
May 11 12:08:04 oliver-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
May 11 12:08:12 oliver-desktop NetworkManager: <info>  VPN plugin state changed: 3
May 11 12:08:12 oliver-desktop NetworkManager: <info>  VPN connection 'VPN connection 1' (Connect) reply received.
May 11 12:08:12 oliver-desktop pppd[2612]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
May 11 12:08:12 oliver-desktop pppd[2612]: pppd 2.4.5 started by root, uid 0
May 11 12:08:12 oliver-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
May 11 12:08:12 oliver-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
May 11 12:08:12 oliver-desktop pppd[2612]: Using interface ppp0
May 11 12:08:12 oliver-desktop pppd[2612]: Connect: ppp0 <--> /dev/pts/1
May 11 12:08:12 oliver-desktop pptp[2615]: nm-pptp-service-2610 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
May 11 12:08:13 oliver-desktop pptp[2623]: nm-pptp-service-2610 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
May 11 12:08:13 oliver-desktop pptp[2623]: nm-pptp-service-2610 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
May 11 12:08:13 oliver-desktop pptp[2623]: nm-pptp-service-2610 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
May 11 12:08:14 oliver-desktop pptp[2623]: nm-pptp-service-2610 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
May 11 12:08:14 oliver-desktop pptp[2623]: nm-pptp-service-2610 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
May 11 12:08:14 oliver-desktop pptp[2623]: nm-pptp-service-2610 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 17383).
May 11 12:08:14 oliver-desktop pptp[2623]: nm-pptp-service-2610 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 55394
May 11 12:08:14 oliver-desktop pptp[2623]: nm-pptp-service-2610 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is 00000000, recv_accm is FFFFFFFF
May 11 12:08:14 oliver-desktop pptp[2623]: nm-pptp-service-2610 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
May 11 12:08:15 oliver-desktop pppd[2612]: CHAP authentication succeeded
May 11 12:08:15 oliver-desktop pppd[2612]: MPPE 128-bit stateless compression enabled
May 11 12:08:16 oliver-desktop pppd[2612]: Cannot determine ethernet address for proxy ARP
May 11 12:08:16 oliver-desktop pppd[2612]: local  IP address 10.1.1.61
May 11 12:08:16 oliver-desktop pppd[2612]: remote IP address 10.1.1.67
May 11 12:08:16 oliver-desktop pppd[2612]: primary   DNS address 10.1.1.2
May 11 12:08:16 oliver-desktop NetworkManager: <info>  VPN connection 'VPN connection 1' (IP Config Get) reply received.
May 11 12:08:16 oliver-desktop NetworkManager: <info>  VPN Gateway: My External IP Address
May 11 12:08:16 oliver-desktop NetworkManager: <info>  Tunnel Device: ppp0
May 11 12:08:16 oliver-desktop NetworkManager: <info>  Internal IP4 Address: 10.1.1.61
May 11 12:08:16 oliver-desktop NetworkManager: <info>  Internal IP4 Prefix: 32
May 11 12:08:16 oliver-desktop NetworkManager: <info>  Internal IP4 Point-to-Point Address: 10.1.1.67
May 11 12:08:16 oliver-desktop NetworkManager: <info>  Maximum Segment Size (MSS): 0
May 11 12:08:16 oliver-desktop NetworkManager: <info>  Internal IP4 DNS: 10.1.1.2
May 11 12:08:16 oliver-desktop NetworkManager: <info>  DNS Domain: '(none)'
May 11 12:08:16 oliver-desktop NetworkManager: <info>  Login Banner:
May 11 12:08:16 oliver-desktop NetworkManager: <info>  -----------------------------------------
May 11 12:08:16 oliver-desktop NetworkManager: <info>  (null)
May 11 12:08:16 oliver-desktop NetworkManager: <info>  -----------------------------------------
May 11 12:08:17 oliver-desktop NetworkManager: <info>  VPN connection 'VPN connection 1' (IP Config Get) complete.
May 11 12:08:17 oliver-desktop NetworkManager: <info>  Policy set 'VPN connection 1' (ppp0) as default for routing and DNS.
May 11 12:08:17 oliver-desktop NetworkManager: <info>  VPN plugin state changed: 4
May 11 12:08:17 oliver-desktop nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
May 11 12:09:12 oliver-desktop ntfs-3g[2664]: Version 2010.3.6 external FUSE 28
May 11 12:09:12 oliver-desktop ntfs-3g[2664]: Mounted /dev/sda5 (Read-Write, label "", NTFS 3.1)
May 11 12:09:12 oliver-desktop ntfs-3g[2664]: Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077
May 11 12:09:12 oliver-desktop ntfs-3g[2664]: Mount options: rw,nosuid,nodev,uhelper=udisks,silent,allow_other,nonempty,relatime,fsname=/dev/sda5,blkdev,blksize=4096,default_permissions
May 11 12:09:12 oliver-desktop ntfs-3g[2664]: Global ownership and permissions enforced, configuration type 1
May 11 12:09:13 oliver-desktop pptp[2623]: nm-pptp-service-2610 log[logecho:pptp_ctrl.c:677]: Echo Request received.
May 11 12:09:13 oliver-desktop pptp[2623]: nm-pptp-service-2610 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 6 'Echo-Reply'
May 11 12:09:47 oliver-desktop ntfs-3g[2705]: Version 2010.3.6 external FUSE 28
May 11 12:09:47 oliver-desktop ntfs-3g[2705]: Mounted /dev/sda2 (Read-Write, label "", NTFS 3.1)
May 11 12:09:47 oliver-desktop ntfs-3g[2705]: Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077
May 11 12:09:47 oliver-desktop ntfs-3g[2705]: Mount options: rw,nosuid,nodev,uhelper=udisks,silent,allow_other,nonempty,relatime,fsname=/dev/sda2,blkdev,blksize=4096,default_permissions
May 11 12:09:47 oliver-desktop ntfs-3g[2705]: Global ownership and permissions enforced, configuration type 1
May 11 12:10:13 oliver-desktop pptp[2623]: nm-pptp-service-2610 log[logecho:pptp_ctrl.c:677]: Echo Request received.
May 11 12:10:13 oliver-desktop pptp[2623]: nm-pptp-service-2610 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 6 'Echo-Reply'
May 11 12:10:47 oliver-desktop pptp[2615]: nm-pptp-service-2610 warn[decaps_gre:pptp_gre.c:331]: short read (-1): Message too long
May 11 12:10:47 oliver-desktop pptp[2623]: nm-pptp-service-2610 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
May 11 12:10:47 oliver-desktop pptp[2623]: nm-pptp-service-2610 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
May 11 12:10:47 oliver-desktop pptp[2623]: nm-pptp-service-2610 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
May 11 12:10:47 oliver-desktop pppd[2612]: Modem hangup
May 11 12:10:47 oliver-desktop pppd[2612]: Connect time 2.6 minutes.
May 11 12:10:47 oliver-desktop pppd[2612]: Sent 12567 bytes, received 132154 bytes.
May 11 12:10:47 oliver-desktop pppd[2612]: MPPE disabled
May 11 12:10:47 oliver-desktop pppd[2612]: Connection terminated.
May 11 12:10:47 oliver-desktop NetworkManager: <info>  VPN plugin state changed: 5
May 11 12:10:47 oliver-desktop NetworkManager: <info>  VPN plugin state changed: 6
May 11 12:10:47 oliver-desktop NetworkManager: <info>  VPN plugin state change reason: 0
May 11 12:10:47 oliver-desktop NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
May 11 12:10:47 oliver-desktop pppd[2612]: Exit.
May 11 12:10:48 oliver-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
May 11 12:10:48 oliver-desktop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
May 11 12:10:48 oliver-desktop nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
May 11 12:11:01 oliver-desktop NetworkManager: <debug> [1273543861.002037] ensure_killed(): waiting for vpn service pid 2610 to exit
May 11 12:11:01 oliver-desktop NetworkManager: <debug> [1273543861.002116] ensure_killed(): vpn service pid 2610 cleaned up
```

/var/log/messages:

```
May 11 12:08:12 oliver-desktop pppd[2612]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
May 11 12:08:12 oliver-desktop pppd[2612]: pppd 2.4.5 started by root, uid 0
May 11 12:08:12 oliver-desktop pppd[2612]: Using interface ppp0
May 11 12:08:12 oliver-desktop pppd[2612]: Connect: ppp0 <--> /dev/pts/1
May 11 12:08:15 oliver-desktop pppd[2612]: CHAP authentication succeeded
May 11 12:08:15 oliver-desktop pppd[2612]: MPPE 128-bit stateless compression enabled
May 11 12:08:16 oliver-desktop pppd[2612]: local  IP address 10.1.1.61
May 11 12:08:16 oliver-desktop pppd[2612]: remote IP address 10.1.1.67
May 11 12:08:16 oliver-desktop pppd[2612]: primary   DNS address 10.1.1.2
May 11 12:10:47 oliver-desktop pppd[2612]: Modem hangup
May 11 12:10:47 oliver-desktop pppd[2612]: Connect time 2.6 minutes.
May 11 12:10:47 oliver-desktop pppd[2612]: Sent 12567 bytes, received 132154 bytes.
May 11 12:10:47 oliver-desktop pppd[2612]: Connection terminated.
May 11 12:10:47 oliver-desktop pppd[2612]: Exit.
```

Any help would be greatly appreciated thanks.

Regards,

Omeil

---

### Post by Omeil on 2010-05-11
Hi All,

Fixed the issue,

My first issue was just a routing issue had to route the address that i required, but since i got the list of hostnames relating to ip addresses don't really need that to work 100%.

The disconnection issue was related to the MTU i believe it was set to 1500 but had to be set below 1200 to work efficiently 1300-1420 had glitches above 1420 made the VPN session fail. Below 1200 seems to be optimal for the PPTP Session with the Windows 2000 VPN server.

Fix: sudo ifconfig eth0 mtu xxxx

eth0 = your networking devices

change the xxxx to your preferred MTU be it mtu 1200, mtu 900 etc..

Hope this helps someone else out there.

Regards,

Omeil:guitar:

---

### Post by radzish on 2013-01-30
Hi,

Changing of MTU did not help. (I am using WiFi, is was changing it on appropriate interface)

Any other ideas ?

(I am using VPN server set up on Asus Router).

---

### Post by radzish on 2013-01-30
Hi,

Changing of MTU did not help. (I am using WiFi, is was changing it on appropriate interface)

Any other ideas ?

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


Logs from VPN Server:

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

### Post by codemaniac on 2013-01-30
Closing the old thread.

As per the Ubuntu Forums Code of Conduct, please do not post in threads more than one year old.

Thanks!

---

