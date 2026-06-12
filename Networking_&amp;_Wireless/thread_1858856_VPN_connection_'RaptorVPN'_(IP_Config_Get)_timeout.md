---
title: "VPN connection 'RaptorVPN' (IP Config Get) timeout exceeded."
date: 2011-10-13
forum: Networking &amp; Wireless
---

### Post by lordbah on 2011-10-13
I can't get a VPN connection to RaptorVPN from Ubuntu 11.04. Log file implies to me that NetworkManager is timing out - but then packets continue to be received after that. Think it would work if the NM timeout could be increased? How can I do that?

```
Oct 13 04:30:03 penguin NetworkManager[18765]: <info> Starting VPN service 'pptp'...
Oct 13 04:30:03 penguin NetworkManager[18765]: <info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 7842
Oct 13 04:30:03 penguin NetworkManager[18765]: <info> VPN service 'pptp' appeared; activating connections
Oct 13 04:30:03 penguin NetworkManager[18765]: <info> VPN plugin state changed: 1
Oct 13 04:30:03 penguin NetworkManager[18765]: <info> VPN plugin state changed: 3
Oct 13 04:30:03 penguin NetworkManager[18765]: <info> VPN connection 'RaptorVPN' (Connect) reply received.
Oct 13 04:30:03 penguin pptp[7848]: nm-pptp-service-7842 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Oct 13 04:30:04 penguin pptp[7854]: nm-pptp-service-7842 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Oct 13 04:30:04 penguin pptp[7854]: nm-pptp-service-7842 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Oct 13 04:30:04 penguin pptp[7854]: nm-pptp-service-7842 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Oct 13 04:30:05 penguin pptp[7854]: nm-pptp-service-7842 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Oct 13 04:30:05 penguin pptp[7854]: nm-pptp-service-7842 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Oct 13 04:30:05 penguin pptp[7854]: nm-pptp-service-7842 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 64643).
Oct 13 04:30:43 penguin NetworkManager[18765]: <warn> **VPN connection 'RaptorVPN' (IP Config Get) timeout exceeded.**
Oct 13 04:30:43 penguin NetworkManager[18765]: <info> Policy set 'Wired connection 1' (eth3) as default for IPv4 routing and DNS.
Oct 13 04:30:48 penguin NetworkManager[18765]: <info> VPN service 'pptp' disappeared
Oct 13 04:31:04 penguin pptp[7854]: nm-pptp-service-7842 log[logecho:pptp_ctrl.c:677]: Echo Request received.
Oct 13 04:31:04 penguin pptp[7854]: nm-pptp-service-7842 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 6 'Echo-Reply'
Oct 13 04:32:04 penguin pptp[7854]: nm-pptp-service-7842 log[logecho:pptp_ctrl.c:677]: Echo Request received.
Oct 13 04:32:04 penguin pptp[7854]: nm-pptp-service-7842 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 6 'Echo-Reply'
Oct 13 04:32:04 penguin pptp[7854]: nm-pptp-service-7842 log[logecho:pptp_ctrl.c:677]: Echo Reply received.
Oct 13 04:32:05 penguin pptp[7854]: nm-pptp-service-7842 log[ctrlp_disp:pptp_ctrl.c:912]: Received Call Clear Request.
Oct 13 04:32:36 penguin pptp[7854]: nm-pptp-service-7842 log[pptp_read_some:pptp_ctrl.c:544]: read returned zero, peer has closed
Oct 13 04:32:36 penguin pptp[7854]: nm-pptp-service-7842 log[callmgr_main:pptp_callmgr.c:258]: Closing connection (shutdown)
Oct 13 04:32:36 penguin pptp[7854]: nm-pptp-service-7842 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Oct 13 04:32:36 penguin pptp[7854]: nm-pptp-service-7842 log[pptp_read_some:pptp_ctrl.c:544]: read returned zero, peer has closed
Oct 13 04:32:36 penguin pptp[7854]: nm-pptp-service-7842 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
```

---

### Post by lordbah on 2011-10-19
In that case ... any suggestions for a VPN which does work with Ubuntu which has a free trial?

---

### Post by cherva on 2011-10-19
OpenVPN is great... and it is free... :) I use it all the time.

---

### Post by lordbah on 2011-10-21
Do you mean openvpn.net, which apparently just redirects to privatetunnel.com for a free trial? I began reading their terms of service and didn't like what I saw.

---

