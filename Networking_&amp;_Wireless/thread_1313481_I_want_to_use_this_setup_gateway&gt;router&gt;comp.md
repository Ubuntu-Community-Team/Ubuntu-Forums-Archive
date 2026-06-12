---
title: "I want to use this setup gateway&gt;router&gt;computer"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by henryfranz2005 on 2009-11-03
Hi guys, I have a problem. My network setup is like this

GATEWAY > GATEWAY (WIFI router) > COMPUTER

all I want to do is to set my network like this

GATEWAY > Router ( WIFI - WRT45G) > Computer

-you may say I don't know what I'm saying but here's another problem because of this network setup. When I connected my computer via lan cable (which means it is connected like this Gatewat > Computer) Then I can see my website which is hosted on my computer. But when I use my router. I can't see (maybe because of double gateway?) I need help guys. Thanks.

---

### Post by hal10000 on 2009-11-03
> GATEWAY > GATEWAY (WIFI router) > COMPUTER

What is the first gateway? is it another router, a modem another pc or what else?

Post the outputs of [COLOR="Red"]ifconfig[/COLOR] and [COLOR="Red"]route[/COLOR]

---

### Post by henryfranz2005 on 2009-11-03
ok sir, 

the first gateway is the modem(adsl) then the second gateway is the router

---

### Post by hal10000 on 2009-11-03
There are two cases:

1.) You are connected via the wifi-router:
----> Your gateway is the wifi router, your modem is just your modem

2.) You are connected directly through your modem:
----> your gateway is your providers machine which you are connected via your modem,
and in this case your modem is also just your modem

> When I connected my computer via lan cable (which means it is connected like this Gatewat > Computer) Then I can see my website which is hosted on my computer. But when I use my router. I can't see (maybe because of double gateway?

What do you mean here?

e.g. if your computer is at home (and connected directly, without  the router), and you are at school or at work, can you see your website on your home-computer? Is it this, what you are talking about?

If so, then it's no wonder that you can't see it if your home-computer is connected via the router, because the router simply drops all incoming connections. But his is not a bug, it's a feature, because it prevents your computer from being hacked.

In other words: If you want your home-computer to be accessed from the internet, then it **must not **be connected behind a router. But take in mind that this can be a great security risk.

---

### Post by henryfranz2005 on 2009-11-04
ok sir thanks. Is there a work around so  I can still host websites on my laptop?

---

### Post by hal10000 on 2009-11-04
The workaround is to connect it directly to your modem withoüt a router between pc and modem.

---

### Post by henryfranz2005 on 2009-11-04
yeah. I think it's just the one. The only workaround and possibly the solution to my problem..

---

### Post by mpokrywka on 2009-11-05
OR, you can add so called "port forwarding" on router WRT54G, you can set it that incoming connections on port 80 will be forwarded to your laptop...

---

