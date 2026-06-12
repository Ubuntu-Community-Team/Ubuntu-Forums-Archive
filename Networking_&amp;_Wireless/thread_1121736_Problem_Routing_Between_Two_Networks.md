---
title: "Problem Routing Between Two Networks"
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by igb on 2009-04-10
I have a network based on the 192.168.0.x range with netmask 255.255.255.0. I also have one computer with two network cards:

wlan0 192.168.0.80
eth0 192.168.1.2

The 192.168.1.x network will have various ip cameras attached. What I want is to be able to access the webcams from the 192.168.0.x network. I have enabled ip forwarding on the computer with the two network cards. From that box I can ping etho at 192.168.1.2 and a webcam at 192.168.1.26.

On another computer on the 192.168.0.x network I have added the following route:

route add -net 192.168.1.0 netmask 255.255.255.0 eth0

from that computer I can ping 192.168.1.2, but not 192.168.1.26. Having spent a day reading about routing and experimenting, I still don't understand what I am doing wrong. Can someone please help me out.

Thanks,

Ian.

---

### Post by superprash2003 on 2009-04-10
[http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/](http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/)

---

### Post by iponeverything on 2009-04-10
Turn on ip forwarding.

```
sudo echo 1 > /proc/sys/net/ipv4/conf/all/forwarding

```
make sure that the devices on 192.168.0.0/24 have a route for 192.168.1.0/24 pointing to 192.168.0.80 as the gateway and that devices on 192.168.1.0/24 have a route to 92.168.0.0/24 with 192.168.1.2 as the gateway.

---

