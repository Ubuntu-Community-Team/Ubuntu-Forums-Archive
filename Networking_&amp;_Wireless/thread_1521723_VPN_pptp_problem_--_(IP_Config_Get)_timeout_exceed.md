---
title: "VPN pptp problem -- (IP Config Get) timeout exceeded"
date: 2010-07-01
forum: Networking &amp; Wireless
---

### Post by d4y on 2010-07-01
Hi!

I'm trying to configure internet access using KDE network manager. Added new VPN connection, set gateway and other options but connection breaks. Here is /var/log/daemon.log
```

Jul  1 17:35:22 dvinokurov-desktop NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Jul  1 17:35:22 dvinokurov-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 1761
Jul  1 17:35:22 dvinokurov-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Jul  1 17:35:22 dvinokurov-desktop NetworkManager: <info>  VPN plugin state changed: 1
Jul  1 17:35:22 dvinokurov-desktop NetworkManager: <info>  VPN plugin state changed: 3
Jul  1 17:35:22 dvinokurov-desktop NetworkManager: <info>  VPN connection 'foovpn' (Connect) reply received.
Jul  1 17:35:22 dvinokurov-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jul  1 17:35:22 dvinokurov-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jul  1 17:35:22 dvinokurov-desktop pptp[1766]: nm-pptp-service-1761 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Jul  1 17:35:22 dvinokurov-desktop pptp[1773]: nm-pptp-service-1761 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Jul  1 17:35:22 dvinokurov-desktop pptp[1773]: nm-pptp-service-1761 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Jul  1 17:35:22 dvinokurov-desktop pptp[1773]: nm-pptp-service-1761 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Jul  1 17:35:23 dvinokurov-desktop pptp[1773]: nm-pptp-service-1761 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Jul  1 17:35:23 dvinokurov-desktop pptp[1773]: nm-pptp-service-1761 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Jul  1 17:35:23 dvinokurov-desktop pptp[1773]: nm-pptp-service-1761 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 143).
Jul  1 17:36:02 dvinokurov-desktop NetworkManager: <info>  VPN connection 'foovpn' (IP Config Get) timeout exceeded.
Jul  1 17:36:02 dvinokurov-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Jul  1 17:36:02 dvinokurov-desktop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jul  1 17:36:02 dvinokurov-desktop pptp[1766]: nm-pptp-service-1761 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Jul  1 17:36:02 dvinokurov-desktop pptp[1766]: nm-pptp-service-1761 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Jul  1 17:36:02 dvinokurov-desktop pptp[1773]: nm-pptp-service-1761 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Jul  1 17:36:02 dvinokurov-desktop pptp[1773]: nm-pptp-service-1761 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Jul  1 17:36:02 dvinokurov-desktop pptp[1773]: nm-pptp-service-1761 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)

```As I understand the main problem is in "(IP Config Get) timeout exceeded". Could anybody suggest a way to solve this problem?

Thanks

---

### Post by jonobr on 2010-07-01
Given the stage at which this fails (right around establishment of GRE
(generic routing encapsulation) it looks as though your blocked from establishing the GRE tunnel.
Do you have control over your own firewall?

You should look to see if port 1723 (PPTP) for source and destination is allowed.

Some routers have a button you check which allows these port numbers and essentially allow traffic to "passthrough"

See my linksys config below, which has a tab specifically for VPN and enabling/disabling ipsec/L2TP/PPTP

---

### Post by d4y on 2010-07-06
Sorry for 2 duplicates of this thread, got troubles with internet connection, browser showed errors when I tried to post, so I posted from another PC. Haven't noticed that posts were posted, my bad.

> **jonobr said:**
> Given the stage at which this fails (right around establishment of GRE
(generic routing encapsulation) it looks as though your blocked from establishing the GRE tunnel.
Do you have control over your own firewall?

You should look to see if port 1723 (PPTP) for source and destination is allowed.

Some routers have a button you check which allows these port numbers and essentially allow traffic to "passthrough"

See my linksys config below, which has a tab specifically for VPN and enabling/disabling ipsec/L2TP/PPTP

I could connect to VPN from Windows PC from same network and I have no installed firewall on my Kubuntu PC, so I don't think that problem is in firewall. Nevertheless, I checked it, I tried to scan VPN server using
```

$ sudo nmap -p 1723 172.16.10.70

```and got
```

Starting Nmap 5.00 ( http://nmap.org ) at 2010-07-06 15:52 YEKST
Interesting ports on 172.16.10.70:
PORT     STATE SERVICE
1723/tcp open  pptp

Nmap done: 1 IP address (1 host up) scanned in 0.17 seconds

```So seems like problem is in VPN configuration on Kubuntu side.

---

### Post by jonobr on 2010-07-06
mmmm.... you did a good test which marrows it down to the ubuntu box.

Im wondering if this is something to do with MTU sizes

There was previous issues where the MTU size going over PPTP was too large cuasing connections to fail.

---

### Post by RiffTumbleweed on 2011-04-05
I had exactly this problem and on a whim removed the *wins* entry from /etc/nsswitch.conf hosts line and presto, everything worked again.:guitar:

---

