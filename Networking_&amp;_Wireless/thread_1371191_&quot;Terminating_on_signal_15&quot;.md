---
title: "&quot;Terminating on signal 15&quot;"
date: 2010-01-03
forum: Networking &amp; Wireless
---

### Post by Ellimist on 2010-01-03
I'm using Ubuntu Hardy Heron. I'm getting connected automatically when I boot up. But when I disconnect and connect again, I don't get connected. If I try to connect again, it doesn't happen. Rather, I get connected and disconnected immediately. Here's a log :
```
Jan  3 15:26:08 ubuntu pppd[6721]: Plugin rp-pppoe.so loaded.
Jan  3 15:26:08 ubuntu pppd[6723]: pppd 2.4.4 started by root, uid 0
Jan  3 15:26:08 ubuntu pppd[6723]: PPP session is 8505
Jan  3 15:26:08 ubuntu pppd[6723]: Using interface ppp0
Jan  3 15:26:08 ubuntu pppd[6723]: Connect: ppp0 <--> eth0
Jan  3 15:26:08 ubuntu pppd[6723]: CHAP authentication succeeded: Authentication success,Welcome!
Jan  3 15:26:08 ubuntu pppd[6723]: CHAP authentication succeeded
Jan  3 15:26:08 ubuntu pppd[6723]: peer from calling number 00:E0:FC:4D:2E:C7 authorized
Jan  3 15:26:08 ubuntu pppd[6723]: replacing old default route to eth0 [192.168.1.1]
Jan  3 15:26:08 ubuntu pppd[6723]: local  IP address 59.93.209.231
Jan  3 15:26:08 ubuntu pppd[6723]: remote IP address 59.93.192.1
Jan  3 15:26:08 ubuntu pppd[6723]: primary   DNS address 218.248.255.193
Jan  3 15:26:08 ubuntu pppd[6723]: secondary DNS address 218.248.240.180
Jan  3 15:26:10 ubuntu pppd[6723]: Terminating on signal 15
Jan  3 15:26:10 ubuntu pppd[6723]: Connect time 0.1 minutes.
Jan  3 15:26:10 ubuntu pppd[6723]: Sent 40 bytes, received 58 bytes.
Jan  3 15:26:10 ubuntu pppd[6723]: restoring old default route to eth0 [192.168.1.1]
Jan  3 15:26:10 ubuntu pppd[6723]: Connection terminated.
Jan  3 15:26:12 ubuntu pppd[6723]: Exit.
Jan  3 15:26:30 ubuntu pppd[6978]: Plugin rp-pppoe.so loaded.
Jan  3 15:26:30 ubuntu pppd[6980]: pppd 2.4.4 started by root, uid 0
Jan  3 15:26:30 ubuntu pppd[6980]: PPP session is 4743
Jan  3 15:26:30 ubuntu pppd[6980]: Using interface ppp0
Jan  3 15:26:30 ubuntu pppd[6980]: Connect: ppp0 <--> eth0
Jan  3 15:26:30 ubuntu pppd[6980]: CHAP authentication succeeded: Authentication success,Welcome!
Jan  3 15:26:30 ubuntu pppd[6980]: CHAP authentication succeeded
Jan  3 15:26:30 ubuntu pppd[6980]: peer from calling number 00:E0:FC:4D:2E:C7 authorized
Jan  3 15:26:31 ubuntu pppd[6980]: replacing old default route to eth0 [192.168.1.1]
Jan  3 15:26:31 ubuntu pppd[6980]: local  IP address 59.93.208.250
Jan  3 15:26:31 ubuntu pppd[6980]: remote IP address 59.93.192.1
Jan  3 15:26:31 ubuntu pppd[6980]: primary   DNS address 218.248.255.193
Jan  3 15:26:31 ubuntu pppd[6980]: secondary DNS address 218.248.240.180
Jan  3 15:26:34 ubuntu pppd[6980]: Terminating on signal 15
Jan  3 15:26:34 ubuntu pppd[6980]: Connect time 0.1 minutes.
Jan  3 15:26:34 ubuntu pppd[6980]: Sent 432 bytes, received 563 bytes.
Jan  3 15:26:34 ubuntu pppd[6980]: restoring old default route to eth0 [192.168.1.1]
Jan  3 15:26:34 ubuntu pppd[6980]: Connection terminated.
Jan  3 15:26:34 ubuntu pppd[6980]: Exit.
```

I'm new to Ubuntu and *nix, so please bear my ignorance.

---

