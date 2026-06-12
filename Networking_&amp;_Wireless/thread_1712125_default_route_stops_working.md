---
title: "default route stops working"
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by luvqry on 2011-03-22
Hi there,

I'm currently working with Ubuntu 10.10.

I wanted to add a default route to a gateway named ppp0.
I did it with the command

> route add default ppp0

It works ok. But then from time to time it suddenly stops and I have to go back again to the server and retype the command. I'm clueless as to why is it happening. I can assure no one is working at the server or doing anything over there.

Does anyone know causes that might be triggering route default to stop working?
Btw where is the best place to add this command so it will be executed automatically on start-up and without needing to login to the server?

thanks.

---

### Post by sedawk on 2011-03-22
By entering a simple "route" you can see the existing
routes.

Is the default route visible with "route" if it stops working?
Or is it really gone from the output of "route"?

Let's assume the route is missing, then you can
check which of the log files in /var/log has changes
recently and have a look at those.
Is it possible that ppp0 is resetting for some reason
and therefore the routing information is gone?
(In that case the normal networking scripts should be
 used to set the route).

---

### Post by luvqry on 2011-03-23
thanks for ur tips.

It happened twice the last 2 days when usually it would do only a time per week.

I look at the logs as you said and I believe those lines below can give me a hint as to where I should look for the problem as the time and date seems to be close of the time I get the issues.

Anyone can help me to understand what's going on at those lines?

```
Mar 22 19:28:40 SERVER avahi-daemon[767]: Withdrawing workstation service for ppp0.
Mar 22 19:28:40 SERVER NetworkManager[762]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Mar 22 19:31:31 SERVER NetworkManager[762]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Mar 22 19:31:31 SERVER NetworkManager[762]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Mar 22 19:31:31 SERVER modem-manager: (net/ppp0): could not get port's parent device
Mar 22 19:38:17 SERVER dhclient: DHCPREQUEST of 10.10.36.204 on eth1 to 10.10.36.8 port 67

```

---

### Post by leg on 2011-03-23
I think you need to go to the [dhcp.conf]("http://www.linuxmanpages.com/man5/dhcpd.conf.5.php") file and set the name of your route there. I had a similar problem with laptop and my router and I used this file to set my name server. Maybe you could use the file to set your gateway.

---

### Post by trippedn on 2011-03-28
For whatever reason, the connection is being dropped and reset.

Gnome Network Manager is re-executing the scripts and its configuration to bring the interfaces back up.

By setting the route manually via the command line, you are adding / configuring a route that is not in the network manager's configuration.

Open up the network manager and look for your connection. It should be under the PPP tab (I think). There will be a connection that is probably named something similar to Auto PPP0 or PPP0 (Auto).

Edit that connection. You can do two things here -- set the route in here, or, uncheck the 'Use Automatically' setting. If you do the later, you will need to set the information by hand (/etc/network/interfaces). With this case, it should be relatively straight forward as there should be other examples in the file to follow -- or you may try a man interfaces (or reply here and ask for help too :)).

EDIT: It looks like the network manager has changed for 10.10? Let me know if you need help.

---

### Post by luvqry on 2011-03-28
Thank you all.
I will get time this week to check all the things you mentioned and maybe I will reply asking for more help. I'm really grateful for all the tips I got from you as it will give me a direction to follow.

---

