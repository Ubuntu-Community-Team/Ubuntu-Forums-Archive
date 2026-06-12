---
title: "PPTP Stops Working"
date: 2009-10-08
forum: Networking &amp; Wireless
---

### Post by jcderr on 2009-10-08
I have pptpd installed and working. Generally, it only works for one connection, then I have to restart the service before any subsequent connections will work. During failure, the actual pptp connection will succeed and authenticate, but no data traffic is possible. I can't talk to the pptpd host or anything on the network beyond. Rehupping the pptpd daemon generally works, in that I can make one successful connection and during _that_ connection, I can talk to everyone.

Today, however, even rehupping does no good. I connect successfully, but at ~2 minutes, the connection resets. During the time it's connected, I can't make any connections to the remote network, nor can they connect to me. The server logs this to messages:

Oct  8 09:29:43 plnx pppd[21195]: No response to 4 echo-requests
Oct  8 09:29:43 plnx pppd[21195]: Serial link appears to be disconnected.
Oct  8 09:29:43 plnx pppd[21195]: Connect time 2.5 minutes.
Oct  8 09:29:43 plnx pppd[21195]: Sent 7444 bytes, received 6134 bytes.
Oct  8 09:29:46 plnx pppd[21195]: Connection terminated.
Oct  8 09:29:46 plnx pppd[21195]: Modem hangup
Oct  8 09:29:46 plnx pppd[21195]: Exit.

The client (running Mac OS X 10.6.1) logs:

Thu Oct  8 09:29:43 2009 : LCP terminated by peer (MPPE disabled)
Thu Oct  8 09:29:43 2009 : pptp_wait_input: Address deleted. previous interface setting (name: en0, address: 192.168.1.2), deleted interface setting (name: ppp0, family: PPP, address: 10.0.1.210, subnet: 255.0.0.0, destination: 10.0.1.200).
Thu Oct  8 09:29:46 2009 : PPTP error when reading socket : EOF
Thu Oct  8 09:29:46 2009 : PPTP error when reading header : read -1, expected 12 bytes
Thu Oct  8 09:29:46 2009 : Connection terminated.
Thu Oct  8 09:29:46 2009 : Connect time 2.5 minutes.
Thu Oct  8 09:29:46 2009 : Sent 17634 bytes, received 7444 bytes.
Thu Oct  8 09:29:46 2009 : PPTP disconnecting...
Thu Oct  8 09:29:46 2009 : PPTP disconnected

Any ideas?

---

### Post by jcderr on 2009-10-08
as a bonus: if i change localip in pptp.conf, it seems I can get the it-only-works-once behavior back. But now, I have to go change localip every single time I want to connect.... is there something janky going on in ip-up on my routing tables or something?

edit: this seems suboptimal too. for some reason, i'll get about a minute of joy, then i'll get total packet loss for about a minute. then joy again. lather, rinse, repeat.

---

