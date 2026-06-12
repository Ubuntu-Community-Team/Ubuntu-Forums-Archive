---
title: "Trouble with tc after upgrading to Karmix"
date: 2009-12-08
forum: Networking &amp; Wireless
---

### Post by kristrev on 2009-12-08
Hello,

After upgrading (clean install) my machine from 9.04 to 9.10, several tc scripts has stopped working. I have not been able to isolate or fix the problem, but it seems to be related to inheritance. For example, the following works in 9.04 but only gives a "RTNETLINK: Invalid argument" in 9.10:

tc qdisc add dev eth0 root handle 1: netem delay 10ms
tc qdisc add dev eth0 parent 1:1 handle 10: htb default 1 r2q 10

Has anyone experienced anything similar and/or have any ideas on how to fix it? When I checked the HTB FAQ, it said that the error is often caused by using the wrong version of tc for the current kernel, but I have found no way of upgrading tc (also, it shouldn't really be necessary).

-Kristian

---

### Post by ChrisKhoo on 2010-02-05
I have a similar problem as well. It has to do with attaching child layers to the queueing discipline (qdisc) tree when the root qdisc is netem. Adding child qdisc layers works fine if the root is cbq

Is there a bug reported for this issue? Is there a workaround for this?

Thanks.

---

### Post by ChrisKhoo on 2010-02-05
I've figured out the issue - netem no longer allows child layers to be added to it. 

In order to produce the equivalent combination of having netem and another queueing discipline, netem has to be the bottommost child.

E.g.

tc qdisc add dev eth0 root handle 1: tbf rate 256kbit buffer 1600 limit 3000
tc qdisc add dev eth0 parent 1: handle 10: netem delay 10ms

This works on Ubuntu 9.10.

---

### Post by PilotJLR on 2010-04-03
> **ChrisKhoo said:**
> I've figured out the issue - netem no longer allows child layers to be added to it. 

In order to produce the equivalent combination of having netem and another queueing discipline, netem has to be the bottommost child.

E.g.

tc qdisc add dev eth0 root handle 1: tbf rate 256kbit buffer 1600 limit 3000
tc qdisc add dev eth0 parent 1: handle 10: netem delay 10ms

This works on Ubuntu 9.10.

ChrisKhoo - thank you very much for posting this! I've been pulling out my hair for three days trying to figure this problem out on Fedora 12. Your solution works for me too.

Thanks!

---

### Post by hrodenburg on 2010-05-17
Yes, thanks for sharing. This is still an issue on Ubuntu 10.04. Chainloading with netem as bottommost did the trick.
Thanks again.

---

