---
title: "internet doesn't work with vpn"
date: 2009-10-01
forum: Networking &amp; Wireless
---

### Post by blob84 on 2009-10-01
Hi I have updgraded ubuntu to 8.04 lts, and now my swissvpn has problem,
I can connect but after 2 minutes it lost connection.
While I'm connected internet doesn't work,
I have port forwarding my router, in var/log/messages i get this:
```
Oct  1 13:02:54 munky-desktop pppd[6394]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Oct  1 13:02:54 munky-desktop pppd[6394]: pppd 2.4.5 started by root, uid 0
Oct  1 13:02:54 munky-desktop pppd[6394]: Using interface ppp0
Oct  1 13:02:54 munky-desktop pppd[6394]: Connect: ppp0 <--> /dev/pts/0
Oct  1 13:02:57 munky-desktop pppd[6394]: CHAP authentication succeeded
Oct  1 13:02:57 munky-desktop pppd[6394]: MPPE 128-bit stateless compression enabled
Oct  1 13:02:59 munky-desktop pppd[6394]: local  IP address 93.94.244.7
Oct  1 13:02:59 munky-desktop pppd[6394]: remote IP address 80.254.79.98
Oct  1 13:02:59 munky-desktop pppd[6394]: primary   DNS address 80.254.79.157
Oct  1 13:02:59 munky-desktop pppd[6394]: secondary DNS address 80.254.77.39
Oct  1 13:04:56 munky-desktop pppd[6394]: Modem hangup
Oct  1 13:04:56 munky-desktop pppd[6394]: Connect time 2.0 minutes.
Oct  1 13:04:56 munky-desktop pppd[6394]: Sent 403151237 bytes, received 0 bytes.
Oct  1 13:04:56 munky-desktop pppd[6394]: Connection terminated.
Oct  1 13:04:56 munky-desktop pppd[6394]: Terminating on signal 15
Oct  1 13:04:56 munky-desktop pppd[6394]: Exit.
```

---

### Post by blob84 on 2009-10-01
ok i solved adding manually a route:

1) add this route (192.168.1.1 is your router)
```
sudo route add connect.swissvpn.net gw 192.168.1.1 eth0
```

2) connect VPN

3) add (192.168.1.2 is your local lan address)
```
sudo route add connect.swissvpn.net gw 192.168.1.2 eht0
```

i don't know but it works

---

