---
title: "Mythbuntu Backend direct into Plasma via dlna?"
date: 2011-09-26
forum: Mythbuntu
---

### Post by Chris Grk-O-Matic on 2011-09-26
I should fix the title to say, minus the the router.
 
I have a Pioneer plasma with a ethernet jack that I am utilizing and when I watch video from my Mythbuntu backend via DD-WRT router on it it looks pretty good except that each hour-long video will end abruptly with an error code (a plasma generated code) at 42 minutes exactly. Also, if I try to fast forward it will screw up the the sync between the time code and the video track ~ like the video can't keep up with the video tracks time.
 
So I thought, or I thought I read somewhere that I can plug the backend directly into the plasma using a crossover cable. My question is, what network setting then should I use on the plasma and the backend? DHCP for both? 
 
I'm just wondering if I would get better performance with the router out of the equation, for testing purposes.
 
Thanks - Chris

---

### Post by nickrout on 2011-09-28
Well there will not be a dhcp serve in that setup so you can't use dhcp (except of course you can set up a dhcp server on the backend).

Easiest though to set up a static address on the backend and on the tv. Set backend to, say, 192.168.1.1 and the tv to 192.168.1.2.

---

### Post by Chris Grk-O-Matic on 2011-09-28
```
 
Easiest though to set up a static address on the backend and on the tv. Set backend to, say, 192.168.1.1 and the tv to 192.168.1.2.

```
Thanks. Please tell me what the DNS and Gateway settings should be on both the TV and the backend.
 
And the the ethernet cable has to be a crossover cable?
 
Thanks for the advice,
Chris

---

### Post by nickrout on 2011-09-28
> **Chris Grk-O-Matic said:**
> ```
 
Easiest though to set up a static address on the backend and on the tv. Set backend to, say, 192.168.1.1 and the tv to 192.168.1.2.

```
Thanks. Please tell me what the DNS and Gateway settings should be on both the TV and the backend.
 
And the the ethernet cable has to be a crossover cable?
 
Thanks for the advice,
Chris

Well you don't be running DNS will you? leave it blank. similarly you won't have access to the outside world so no Gateway is needed.

Although I doubt that the router is your problem!

---

