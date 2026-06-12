---
title: "Unbuntu does not see my router"
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by singlemanriot on 2008-12-19
I have just got into ubuntu 8.10 everything works barring one thing, no matter what I try ubuntu will not find my Linksys wag54gs. Now i know that wireless works because i have had it connected to a Netgear router at my girlfriends house without issue it also picks up every other router in the area. I know there is no issue with the router as windows will connect fine(also wired conections to it work fine). I have an intel 4965 wireless card and I am using Network manager. I have tried Wicd too and that has the same issue. The computer I'm using is an Acer 6920g. Any advice would be really appreciated, although I am new too all this so the the more simple the better.

---

### Post by pytheas22 on 2008-12-19
Please open a terminal (Applications>Accessories menu), run the following commands and post the output here:
```

lspci -nn
lshw -C Network
sudo iwlist scan
uname -m
```

This will help to pinpoint the problem.  Intel wireless should definitely work in Linux (in fact I'm quite surprised yours doesn't work out-of-the-box), so we can definitely fix this.

---

### Post by singlemanriot on 2008-12-20
thanks here is the output, it does work just not with my router, it finds every other one but mine its really weird. I've even tried changing the broadcast channel and that made no difference:confused:

---

### Post by pytheas22 on 2008-12-20
hmmm, yes, it does look like your wireless card is working normally; it can see other networks without a problem, as you note.

A couple possibilities:

1. are you in Europe or Asia?  If so, your card may not be able to see routers on channels 12 and up because the iwlagn driver operates in U.S. mode by default (but you can change this).  I know you said you tried changing the channel of your router; which ones did you try?  Did you try channel 1--because your card can definitely see that channel.

2. is your router in 11b or 11a mode?  If so, can you change it to 11g or 11n?

Also, what is the output of:
```

iwconfig wlan0
```

---

### Post by singlemanriot on 2008-12-20
I only tried cannel 6 ill get the results of that other test asap but I won't be home until sunday night uk time so ill be posting it then thanks for the help so far.  Its not a big deal but really annoying

---

### Post by singlemanriot on 2008-12-21
Thanks for all the help I changed the channel to channel 1 and its flying now. much appreciated.

---

