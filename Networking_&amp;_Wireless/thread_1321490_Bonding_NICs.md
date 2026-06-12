---
title: "Bonding NICs"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by dvirdc on 2009-11-10
Hey,

I wanna bond two NICs: Eth0 + Wlan0. they're both installed on one PC.
Now- is it possible to gain more BW if I connect each to a different network?
How can I do this?

Cheers

---

### Post by BatsotO on 2009-11-10
What i know when you do bonding you need the confirm that your isp support this configuration. The cheaper way will be load balancing, and easily applied for router using pfsense. With bonding you can gain more bandwith, unlike load balancing.

---

### Post by dvirdc on 2009-11-10
well, if i do use load balancing, how does it help me?
i mean, do i get something out of that?
can i connect using two different nics to two different networks and use their both bandwidth?


thanks

---

### Post by unlimitedme on 2009-11-10
Just like BatsotO explained earlier, 
By bonding your nic doesn't mean you will get both capacity.

Try to search more on load balancing term.

---

### Post by BatsotO on 2009-11-10
Depend on how many pc in your network connect to internet, if it only one, than load balancing wont help much, because load balancing will only balancing the load into different connection so lighten the burden of each one, like having two horses pulling the cart, it wont have double speed, but if the load is heavy like 10 or more pcs accessing the net, it helps.
What i know is if you need aggregated bandwidth from two different connection, the isp needs to bond the two connection to achieve double bandwidth, will need routers on your side and isp's side, and if you use two different providers i believe it's impossible.

---

### Post by dvirdc on 2009-11-10
what about link aggregation? 
do you know how to set it up?

---

### Post by BatsotO on 2009-11-10
I believe that is the way to overcome network traffic above the max capability of one NIC. I only have experience with load balancing with pfsense, so i don't have to worry about peak connection on one line coz i have second line that still do the job, but still it not doubled the bandwidth. And since my isp offer twice bandwidth than what i have now, it is cheaper to simply upgrade the connection if i need one. What i know is merging 2 lines means that those 2 lines must act like 1 line, which involve merging 2 ips in to 1 and that is impossible when the 2 lines comes from different isp. someone correct me if i'm wrong.

---

### Post by dvirdc on 2009-11-10
well thx anyway,

any ideas anyone?
):P

---

