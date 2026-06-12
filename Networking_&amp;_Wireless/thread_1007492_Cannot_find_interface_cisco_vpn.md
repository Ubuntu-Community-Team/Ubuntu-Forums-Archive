---
title: "Cannot find interface: cisco vpn"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by feenikz4180 on 2008-12-10
my Cisco vpn or vpnc used to work flawlessly without any disconnects on 8.04 but after upgrading to 8.10 - The vpn software lose their binding with the wlan0 interface intermittently into a session. They just random disconnect and the only way to connect to the vpn again is to reconnect to the network and then log in to the vpn.

This is the error on cisco vpn:
Your VPN connection is secure.

 cannot find interface for address: 172.28.37.228
cannot find interface for address: 172.28.37.228
Secure VPN Connection terminated locally by the Client
Reason: Lost contact with the security gateway. Check your network connection
Disconnecting the VPN connection.

I tried disabling IPv6 along with lower MTUs but it didnt help..

---

### Post by xscottx3 on 2008-12-14
I am having the exact same issue when connecting to my university's wireless. Once it disconnects me and gives the interface failure message I then have to reboot to be able to connect again. And within a short amount of time I get the same issue. Anyone have any ideas?

---

### Post by xscottx3 on 2008-12-14
I figured out a solution to the problem. Do away with Cisco VPN and use vpnc. Install it, reboot and then go to VPN connections, configure VPN, add, and then configure your VPN connection. Then connect to network and vpn. This seems to solve the problem and you are no longer kicked off the network ever. This worked for me, hopefully works for you, let me know please. Good luck.

---

