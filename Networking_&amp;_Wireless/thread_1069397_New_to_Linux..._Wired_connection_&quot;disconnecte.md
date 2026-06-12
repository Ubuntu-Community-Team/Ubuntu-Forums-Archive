---
title: "New to Linux... Wired connection &quot;disconnected&quot;"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by klunuts on 2009-02-13
Ah, this is driving me mad. So, I built my first computer yesterday (the parts were a birthday gift for my 15th birthday today (hooray)), and I hooked everything up correctly. I installed Ubuntu 8.10 correctly as well. At first, I plugged in the ethernet chord into the back of my computer and then straight into the base station just like you're suppose to, and it worked fine. But then, I ran update manager and restarted my machine today (about 45 minutes ago). For some reason, when it restarted, it said "Disconnected: The network connection has been disconnected." I could probably figure out what is wrong if I knew my way around Ubuntu (or just Linux for that matter), but I'm a Mac guy... So I don't know what I'm doing haha. Anyone think they could help me out? It would be much appreciated.

P.S. My wireless connection on my laptop (which I'm on right now), my mom's laptop, my brothers laptop, and my brother's desktop are all working fine right now... If that matters.

---

### Post by klunuts on 2009-02-13
_

---

### Post by ugm6hr on 2009-02-14
Give us (copy & paste) output from:

```
lspci
lshw -class network
ifconfig
```

When connected with wire.

---

### Post by tuskenraider on 2009-02-14
did you try restarting your switch/hub/router?  i had that issue the other day and i had to restart my switch and that fixed it..  just a thought....

---

### Post by mdhunn on 2009-02-14
Once in a great while I get some network wiredness too.  Try this:

1. Disable networking by right clicking the networking icon in your notification area.

2. Re-start your base station or router.

3. Re-enable networking on your computer.

Sometimes dhcp auto-configuration for things like your ip address sticks.  Some times it's the computer and, sometimes it's the router.  

COMPUTER:  Give me an ip!
ROUTER: I all ready gave you one!
COMPUTER: NO YOU DIDN'T
ROUTER:  TOO BAD
COMPUTER: I'm disconnected :(

---

### Post by tuskenraider on 2009-02-14
> **mdhunn said:**
> 
COMPUTER:  Give me an ip!
ROUTER: I all ready gave you one!
COMPUTER: NO YOU DIDN'T
ROUTER:  TOO BAD
COMPUTER: I'm disconnected :(


hilarity!  and very very true.

---

### Post by zander1013 on 2009-02-14
don't forget to try and restart your modem too! sometimes you have to do this to get a new dhcp ip address.

zander

---

### Post by klunuts on 2009-02-14
well i did everything mdhunn and zander1013 said to do, but it still won't work. If i hover my mouse over the icon when it's trying to connect, it says something about trying to get an adress from the wired connection.? Is there some setting I have to turn on or switch or something maybe?

---

