---
title: "Splitting the internet downstream between 2 computers in a home network"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by cb951303 on 2009-01-29
Well, I don't know exactly what this is called but here is the situation.

I have 4Mbit unlimited adsl connection at home. It's distrubuted between 2 computers through a US Robotics router. When I start downloading something, my brother always complains about how he can't play WoW because of the latency eventhough I limit my download to something like 100kb/s. So I thought, I may shut his mouth once and for all by splitting the downstream exactly to 2 equal pieces. This way, eventhough he gets latency, I don't have to worry about it since we're using exactly the same amount of internet. Is there a way to do it? Should I buy a complicated router or something? 

Thanks in advance

---

### Post by sedawk on 2009-01-29
First, you can check when the problem starts, e.g. by pinging a (nearby) machine in the web while increasing your download bandwidth.

Next your router might have a feature called QoS (Quality of Service).
May be you can solve the problem by reconfiguring the router,
giving "higher priority" to WoW-traffic.

Then you might want to verify the speeds given in your posting again.
The fastest adsl I know can do 24 MBit downstream, which is
similar do a download speed of 2.4 MByte/s. In this case
a speed limit of 1.2 MByte/s would make sure that both computer
get a fair share of the network.

---

### Post by cb951303 on 2009-01-29
> **sedawk said:**
> First, you can check when the problem starts, e.g. by pinging a (nearby) machine in the web while increasing your download bandwidth.

Next your router might have a feature called QoS (Quality of Service).
May be you can solve the problem by reconfiguring the router,
giving "higher priority" to WoW-traffic.

Then you might want to verify the speeds given in your posting again.
The fastest adsl I know can do 24 MBit downstream, which is
similar do a download speed of 2.4 MByte/s. In this case
a speed limit of 1.2 MByte/s would make sure that both computer
get a fair share of the network.

There is Quality of Service panel in my router config page. I will try to configure it now but does giving higer priority to wow means I'm gonna use less bandwith? I want it to be 50:50...

Ooops, obviously I meant 4Mbit and 100kb/s :) sorry for that, correcting now...

---

### Post by cb951303 on 2009-01-29
Here is how my QoS page looks like.

The machine running WoW is on local IP 192.168.1.111 and the game uses port 3724.

My machine is on ip 192.168.1.101
The gateway/router is 192.168.1.1

So any idea how can I fill this form :)??

---

### Post by cb951303 on 2009-01-29
Apperently IPs are optional. I just typed in the port number and thats all. Working like charm. It didn't of course split the bandwith in half but it prioritizes WoW packets so that latency drops. And there isn't any siginificant drop on my download rates. A+ solution :popcorn:

Thanks

---

