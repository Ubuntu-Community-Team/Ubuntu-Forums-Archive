---
title: "default gateway pinging"
date: 2012-06-19
forum: Networking &amp; Wireless
---

### Post by fox hunter on 2012-06-19
Guys, this may be a silly question.In a private network (two laps are connected together for example)can we ping to the default gateway of the ip address? The three cases are 1)there is no 'physical' gateway. It is only specified in the configuration page 2)there is a router with an ip which is the default gateway. 3) There is a laptop which acts as the gateway.

Another doubt of mine is whether two hosts in two network(two computer with different network identifying prefix)can be connected directly(without any router in between) and pinged to each other or not? 
Thanks a lot for reading patiently through my rather long question(s)!!

---

### Post by rukiaEnix on 2012-06-19
You need a router to ping to different networks, or make one of your computers to act as a router.

---

### Post by fox hunter on 2012-06-20
Thanks a lot for answering one of my questions. Can you be so kind as to answer my first question also.The question is(pardon me for the small error in the initial posting.So I modified it):

Let there be a private network (two laptops are connected together for example). Can we ping to the ip address of the default gateway of the other laptop? The three cases are 1)there is no 'physical' gateway. It is only specified in the configuration page 2)there is a router with an ip which is the default gateway. 3) There is a laptop which acts as the gateway.

---

### Post by rukiaEnix on 2012-06-21
OK,

If the default gateway of the IP you want to ping is in the same network you can do it.

I still don't understand the first scenario.

Scenario 2: If the two laptops are on the same network of that router working as gateway you can ping it.

Scenario 3: If that laptop that works as gateway is also in the same network of the other two laptops you can ping it also.

All really depends on the network configuration.

---

### Post by fox hunter on 2012-06-22
Thanks a lot for your clarifications!!
What I maeant by the first scenario is this :suppose we setup a network with two hosts connected together trough a switch. I give  10.1.1.1 and 10.1.1.2 as the static IP address respectively and 10.1.1.4 and 10.1.1.5 as the default gateway address respectively, can I ping to 10.1.1.5 and 10.1.1.4 from 10.1.1.1. Clearly there is no host with this ip address. Its only that we have specified the default gateway address as so.

Please forgive me if my question is a stupid one.:)for I'm a newbie

---

### Post by rukiaEnix on 2012-06-22
If 10.1.1.5 and 10.1.1.4 are assign to a device, yes you can ping them because they are in the same network.

But if you just have those IP assign as the default gateway of host A and B but not assign as the IP of a device then you can't ping them. To ping to an IP it must be assign to a device, and that device has to be running.

---

### Post by fox hunter on 2012-06-23
Thanks a lot rukiaEnix !

---

### Post by rukiaEnix on 2012-06-23
You're welcome ;)

If you don't have more questions you should change this thread to solved.

---

