---
title: "How to add routes to Network Manager GUI Applet in Ubuntu Lucid Lynx 10.04?"
date: 2010-10-12
forum: Networking &amp; Wireless
---

### Post by exodus on 2010-10-12
Greetings folks!

I recently successfully setup a PPTP connection to my company's VPN. I used the Network Manager GUI applet that comes by default with Ubuntu Lucid Lynx 10.04 (64 bit version).

In my further research, I found that after successfully connecting you need to setup ROUTES to be able to browse/access other machines and services behind the PPTP server.

So I went to the command line and added the following to make it work:
```
 route add -net 192.168.10.0 netmask 255.255.255.0 dev ppp0
```

My question is how can the above route's equivalent be entered in the Network Manager GUI applet over here
[IMG]http://img259.imageshack.us/img259/4240/screenshoteditingipv4ro.png[/IMG]

You can get to the adding route windows by following these steps:
**System -> Preferences -> Network Connections -> VPN(Tab) -> Select existing VPN / Add new VPN -> Edit(Button) -> IPv4 Settings (Tab) -> Routes (Button)**

If I can figure this out, it will be peace of mind for me!

---

