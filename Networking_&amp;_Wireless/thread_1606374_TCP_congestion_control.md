---
title: "TCP congestion control"
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by night_fox on 2010-10-26
I found out that TCP uses a congestion control algorithm to become slower when the network gets congested. This works if everyone wants to be "nice" or is too ignorant to be "nasty" by turning it off, and always trying to get the maximum speed at the expense of other people.

Supposing, purely hypothetically, that someone was a mean cruel sociopath who doesn't give a damn about how fast other people's internet worked, How would he/she/they go about disabling TCP congestion control in ubuntu?

---

### Post by Brandon Williams on 2010-10-27
With a stock linux kernel, it is not possible to disable TCP congestion control. You can choose which congestion control algorithm your system uses, but you can't simply turn it off. This is because it simply does not make sense to do so. Congestion control is not about being "nice" to everyone else on the network ... it's about getting better performance for yourself by minimizing loss (and thus data retransmission) for your own connections. Generally speaking, a user who is trying to maximize throughput should be using some sort of congestion control algorithm.

On the other hand, a user who just wants to cause trouble for everyone else could write a TCP engine that runs outside of the kernel, sending and receiving packets using a raw socket (or something equivalent).

---

### Post by night_fox on 2010-10-29
But what about the slow start? Surely it's better to just risk firing off as packets as fast as possible to begin with? Especially when web browsing.

---

### Post by Brandon Williams on 2010-10-29
You're right that it will typically be the case that being optimistic in your initial cwnd value is a net benefit if you're typically transmitting a lot of data. However, there's no way to do that in a stock linux kernel. There are a few mitigating factors, though.

First, keep in mind that slow start isn't really "slow" ... it's actually the fast (exponential) part of window growth. Yes, the first couple of RTTs are slow, but it ramps up pretty fast. Also, if the remote machine is one that you communicated with recently, linux "remembers" the values that were in effect at that time so that it can use an optimistic cwnd ramp-up strategy.

Modifying the cwnd strategy would only help a lot if you are typically transmitting, but with web browsing you are typically receiving. Even with SSL connections, you will tend not to be sending very many packets in a row.

---

