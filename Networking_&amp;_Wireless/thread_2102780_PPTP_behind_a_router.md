---
title: "PPTP behind a router?"
date: 2013-01-08
forum: Networking &amp; Wireless
---

### Post by KisteBecks on 2013-01-08
hi,

i was unable to get a working PPTP connection with a free bodyvpn account through the network manager/vpn tab

my network setup:

client -> switch -> router

i already have a default route to the router which handles the dialup connection. im new to pptp and im assuming that it will create a new default route, is that right?

According to:
[https://help.ubuntu.com/community/VPNClient#Debugging_a_connection](https://help.ubuntu.com/community/VPNClient#Debugging_a_connection)

it might be possible to activate debugging informations with gconf-editor, but the path:
```

system/networking/vpn_connections

```does not exist on my ubuntu 12.04.1


so i used pptp-linux as command line client, i created the following files:

/etc/ppp/chap-secrets
```

myusernamefrombodyvpn PPTP mybodyvpnpassword *

```/etc/ppp/peers/bodyvpn
```

remotename bodyvpn
linkname bodyvpn
ipparam bodyvpn
pty "pptp pptp.bodyvpn.com --nolaunchpppd "
name mybodyvpnusername
usepeerdns
require-mppe
refuse-eap
noauth

# adopt defaults from the pptp-linux package
file /etc/ppp/options.pptp

```connection specific data comes from:
[http://www.bodvpn.com/how-to-create-a-vpn-connection-in-ubuntu/](http://www.bodvpn.com/how-to-create-a-vpn-connection-in-ubuntu/)


starting the connection via:
sudo pppd debug call bodyvpn

results in:
```

Jan  8 11:45:41 ws-b pppd[3868]: pppd 2.4.5 started by root, uid 0
Jan  8 11:45:41 ws-b pppd[3868]: using channel 4
Jan  8 11:45:41 ws-b NetworkManager[1116]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan  8 11:45:41 ws-b NetworkManager[1116]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jan  8 11:45:41 ws-b pppd[3868]: Using interface ppp0
Jan  8 11:45:41 ws-b pppd[3868]: Connect: ppp0 <--> /dev/pts/1
Jan  8 11:45:41 ws-b pptp[3872]: anon log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Jan  8 11:45:41 ws-b pptp[3878]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Jan  8 11:45:42 ws-b pppd[3868]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x3519781d> <pcomp> <accomp>]
Jan  8 11:46:12  pppd[3868]: last message repeated 9 times
Jan  8 11:46:12 ws-b pppd[3868]: LCP: timeout sending Config-Requests
Jan  8 11:46:12 ws-b pppd[3868]: Connection terminated.
Jan  8 11:46:12 ws-b avahi-daemon[1045]: Withdrawing workstation service for ppp0.
Jan  8 11:46:12 ws-b NetworkManager[1116]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan  8 11:46:12 ws-b pppd[3868]: Modem hangup
Jan  8 11:46:12 ws-b pppd[3868]: Waiting for 1 child processes...
Jan  8 11:46:12 ws-b pppd[3868]:   script pptp pptp.bodyvpn.com --nolaunchpppd , pid 3869
Jan  8 11:46:17 ws-b pppd[3868]: sending SIGTERM to process 3869
Jan  8 11:46:17 ws-b pppd[3868]: Exit.

```any idea whats wrong?

---

### Post by KisteBecks on 2013-01-08
somehow i managed to read "body"vpn when they are called "bod"vpn. 
changing all occourences to bodvpn results in this error:


also posted here: (longer lines)
[http://pastebin.ca/2300380](http://pastebin.ca/2300380)


```

Jan  8 12:45:50 ws-b pppd[4827]: pppd 2.4.5 started by root, uid 0
Jan  8 12:45:50 ws-b pppd[4827]: using channel 7
Jan  8 12:45:50 ws-b pppd[4827]: Using interface ppp0
Jan  8 12:45:50 ws-b pppd[4827]: Connect: ppp0 <--> /dev/pts/1
Jan  8 12:45:50 ws-b NetworkManager[1116]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan  8 12:45:50 ws-b NetworkManager[1116]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jan  8 12:45:50 ws-b pptp[4830]: anon log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Jan  8 12:45:50 ws-b pptp[4837]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Jan  8 12:45:50 ws-b pptp[4837]: anon log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Jan  8 12:45:50 ws-b pptp[4837]: anon log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Jan  8 12:45:51 ws-b pppd[4827]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xbb4e9294> <pcomp> <accomp>]
Jan  8 12:45:51 ws-b pptp[4837]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Jan  8 12:45:52 ws-b pptp[4837]: anon log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Jan  8 12:45:52 ws-b pptp[4837]: anon log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 52940).
Jan  8 12:45:52 ws-b pppd[4827]: rcvd [LCP ConfReq id=0x0 <mru 1400> <auth eap> <magic 0x3dfb2fc7> <pcomp> <accomp> <callback CBCP> <mrru 1614> <endpoint [local:7b.cd.ba.d4.08.3b.4d.4f.8b.30.67.bc.34.d7.f1.84.00.00.00.00]> < 17 04 19 03>]
Jan  8 12:45:52 ws-b pppd[4827]: No auth is possible
Jan  8 12:45:52 ws-b pppd[4827]: sent [LCP ConfRej id=0x0 <auth eap> <callback CBCP> <mrru 1614> < 17 04 19 03>]
Jan  8 12:45:52 ws-b pppd[4827]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xbb4e9294> <pcomp> <accomp>]
Jan  8 12:45:52 ws-b pppd[4827]: rcvd [LCP TermReq id=0x1 "=\37777777773/\37777777707\000<\37777777715t\000\000\003\37777777627"]
Jan  8 12:45:52 ws-b pppd[4827]: sent [LCP TermAck id=0x1]
Jan  8 12:45:53 ws-b pptp[4837]: anon log[ctrlp_disp:pptp_ctrl.c:912]: Received Call Clear Request.
Jan  8 12:45:54 ws-b pppd[4827]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xbb4e9294> <pcomp> <accomp>]
Jan  8 12:46:24  pppd[4827]: last message repeated 9 times
Jan  8 12:46:24 ws-b pppd[4827]: LCP: timeout sending Config-Requests
Jan  8 12:46:24 ws-b pppd[4827]: Connection terminated.
Jan  8 12:46:24 ws-b avahi-daemon[1045]: Withdrawing workstation service for ppp0.
Jan  8 12:46:24 ws-b NetworkManager[1116]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan  8 12:46:24 ws-b pppd[4827]: Modem hangup
Jan  8 12:46:24 ws-b pppd[4827]: Waiting for 1 child processes...
Jan  8 12:46:24 ws-b pppd[4827]:   script pptp pptp.bodvpn.com --nolaunchpppd , pid 4828
Jan  8 12:46:24 ws-b pptp[4830]: anon warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Jan  8 12:46:24 ws-b pptp[4830]: anon warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Jan  8 12:46:24 ws-b pptp[4837]: anon log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Jan  8 12:46:24 ws-b pptp[4837]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Jan  8 12:46:24 ws-b pptp[4837]: anon log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Jan  8 12:46:24 ws-b pppd[4827]: Script pptp pptp.bodvpn.com --nolaunchpppd  finished (pid 4828), status = 0x0
Jan  8 12:46:24 ws-b pppd[4827]: Exit.

```

---

### Post by Whoopie on 2013-01-08
Did you follow this howto? -> [http://www.bodvpn.com/how-to-create-a-vpn-connection-in-ubuntu/](http://www.bodvpn.com/how-to-create-a-vpn-connection-in-ubuntu/)

It shows that you should disable MPPE, but you enabled/forced it with require-mppe.

And your /etc/ppp/chap-secrets is wrong. Change "PPTP" to "*". Or change remotename in /etc/ppp/peers/bodvpn to "PPTP".

---

### Post by KisteBecks on 2013-01-09
new config:
```

remotename bodvpn
linkname bodvpn
ipparam bodvpn
pty "pptp pptp.bodvpn.com --nolaunchpppd "
name freebodyvpn6551
usepeerdns
#require-mppe
#refuse-eap
noauth
# adopt defaults from the pptp-linux package
file /etc/ppp/options.pptp

```
even without MPPE i get this:
```

Jan  9 12:05:36 ws-b pppd[7099]: pppd 2.4.5 started by root, uid 0
Jan  9 12:05:36 ws-b pppd[7099]: using channel 14
Jan  9 12:05:36 ws-b NetworkManager[1116]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan  9 12:05:36 ws-b NetworkManager[1116]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown
 configuration found.
Jan  9 12:05:36 ws-b pppd[7099]: Using interface ppp0
Jan  9 12:05:36 ws-b pppd[7099]: Connect: ppp0 <--> /dev/pts/1
Jan  9 12:05:36 ws-b pptp[7103]: anon log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Jan  9 12:05:36 ws-b pptp[7109]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Jan  9 12:05:36 ws-b pptp[7109]: anon log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Jan  9 12:05:36 ws-b pptp[7109]: anon log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Jan  9 12:05:37 ws-b pppd[7099]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xb02a77fc> <pcomp> <accomp>]
Jan  9 12:05:37 ws-b pptp[7109]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Jan  9 12:05:37 ws-b pptp[7109]: anon log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Jan  9 12:05:37 ws-b pptp[7109]: anon log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 27224).
Jan  9 12:05:37 ws-b pppd[7099]: rcvd [LCP ConfReq id=0x0 <mru 1400> <auth eap> <magic 0x7bbb1099> <pcomp> <accomp> <callback CBCP> <mrru 161
4> <endpoint [local:7b.cd.ba.d4.08.3b.4d.4f.8b.30.67.bc.34.d7.f1.84.00.00.00.00]> < 17 04 1a e3>]
Jan  9 12:05:37 ws-b pppd[7099]: No auth is possible
Jan  9 12:05:37 ws-b pppd[7099]: sent [LCP ConfRej id=0x0 <auth eap> <callback CBCP> <mrru 1614> < 17 04 1a e3>]
Jan  9 12:05:37 ws-b pppd[7099]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xb02a77fc> <pcomp> <accomp>]
Jan  9 12:05:37 ws-b pppd[7099]: rcvd [LCP TermReq id=0x1 "{\37777777673\020\37777777631\000<\37777777715t\000\000\003\37777777627"]
Jan  9 12:05:37 ws-b pppd[7099]: sent [LCP TermAck id=0x1]
Jan  9 12:05:37 ws-b pptp[7109]: anon log[ctrlp_disp:pptp_ctrl.c:912]: Received Call Clear Request.
Jan  9 12:05:40 ws-b pppd[7099]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xb02a77fc> <pcomp> <accomp>]
Jan  9 12:06:09  pppd[7099]: last message repeated 9 times
Jan  9 12:06:09 ws-b pptp[7109]: anon log[pptp_read_some:pptp_ctrl.c:544]: read returned zero, peer has closed
Jan  9 12:06:09 ws-b pptp[7109]: anon log[callmgr_main:pptp_callmgr.c:258]: Closing connection (shutdown)
Jan  9 12:06:09 ws-b pptp[7109]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Jan  9 12:06:09 ws-b pptp[7109]: anon log[pptp_read_some:pptp_ctrl.c:544]: read returned zero, peer has closed
Jan  9 12:06:09 ws-b pptp[7109]: anon log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Jan  9 12:06:09 ws-b pppd[7099]: Script pptp pptp.bodvpn.com --nolaunchpppd  finished (pid 7100), status = 0x0
Jan  9 12:06:09 ws-b pppd[7099]: Modem hangup
Jan  9 12:06:09 ws-b pppd[7099]: Connection terminated.


```

---

### Post by Whoopie on 2013-01-11
Again, please adopt your /etc/ppp/chap-secrets as decribed above.

---

