---
title: "Squid via Network Wireless Router &amp; Wireless Clients"
date: 2012-07-02
forum: Networking &amp; Wireless
---

### Post by stylemessiah on 2012-07-02
Hopefully this is a simple question, with an equally quick answer.

I have set up traditional squid setups before, with the 2 NIC setup.

This time though i have only a wireless router connected via ethernet to the squid box (1 NIC only).

All clients will connect to the squid box via the wireless router.

i.e. 
```

Wireless Client Laptops
|     
\/
Wireless Router/ADSL2 Modem ---- > Interwebs
|  /\ 
\/  |
Squid
```So my question (and im probably looking for reinforcement/outright ridicule for my own thoughts) is 

"Whats the best way to implement this?"

Is it as simple as forwarding all traffic from the router port 80 to the squid box in the router config and running the squid box in transparent mode.

Or

The above but conventional with proxy set manually on each client

Or neither, and you have a more sane approach

Any help will be most appreciated

Detailed responses get a cookie

---

### Post by stylemessiah on 2012-07-06
*bump*

Anyone?

---

