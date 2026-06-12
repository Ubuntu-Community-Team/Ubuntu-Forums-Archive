---
title: "KDE VPN Routing with network-daemon"
date: 2012-03-15
forum: Networking &amp; Wireless
---

### Post by moyam01 on 2012-03-15
Hello,

I'm trying to route traffic on my laptop so that all traffic will got through normally on local connection, except for when the resource neeeded is on the OpenVPN, in which case it uses the OpenVPN. I have succesfully made the OpenVPN connect, and with a straight tunnnel I am able to ping the server that I want. However. when I setup routing through daemon, there is no ping response to the server.

The setup is as follows in the Daemon:

Address: 192.168.X.X- the local IP adress of the server I want to contact (also houses OpenVPN server at home)
Netmask: 255.255.255.0- the local netmask at home
Gateway: - The gateway of the server at home? (This is a bit ambigous)
Metric: 1- I have no idea waht this is, sought out a guide and it said to put 1 in this window. If there is
an expalnation for what this is I would appreciate it.

"Use only for resources on this connection" is selected.

What am i missing?

Thanks,
moyam01

---

