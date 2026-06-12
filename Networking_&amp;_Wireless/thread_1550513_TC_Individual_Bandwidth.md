---
title: "TC Individual Bandwidth"
date: 2010-08-11
forum: Networking &amp; Wireless
---

### Post by nrs on 2010-08-11
My objective: To give each IP in a subnet it's own bandwidth limit. 

I've looked at this.
```

    
      tc qdisc add dev $DEV root handle 1: cbq avpkt 1000 bandwidth 10mbit 

      tc class add dev $DEV parent 1: classid 1:1 cbq rate 512kbit \
      allot 1500 prio 5 bounded isolated 

      tc filter add dev $DEV parent 1: protocol ip prio 16 u32 \
      match ip dst 10.8.0.1/24 flowid 1:1

```The problem: The bandwidth ceiling is collectively shared amongst 10.8.0.1/24 (512/255). What I want is for 
everyone in 10.8.0.1/24 to have a max of 512 to themselves. Is there a sane way I can accomplish
this or do I have to repeat these commands 255 times creating new classes and matching each IP individually? Would that even work?

---

