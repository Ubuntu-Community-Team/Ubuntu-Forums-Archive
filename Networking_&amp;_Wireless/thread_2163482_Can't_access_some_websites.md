---
title: "Can't access some websites"
date: 2013-07-18
forum: Networking &amp; Wireless
---

### Post by liquidstone on 2013-07-18
I can't open some websites on the internet, it seems that my DSL connection permits it. (sites like opera.com, speedtest.net ...)
When i connect ethernet cable with my wireless router (note this is not anymore dsl connection, but a normal ethernet), i can open all those pages. It seems that there is something wrong with the DSL in Network Connections that permits me to open some webpages. 
How to fix this?

---

### Post by liquidstone on 2013-07-20
bump
ok i made video, [here]("http://www.youtube.com/watch?v=h1PIs_QXLKs&feature=youtu.be"). with pppoeconf everything its ok, but when i manage my connection with network manager, it blocks

---

### Post by DeathByDenim on 2013-07-20
Have you check the logs to see if there are any clues there? There should be some information regarding ppp in /var/log/syslog. Any errors or warnings in there?

---

### Post by liquidstone on 2013-07-20
this is suspicious: [http://pastebin.com/GgyRB1LV](http://pastebin.com/GgyRB1LV)

---

### Post by steeldriver on 2013-07-20
I guess it might be an MTU issue - check the MTU when you are using pppoeconf and again when you are using network manager (e.g. using ifconfig), if necessary adjust the network manager MTU down

---

### Post by liquidstone on 2013-07-20
its not the MTU, its 1480

---

### Post by steeldriver on 2013-07-20
sorry, I don't understand your network configuration - you have a modem? or a router? or both? are you physically bypassing the router and connecting directly to the modem when you switch from eth to ppp?

---

### Post by liquidstone on 2013-07-20
i have wireless internet with Ubiquiti antena, attached to sort-of router. It uses ad-hoc dsl connection. I also have wireless router from who i share internet in my house. When i make connection straight from the antena, i need to make dsl connection and it's only then when i have problems. When i use my wireless router, i don't have problems

---

### Post by Deorc on 2013-11-06
I have exactly the same problem as OP said. Any suggestion?

---

