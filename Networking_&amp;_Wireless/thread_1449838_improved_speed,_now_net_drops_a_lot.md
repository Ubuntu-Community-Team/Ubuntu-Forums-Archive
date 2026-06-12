---
title: "improved speed, now net drops a lot"
date: 2010-04-08
forum: Networking &amp; Wireless
---

### Post by rcayea on 2010-04-08
Hi everyone,

I was having terribly slow internet speed with my wireless setup. I followed someone's advice and now my internet speed is flying. However, now I lose connection a lot - almost once every few minutes. Is there any reason for the changes listed below to make me lose connection so easily?

SETUP:
Ubuntu 910 - 64Bit
Wireless Router: WRT160N
Wireless Card: PCI Asus PCE N13

Changes that improved speed, but killed stability:

Radio Band frequency should be 20 MHZ, 
standard channel change to 11 
advanced wireless settings should be Beacon Interval 2306
Rts thres = 2307 
Disable the Security easy setup*option.
Uncheck the Block Anonymous Internet Requests & reduce the MTU size to* 1400 

thanks,
Randy

---

### Post by rcayea on 2010-04-08
I bump in hope of getting some advice.

---

### Post by arjuntank on 2010-04-08
may be this would help:
[http://homecommunity.cisco.com/t5/Wireless-Routers/Problems-with-WRT160N/m-p/158809]("http://homecommunity.cisco.com/t5/Wireless-Routers/Problems-with-WRT160N/m-p/158809")

i would change the DNS servers to check whether its a hardware issue or the DNS. i would also change the channel to see if that helps. i think default is auto, but you can change it to 11 or something else. this can help if local noise is causing the problem. i am not entirely sure though.

---

### Post by rcayea on 2010-04-08
thanks for the link, arjuntank.

---

