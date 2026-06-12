---
title: "VPN on 10.04"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by giesen2 on 2010-05-10
I configure a Microsoft VPN, but when I click connect, I get a popup notification, "VPN Connection Failed. The VPN connection 'myvpn' failed."

I use this VPN all the time from my Windows laptop.

How can I fix this or how can I at least get more detailed logs and error messages?

---

### Post by Omeil on 2010-05-10
Hi,

For more detailed logs of whats happening best to post these two on here:

/var/log/syslog

and

/var/log/messages

Also can you post your VPN settings.

Regards,

Omeil

---

### Post by giesen2 on 2010-05-10
OK, I pasted my logs below... I removed some personal details (real VPN host name is not vpn.####.com). My config is plain vanilla (entered VPN host, NT domain, user, pass, and that's it). I've read a ton of how-to guides and gone through elaborate step-by-step instructions, but they never worked (I've done a full reformat since then, so everything is default now)

Anything that I can try changing?

```

May 10 20:58:27 mysystem NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
May 10 20:58:27 mysystem NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 1955
May 10 20:58:27 mysystem NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
May 10 20:58:27 mysystem NetworkManager: <info>  VPN plugin state changed: 1
May 10 20:58:27 mysystem NetworkManager: <info>  VPN plugin state changed: 3
May 10 20:58:27 mysystem NetworkManager: <info>  VPN connection 'vpn.####.com' (Connect) reply received.
May 10 20:58:27 mysystem pppd[1957]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
May 10 20:58:27 mysystem pppd[1957]: pppd 2.4.5 started by root, uid 0
May 10 20:58:27 mysystem NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
May 10 20:58:27 mysystem NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
May 10 20:58:27 mysystem pppd[1957]: Using interface ppp0
May 10 20:58:27 mysystem pppd[1957]: Connect: ppp0 <--> /dev/pts/0
May 10 20:58:28 mysystem pptp[1961]: nm-pptp-service-1955 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
May 10 20:58:28 mysystem pptp[1968]: nm-pptp-service-1955 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
May 10 20:58:28 mysystem pptp[1968]: nm-pptp-service-1955 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
May 10 20:58:28 mysystem pptp[1968]: nm-pptp-service-1955 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
May 10 20:58:29 mysystem pptp[1968]: nm-pptp-service-1955 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
May 10 20:58:29 mysystem pptp[1968]: nm-pptp-service-1955 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
May 10 20:58:29 mysystem pptp[1968]: nm-pptp-service-1955 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 256).
May 10 20:58:29 mysystem pptp[1968]: nm-pptp-service-1955 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
May 10 20:58:29 mysystem pptp[1968]: nm-pptp-service-1955 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is 00000000, recv_accm is FFFFFFFF
May 10 20:58:29 mysystem pptp[1968]: nm-pptp-service-1955 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
May 10 20:58:29 mysystem pptp[1968]: nm-pptp-service-1955 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
May 10 20:58:29 mysystem pptp[1968]: nm-pptp-service-1955 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is FFFFFFFF, recv_accm is FFFFFFFF
May 10 20:58:29 mysystem pptp[1968]: nm-pptp-service-1955 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
May 10 20:58:29 mysystem pppd[1957]: LCP terminated by peer (WM-z^CS^@<M-Mt^@^@^BM-3)
May 10 20:58:29 mysystem pptp[1968]: nm-pptp-service-1955 log[ctrlp_disp:pptp_ctrl.c:912]: Received Call Clear Request.
May 10 20:58:30 mysystem NetworkManager: <debug> [1273543110.002741] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1C:10:CC:33:2C (LOCALWIFI)
May 10 20:58:32 mysystem pppd[1957]: Connection terminated.
May 10 20:58:32 mysystem NetworkManager: <info>  VPN plugin failed: 1
May 10 20:58:32 mysystem NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
May 10 20:58:32 mysystem pptp[1961]: nm-pptp-service-1955 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
May 10 20:58:32 mysystem pppd[1957]: Modem hangup
May 10 20:58:32 mysystem pptp[1961]: nm-pptp-service-1955 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
May 10 20:58:32 mysystem pptp[1968]: nm-pptp-service-1955 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
May 10 20:58:32 mysystem pptp[1968]: nm-pptp-service-1955 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
May 10 20:58:32 mysystem pptp[1968]: nm-pptp-service-1955 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
May 10 20:58:32 mysystem NetworkManager: <info>  VPN plugin failed: 1
May 10 20:58:32 mysystem pppd[1957]: Exit.
May 10 20:58:32 mysystem NetworkManager: <info>  VPN plugin failed: 1
May 10 20:58:32 mysystem NetworkManager: <info>  VPN plugin state changed: 6
May 10 20:58:32 mysystem NetworkManager: <info>  VPN plugin state change reason: 0
May 10 20:58:32 mysystem NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.

```

---

### Post by giesen2 on 2010-05-12
any ideas?

---

### Post by Luffield on 2010-05-23
Are you using Ubuntu 10.04 64-bit? I'm suffering from this problem after upgrading from 9.10 64-bit, but I can connect to the VPN with my netbook (also a 9.10 to 10.04 upgrade, but 32-bit) and when I use Windows XP.

---

### Post by Omeil on 2010-05-23
Not 100% sure but this thread could be related [http://ubuntuforums.org/showthread.php?p=7002673]("http://ubuntuforums.org/showthread.php?p=7002673")

Regards,

Omeil

---

### Post by Omeil on 2010-09-22
Hi,

I figured out my VPN issue, it was related to the Maximum Transmission Unit Size for the network device, i think by default Ubuntu 10.04 64bit must be set at the maximum 1500 for larger packets to be sent, although since it takes slightly longer to receive the large packet the VPN thinks its lost connection (or along those lines) so it fails. try in the terminal:

sudo ifconfig eth0 MTU 300-1000

That will change the MTU for the network device eth0 and choose an MTU between 300-1000 for the VPN to stay connected (its what worked for me). Hope this helps.

Kind Regards,

Omeil:guitar:

---

### Post by lameei on 2010-09-28
This was exactly the solution. Thanks so much.

---

