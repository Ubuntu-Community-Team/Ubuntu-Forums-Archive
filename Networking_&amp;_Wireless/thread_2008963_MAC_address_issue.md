---
title: "MAC address issue?"
date: 2012-06-23
forum: Networking &amp; Wireless
---

### Post by ogsarticuno on 2012-06-23
Hey guys, I'm sure variants of this question are asked all the time, but I haven't been able to find a thread anywhere that fixes my problem.  I'm trying to teach myself a little bit of networking/ gain competency with ubuntu, and I've arbitrarily decided to attempt changing my mac address.  Right now I'm tried two methods,

>  ifconfig eth0 down
>  ifconfig eth0 hw eth <insert desired mac address here>
>  ifconfig eth0 up

and

ifconfig eth0 down
macchanger -m <insert desired mac address here> eth0
ifconfig eth0 up.

Obviously, after typing the down command my internet connection dies, and just after I type "up" (but before I've reconnected), the new mac address sticks.  I think get a "disconnected" notification again, followed by a connection notice, following which my mac address has reset to its original state.  Is this because I'm doing something wrong? Or could it have something to do with my universities network?  I should add to this that I'm very inexperienced with both networking and ubuntu, so any help would be greatly appreciated.  Thanks

-Using Ubuntu btw

---

