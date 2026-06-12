---
title: "Network Simulator 2 (ns 2.34) Simulating a blackhole"
date: 2010-10-20
forum: Networking &amp; Wireless
---

### Post by silentcoder89 on 2010-10-20
I'm trying to create a manual transmission of RREP packet to simulate a blackhole.
the following is how i do it :

if(rtable.rt_lookup(IP_BROADCAST)==0){
    rtable.rt_add(IP_BROADCAST);
}
sendReply(IP_BROADCAST, 1, index, 1000, MY_ROUTE_TIMEOUT, CURRENT_TIME);
rtable.rt_delete(IP_BROADCAST);

however the simulation fails with message :

ns: scheduler going backwards from .... to ....

i have suspected the incorrect argument value was CURRENT_TIME. But what else should i replace 
into it?

or did i used an incorrect approach?
Please help. I'm really stuck in here.

Any help is appreciated.
Thanks in advance.

---

### Post by silentcoder89 on 2010-10-21
Never mind. I found the cause -- i have to schedule the sendReply() function using TimerHandler.

---

