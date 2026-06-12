---
title: "cable modem ---&gt; gigabit switch --&gt;computers? no router?"
date: 2013-01-10
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2013-01-10
what would happen if you did that?

or to eliminate router, would you have to setup ubuntu router as a router?

so it would then be 

cable modem ---> ubuntu router -->gigabit switch -->computers?

I have been interested in using wired gigabit, so was thinking of a gigabit switch and get rid of fast Ethernet routers (the fast Ethernet is a gimmicky slogan as it is so slow compared to gigabit)

Then for wireless, attach wireless router off the gigabit switch or attach wireless router off a second nic on the pc.

---

### Post by Doug S on 2013-01-11
> cable modem ---> gigabit switch -->computers? no router?
what would happen if you did that?It depends on how many IP addresses your ISP gives you. In my case I have 2 IP addresses and can do exactly what you show with two computers (but actually I use use two routers, one of which is an Ubuntu server computer).> or to eliminate router, would you have to setup ubuntu router as a router?You would not be eliminating the router, but rather your router is an ubuntu computer. Confusing.> so it would then be
cable modem ---> ubuntu router -->gigabit switch -->computers?
I have been interested in using wired gigabit, so was thinking of a gigabit switch and get rid of fast Ethernet routers (the fast Ethernet is a gimmicky slogan as it is so slow compared to gigabit)
Then for wireless, attach wireless router off the gigabit switch or ...Yes, that is exacly how I have my network configured, except that I have my wireless router configured as a switch instead of a router. Then everything on my LAN is on one tidy little sub-net and I do not have to think much about the wireless stuff.

---

### Post by sdowney717 on 2013-01-13
I have decided to buy a 5 port gigabit switch and then forget about using ubuntu as a router handing out DHCP as in 'share this connection to other computers'

Then you network is dependent on the ubuntu PC working.

My gigabit switch is Trendnet TEG-S50g I got used for $15 off ebay. It is 3 months old. Some of these switches like the cisco ones on newegg get bad reviews as the capacitors dry up inside after 2 years or they get hot and have noisy fans.

So my network will be

cable modem -- wireless router -- gigabit switch -- up to 4 PC's

And I can plug in my printer and other items to the wireless router's ports.

Since there will be only one router, everything will be on the same subnet.

---

### Post by redmk2 on 2013-01-13
> **sdowney717 said:**
> ...the fast Ethernet is a gimmicky slogan as it is so slow compared to gigabit...
But 10X faster that Ethernet 10BaseT that it replaced.

---

