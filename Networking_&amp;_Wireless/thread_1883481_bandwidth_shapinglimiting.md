---
title: "bandwidth shaping/limiting"
date: 2011-11-19
forum: Networking &amp; Wireless
---

### Post by triscross on 2011-11-19
i have a ubuntu 10.4 server on my network and i have 3 other pc's connected to my network if i install another nic into my server then connect that to a old wireless router/switch ca i then limit the bandwidth of the computers connected the 2nd router
can i limit this by a percentage or just a figure in mbs


thanks

---

### Post by matt_symes on 2011-11-19
Hi

If you are going to use your router just as a switch (not a gateway, no dhcp etc) because your server has taken over this role then take a look at traffic control.

```
man tc
```You can limit bandwidth in kb, Mb etc. I am not sure about percentages. 

You may also want to limit the number of connections each client can make. For this you need the conntrack and connlimit modules. You can limit connections with iptables rules.

If the router is going to do this then you may want to flash it with dd-wrt. You can then ssh into the router and set traffic control manually. To limit the number of connections each client can make you need either to purchase the paid version of dd-wrt or build it yourself with the connlimit module installed.

I am currently looking into the second option as i did not receive an answer when i e-mailed them about getting a flash image for a particular router with that module installed.

Kind regards

---

### Post by triscross on 2011-11-19
my first thought was dd-wrt but i havent got a router handy that i can install it on 
i can use the router as a switch just turning off dhcp 
looking into man tc now i will probley need a guide :)

thanks for your help

---

### Post by matt_symes on 2011-11-19
Hi

No problem. Post back if you need more pointers. I am no expert on this by any means. I researched just enough to achieve my goals.

Another point; to test it after you have set it up use a line speed checker. I use broadbandspeedchecker because i am based in the UK *(i am in no way endorsing them above any other)*. You may want to use one nearer to your locale.

Just remember though, it does use up your bandwidth if you have that kind of contract with your ISP. I am lucky. I have no restricted cap per month. I just have to abide by a fair use policy.

Kind regards

---

