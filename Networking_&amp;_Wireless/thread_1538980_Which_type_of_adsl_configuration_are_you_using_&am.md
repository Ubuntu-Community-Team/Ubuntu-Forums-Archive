---
title: "Which type of adsl configuration are you using &amp; why?"
date: 2010-07-26
forum: Networking &amp; Wireless
---

### Post by linuxyogi on 2010-07-26
As we all know there are two ways one can configure adsl modem/router ----

(1) pppoe & (2) bridge mode.

I used pppoe mode for over 4 years.

Now I connect using bridge mode.

Why? 

There are both advantages & disadvantages in both the configuration types.

**_pppoe_**

_**_Advantage
In pppoe mode the main advantage is (in most cases) the adsl router's inbuilt firewall provides a primary line of defense against any kind of intrusion attempts from the internet. Your OS's software firewall is the next thing that is suppose to do the same.

_*Disadvantage*_

The main disadvantage is if you (for whatever reason) wan't to reset/redial your pppoe connection you need to hard reset the router. Now , as I have learned from my own expierience, the more you switch your router on & off the fast it will die.


**_Bridge Mode_**

*_Advantage_*

The main advantage is that you don't need to reset your modem to connect/reconnect because you are using your OS's dialer. This in a way prevents premature failure of the router. 

*_Disadvantage_* 

The main disadvantage is in bridge mode you cannot use your router's inbuilt firewall. Personally I trust Ubuntu's firewall completely but still having 2 is better than having 1.

---

### Post by dineshs on 2010-07-26
I use PPPoE mode because I can share the connection.I use a 4 port modem to connect other 2 computers.If I use bridge mode I will need another NIC card and a switch.Am I right?

---

### Post by linuxyogi on 2010-07-26
> **dineshs said:**
> I use PPPoE mode because I can share the connection.I use a 4 port modem to connect other 2 computers.If I use bridge mode I will need another NIC card and a switch.Am I right?

Yes, in your situation if you use bridge mode ---

(a) At least one pc must will have to be equipped with  two lan adapters.
This pc will act as a gateway for the others PCs & must be kept running if other PCs on the network needs constant internet connectivity .

(b) And yes, you will also need to install a switch.

Thanks for your reply.

---

