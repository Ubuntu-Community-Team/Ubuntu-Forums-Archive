---
title: "Making two browsers use two different active network connections"
date: 2013-09-04
forum: Networking &amp; Wireless
---

### Post by almikul on 2013-09-04
I have two wired connections: connection A is from work and connection B is from USB phone tethering (or wi-fi). I would like to do work-related activities with browser A (let's say Firefox) and all leisure browsing with browser B (Chrome). Is there any way to do that in Ubuntu? Maybe, I can create some local proxy set-up to utilise only a specific connection and then tell the browser to use this proxy? 

Your input would be highly appreciated :)

---

### Post by houstonbofh on 2013-09-04
You would need more than just a local proxy.  You simply can not have more than one default gateway, and that is how you know the "path to the Internet" for the entire system.  You would need a proxy on the local subnet of one network and the default gateway on the other network to do what you want.

(Short of a complex load balancing routing system)

---

### Post by almikul on 2013-09-05
Thanks for the response. Let's simplify the task then.

I have eth0 and wlna0 active connections. The default route for eth0 is 10.0.0.0 and for wlan0 it is 20.0.0.0. Suppose, my IP addresses on eth0 and wlan0 are 10.0.0.1 and 20.0.0.1, respectively. Now, default traffic goes via 10.0.0.0 (eth0), but I would like to go to some website through 20.0.0.0 (wlan0). 

Let's say I want to go to [www.google.com](www.google.com) only through wlan0. Can I set up a route to achieve this goal? I tried ```
sudo ip route add 74.125.224.83 via 20.0.0.0 dev wlan0
```, but it did not work, as google website would not load (would be waiting a long time and then showing 404). I got this 74.125.224.83 IP for [www.google.com](www.google.com) by pinging. Now, this task should be a piece of cake for networking guys ;-)

---

### Post by almikul on 2013-09-05
I did some experimenting, and I noticed that I can switch between network connections for *default* traffic but individual IP addresses still do not work. For instance, doing:```
sudo ip route del default
sudo ip route add default via 20.0.0.0 dev wlan0
``` will work, but if I want to specify a particular IP or a subnet: ```
sudo ip route add <specific IP> via 20.0.0.0 dev wlan0
``` it does not work. Maybe, I am not specifying destination IP or subnet correctly?

---

### Post by houstonbofh on 2013-09-06
Routes are for networks, not addresses, and networks all have netmasks.
```

ip route add 74.125.224.0/24 via 20.0.0.1 dev wlan0

```
Try that.

---

### Post by almikul on 2013-09-11
It works, but only if I add "proto kernel" afterwards. For example: ```
ip route add 74.125.224.0/24 via 20.0.0.1 dev wlan0 proto kernel
```
I don't even know what options "proto kernel" sets, but it works for now ;) Thanks, man!

---

