---
title: "Remote desktop"
date: 2010-04-16
forum: Networking &amp; Wireless
---

### Post by sn0m on 2010-04-16
Hi chaps
Can someone help me out with remote desktop.
It works fine within local network, but when I try it remotley over network it doesn't work.
Is there an option that has been disabled for security reasons.
I tried to google it but no luck.
Any help is appreciated.
Thanks
Sokol

---

### Post by new_tolinux on 2010-04-16
I don't know which port is used for Remote Desktop in Linux, but I guess you have to forward that port in your router.

A windows machine uses port 3389 by default if it is configured to access from a remote location. I'm sure that's not the same port as Linux (Ubuntu) uses.

---

### Post by terazen on 2010-04-16
Is the ip address of the device you want to connect to 192.168.x.x?  You can't connect to certain ip addresses remotely and would have to use port forwarding like new_tolinux said.

---

