---
title: "Vpn pptp"
date: 2010-09-04
forum: Networking &amp; Wireless
---

### Post by rikoshay on 2010-09-04
I use a commercial VPN service that I have configured through Network Manager. However, it is quite flaky and prone to disconnecting. I gather there is no way to make network manager automatically reconnect so I have tried to manually configure the connection using this guide - [http://pptpclient.sourceforge.net/howto-ubuntu.phtml](http://pptpclient.sourceforge.net/howto-ubuntu.phtml) which has a persist option.

When I ```
sudo pon $TUNNEL nodetach
``` I get a response that looks very much like it is connected. However, nothing is routing through this connection.

How do I get my web browser and other programs to go through the tunnel which they are currently all bypassing?

Thanks - using Jaunty.

---

### Post by rikoshay on 2010-09-05
OK - so I've worked out I need to alter the routing table to send all packets via ppp0 however, I am unable to successfully do this. I have tried: ```
route add -net 192.168.0.0 netmask 255.255.255.0 dev ppp0

``` which just breaks everything. Following the instructions from another website ```
sudo route del (IP address of ppp0)
sudo route del default
sudo route add default dev ppp0
```

This does something and I can see my browser trying to channel data through the tunnel (in the terminal where I started it) but still ultimately fails to work.

Does anyone know how I should be amending my routing table?

---

