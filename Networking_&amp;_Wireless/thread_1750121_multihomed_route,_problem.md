---
title: "multihomed route, problem"
date: 2011-05-05
forum: Networking &amp; Wireless
---

### Post by 8Kuula on 2011-05-05
hmm, okay.
I have setup ubuntu server with two isp connection to internet (cable and adsl). Server box shares connections to local network too, so server box has total 3 nics, $nic1 and $nic2 are connections to internet, $nic0 is to local network.
$nic{0,1,2}_gw are gateways.

```
ip route add default scope global nexthop via $nic1_gw dev $nic1 weight 20 nexthop via $nic2_gw dev $nic2 weight 1
```
So with this (way i understand) routes that are created from server itself and from local network, are created 20 times more likely thru $nic1 than $nic2, and if $nic1 gets down routes are created thru $nic2 and if $nic2 gets down then routes go thru $nic1.

So in to "problem" part... everyting seems to work as intended until substained connection is created (like with games, Starcraft 2 and Black Ops with my tests). In some point connection gets disconnected. And question is, why?
If route to game server is created thru $nic1 then it should stay until not used anymore, right?

_Seems_ this is not case.

With "watch -n1 ip route show cache \| grep <gameserverIP>" runing and playing some black ops (easier to get gameserver ip).
Some point route switches from $nic1 to $nic2 and game disconnects, I think gameserver do not like that players IP changes on fly.

Route is in use so it should not make that switch, yet it does do it. Question is why?

---

