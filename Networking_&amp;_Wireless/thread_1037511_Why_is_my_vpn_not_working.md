---
title: "Why is my vpn not working?"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by ubantuwannabe on 2009-01-11
I am trying to set up a client pptp vpn connection to a remote private network.

Why is my vpn not working?

here's what I log 

tail -f /var/log/message

Jan 12 10:02:18 chunhung-desktop pppd[5938]: local  IP address 192.168.1.190
Jan 12 10:02:18 chunhung-desktop pppd[5938]: remote IP address 63.216.144.163
Jan 12 10:12:49 chunhung-desktop -- MARK --
Jan 12 10:15:57 chunhung-desktop pppd[5938]: Terminating on signal 15
Jan 12 10:15:57 chunhung-desktop pppd[5938]: Connect time 13.7 minutes.
Jan 12 10:15:57 chunhung-desktop pppd[5938]: Sent 15352 bytes, received 10854 bytes.
Jan 12 10:15:57 chunhung-desktop pppd[5938]: Child process /usr/sbin/pptp 63.216.144.163 --nolaunchpppd --logstring nm-pptp-service-5933 (pid 5939) terminated with signal 15
Jan 12 10:15:57 chunhung-desktop pppd[5938]: Modem hangup
Jan 12 10:15:57 chunhung-desktop pppd[5938]: Connection terminated.
Jan 12 10:15:57 chunhung-desktop pppd[5938]: Exit.
Jan 12 10:20:36 chunhung-desktop pppd[6073]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so loaded.
Jan 12 10:20:36 chunhung-desktop pppd[6073]: pppd 2.4.4 started by root, uid 0
Jan 12 10:20:36 chunhung-desktop pppd[6073]: Using interface ppp0
Jan 12 10:20:36 chunhung-desktop pppd[6073]: Connect: ppp0 <--> /dev/pts/1
Jan 12 10:20:48 chunhung-desktop pppd[6073]: CHAP authentication succeeded
Jan 12 10:20:48 chunhung-desktop pppd[6073]: local  IP address 192.168.1.190
Jan 12 10:20:48 chunhung-desktop pppd[6073]: remote IP address 63.216.144.163

here is what I get from /var/log/syslog

tail -f /var/log/syslog
Jan 12 10:33:26 chunhung-desktop avahi-daemon[4529]: New relevant interface eth0.IPv4 for mDNS.
Jan 12 10:33:26 chunhung-desktop avahi-daemon[4529]: Registering new address record for 192.168.123.102 on eth0.IPv4.
Jan 12 10:33:26 chunhung-desktop pppd[6197]: Child process /usr/sbin/pptp 63.216.144.163 --nolaunchpppd --logstring nm-pptp-service-6194 (pid 6198) terminated with signal 15
Jan 12 10:33:26 chunhung-desktop pppd[6197]: Modem hangup
Jan 12 10:33:26 chunhung-desktop pppd[6197]: Connection terminated.
Jan 12 10:33:26 chunhung-desktop pppd[6197]: Exit.
Jan 12 10:33:27 chunhung-desktop NetworkManager: <info> Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Jan 12 10:33:27 chunhung-desktop NetworkManager: <info> Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Jan 12 10:33:27 chunhung-desktop NetworkManager: <info> VPN service 'org.freedesktop.NetworkManager.pptp' disappeared, cancelling connections
Jan 12 10:33:27 chunhung-desktop nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Jan 12 10:36:27 chunhung-desktop NetworkManager: <info> Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Jan 12 10:36:27 chunhung-desktop NetworkManager: <info> VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 6266
Jan 12 10:36:27 chunhung-desktop NetworkManager: <info> VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Jan 12 10:36:27 chunhung-desktop NetworkManager: <info> VPN plugin state changed: 3
Jan 12 10:36:27 chunhung-desktop pppd[6269]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so loaded.
Jan 12 10:36:27 chunhung-desktop NetworkManager: <info> VPN connection 'smshub' (Connect) reply received.
Jan 12 10:36:27 chunhung-desktop pppd[6269]: pppd 2.4.4 started by root, uid 0
Jan 12 10:36:27 chunhung-desktop pppd[6269]: Using interface ppp0
Jan 12 10:36:27 chunhung-desktop pppd[6269]: Connect: ppp0 <--> /dev/pts/2
Jan 12 10:36:27 chunhung-desktop pptp[6272]: nm-pptp-service-6266 log[mainptp.c:314]: The synchronous pptp option is NOT activated
Jan 12 10:36:29 chunhung-desktop pptp[6278]: nm-pptp-service-6266 log[ctrlp_repptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Jan 12 10:36:30 chunhung-desktop pptp[6278]: nm-pptp-service-6266 log[ctrlp_dispptp_ctrl.c:739]: Received Start Control Connection Reply
Jan 12 10:36:30 chunhung-desktop pptp[6278]: nm-pptp-service-6266 log[ctrlp_dispptp_ctrl.c:773]: Client connection established.
Jan 12 10:36:30 chunhung-desktop pptp[6278]: nm-pptp-service-6266 log[ctrlp_repptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Jan 12 10:36:31 chunhung-desktop pptp[6278]: nm-pptp-service-6266 log[ctrlp_dispptp_ctrl.c:858]: Received Outgoing Call Reply.
Jan 12 10:36:31 chunhung-desktop pptp[6278]: nm-pptp-service-6266 log[ctrlp_dispptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 715).
Jan 12 10:36:42 chunhung-desktop pppd[6269]: CHAP authentication succeeded
Jan 12 10:36:46 chunhung-desktop pppd[6269]: Cannot determine ethernet address for proxy ARP
Jan 12 10:36:46 chunhung-desktop pppd[6269]: local IP address 192.168.1.190
Jan 12 10:36:46 chunhung-desktop pppd[6269]: remote IP address 63.216.144.163
Jan 12 10:36:46 chunhung-desktop NetworkManager: <info> VPN connection 'smshub' (IP Config Get) reply received.
Jan 12 10:36:46 chunhung-desktop NetworkManager: <info> VPN Gateway: 63.216.144.163
Jan 12 10:36:46 chunhung-desktop NetworkManager: <info> Tunnel Device: ppp0
Jan 12 10:36:46 chunhung-desktop NetworkManager: <info> Internal IP4 Address: 192.168.1.190
Jan 12 10:36:46 chunhung-desktop NetworkManager: <info> Internal IP4 Prefix: 32
Jan 12 10:36:46 chunhung-desktop NetworkManager: <info> Internal IP4 Point-to-Point Address: 0.0.0.0
Jan 12 10:36:46 chunhung-desktop NetworkManager: <info> Maximum Segment Size (MSS): 0
Jan 12 10:36:46 chunhung-desktop NetworkManager: <info> DNS Domain: '(none)'
Jan 12 10:36:46 chunhung-desktop NetworkManager: <info> Login Banner:
Jan 12 10:36:46 chunhung-desktop NetworkManager: <info> -----------------------------------------
Jan 12 10:36:46 chunhung-desktop NetworkManager: <info> (null)
Jan 12 10:36:46 chunhung-desktop NetworkManager: <info> -----------------------------------------
Jan 12 10:36:47 chunhung-desktop NetworkManager: <info> VPN connection 'smshub' (IP Config Get) complete.

I only see that there's lock icon on top of the wired connection on the right hand corner.

also whenever I enable vpn I have to disable vpn in order to connect to internet why this is so? and how to enable internet connection while still connected with my private network?

thanks

---

