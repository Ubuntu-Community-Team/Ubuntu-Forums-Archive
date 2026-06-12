---
title: "Systemwide Proxy Settings"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by Vistro on 2009-12-28
First, I would like to say I mean proxy in that I want to point all internet connections to my Phone. I DO NOT mean that I want to use someone else's IP address to get past a forum block. I know that second meaning of proxy has become the default, but I think we can save a lot of time if we get that down. 

I have pulled open the Network Proxy box, and set it to localhost, 8181, then checked the "Use this for all services" box. Web, Secure Web, work fine. Anything that doesn't use Web, Secure Web, Ftp or Socks (what's listed in that box) WILL NOT WORK. See also: Ventrilo, Mangler, WoW. 

I tried the Apply System Wide, and entered my password in the two boxes it gave me, but nothing happened after that. I'm at least looking for a box saying "Settings Applied!"... the lack of any confirmation is very... for lack of the correct word, dissatisfying. 

How do I force (TEMPORARILY!!!! I have WiFi at home, but in the car, I must use my phone) Ubuntu to forward every last scrap of internet bandwidth to localhost:8181?

Thanks!

---

### Post by shredder12 on 2009-12-30
I think the trouble is that when you set the network proxy in System->preferences->network proxy you are probably overlooking the **ignored hosts** tab. If that's true then you will find that **localhost** and **127.0.0.1** are set to be ignored i.e. no proxy for them under any scenario.

I think removing those entries will solve your problem..

---

