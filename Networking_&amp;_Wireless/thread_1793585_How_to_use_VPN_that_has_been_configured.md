---
title: "How to use VPN that has been configured?"
date: 2011-06-29
forum: Networking &amp; Wireless
---

### Post by Number6 on 2011-06-29
Using Unity in Ubuntu 11.04,

OK I've figured out to to set up a VPN, by clicking on the Networking Icon and clicking VPN Connections->Configure VPN and setting up the details... but how to I actually USE the VPN I set up??? I thought it would appear in the VPN Connections but no the only things in there are Configure VPN and Disconnect VPN!

UPDATE: Nevermind.. I rebooted and it appeared in the VPN Connections as expected :)

---

### Post by qchapter on 2011-06-29
I typically need to restart after installing openvpn on ubuntu.  Reboot and you should see it in the vpn list after logging back in.

Thanks,

Kevin

---

### Post by Number6 on 2011-06-29
Yes that did the trick thanks... my problem now is that when I try to connect I get an odd message saying "Connection was not provided by any settings service"!!

What on earth does that mean? :confused:

---

### Post by qchapter on 2011-06-29
#6,

Not sure what that means.  I need a bit more info.  Please paste any vpn related entries from /var/log/syslog, and can you confirm that you are in fact connecting to an openvpn server, and not a Cisco or Juniper vpn concentrator?

Thanks,

Kevin

---

### Post by Number6 on 2011-06-29
OK I rebooted again and now I just get a connection failed message. I'm trying to connect to a Windows 2003 SBS Server
, definately no VPN concentrators involved.. I suspect I don't have the settings right.. Syslog as follows:

Jun 30 12:23:21 Star-One pppd[1725]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Jun 30 12:23:21 Star-One NetworkManager[642]: <info> VPN connection 'The Gate' (Connect) reply received.
Jun 30 12:23:21 Star-One pppd[1725]: pppd 2.4.5 started by root, uid 0
Jun 30 12:23:21 Star-One pppd[1725]: Using interface ppp0
Jun 30 12:23:21 Star-One pppd[1725]: Connect: ppp0 <--> /dev/pts/0
Jun 30 12:23:21 Star-One NetworkManager[642]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jun 30 12:23:21 Star-One NetworkManager[642]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jun 30 12:23:21 Star-One pptp[1728]: nm-pptp-service-1722 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Jun 30 12:23:21 Star-One pptp[1736]: nm-pptp-service-1722 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Jun 30 12:23:21 Star-One pptp[1736]: nm-pptp-service-1722 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Jun 30 12:23:21 Star-One pptp[1736]: nm-pptp-service-1722 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Jun 30 12:23:22 Star-One pptp[1736]: nm-pptp-service-1722 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Jun 30 12:23:22 Star-One pptp[1736]: nm-pptp-service-1722 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Jun 30 12:23:22 Star-One pptp[1736]: nm-pptp-service-1722 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 57720).
Jun 30 12:23:25 Star-One pptp[1736]: nm-pptp-service-1722 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Jun 30 12:23:25 Star-One pptp[1736]: nm-pptp-service-1722 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is 00000000, recv_accm is FFFFFFFF
Jun 30 12:23:25 Star-One pptp[1736]: nm-pptp-service-1722 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Jun 30 12:23:25 Star-One pptp[1736]: nm-pptp-service-1722 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Jun 30 12:23:25 Star-One pptp[1736]: nm-pptp-service-1722 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is FFFFFFFF, recv_accm is FFFFFFFF
Jun 30 12:23:25 Star-One pptp[1736]: nm-pptp-service-1722 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Jun 30 12:23:25 Star-One pppd[1725]: LCP terminated by peer (CM-^O^YM-O^@<M-Mt^@^@^BM-3)
Jun 30 12:23:26 Star-One pptp[1736]: nm-pptp-service-1722 log[ctrlp_disp:pptp_ctrl.c:912]: Received Call Clear Request.
Jun 30 12:23:28 Star-One pppd[1725]: Connection terminated.
Jun 30 12:23:28 Star-One NetworkManager[642]: <warn> VPN plugin failed: 1
Jun 30 12:23:28 Star-One avahi-daemon[646]: Withdrawing workstation service for ppp0.
Jun 30 12:23:29 Star-One NetworkManager[642]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jun 30 12:23:29 Star-One pptp[1728]: nm-pptp-service-1722 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Jun 30 12:23:29 Star-One pptp[1728]: nm-pptp-service-1722 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Jun 30 12:23:29 Star-One NetworkManager[642]: <warn> VPN plugin failed: 1

---

### Post by qchapter on 2011-06-29
Ah, a pptp vpn.  I'm afraid I have no experience with pptp, so I won't be any help.  My experience is with OpenVPN and Cisco VPN.  Anyone familiar with pptp care to chime in here?

Thanks,

Kevin

---

### Post by Number6 on 2011-06-30
Thanks for trying anyway Kevin!

So calling all PPTP VPN experts.. I have chocolate fish!

---

