---
title: "DHCP server only starts manually"
date: 2010-12-08
forum: Networking &amp; Wireless
---

### Post by john.bester on 2010-12-08
I have a LTSP server installation which works, but there is one nagging little problem. Whenever I restart the server, the dhcp3-server service does not start automatically. It tries to, but it seems like the networking is not ready at the time. Syslog contains this after a reboot:
dhcpd: Not configured to listen on any interfaces!

However, if I start dhcp3-server after the server has finished booting, it starts successfully and the message does not appear in syslog. All I can think is the problem is that I defined the static network address using the nm-connection-editor (std way - right click on nm-applet icon and choosing "edit connections"). Could it be that this address is only assigned to the interface after dhcp3-server attempted to start during boot-up?

---

