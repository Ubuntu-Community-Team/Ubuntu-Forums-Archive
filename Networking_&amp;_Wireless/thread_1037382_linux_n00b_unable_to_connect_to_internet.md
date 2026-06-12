---
title: "linux n00b unable to connect to internet"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by hoejira on 2009-01-11
Hello all,
i'm a complete linux n00b and just finished installing Ubuntu on a 2nd computer in the house in hopes to create a remote server.  Turns out this is alot more complicated than i thought... i've installed Ubuntu in a dedicated partition and everythings up and running... im having a problem however connecting to the internet through my router (dlink dgl-4300)... if i connect the computer right to the internet it works... does anyone have any ideas of what i can do

---

### Post by 2hot6ft2 on 2009-01-11
Have you logged on to your router to look at the settings and see if you can spot the problem?
Perhaps resetting your router to the default settings to get connected then setting it up one pc at a time the way you want it.

---

### Post by hoejira on 2009-01-11
yea i've already gone through that i actually have 2 of the same routers and have swapped them out and reset to defaults.. this computer as well as both my xbox 360's are able to connect through the routers.... for some reason i just cannot get ubuntu to work with the router....

---

### Post by 2hot6ft2 on 2009-01-11
You said it would connect when bypassing the router, right? Did you completely shut down and do a cold boot when changing it from connecting directly to the modem and changing it to connecting to the router?

Reason being that it would have to release the IP address assigned by the modem to be re-assigned by the router.

---

### Post by hoejira on 2009-01-11
just tried that again and still no luck... i can access my router and change settings on it but i cannot access the internet which really doesnt make sense, is there any settings or anything that im missing

---

### Post by 2hot6ft2 on 2009-01-11
> **hoejira said:**
> just tried that again and still no luck... i can access my router and change settings on it but i cannot access the internet which really doesnt make sense, is there any settings or anything that im missing
What do you get if you run
```
ifconfig
```
in a terminal?
Applications>Accessories>Terminal

---

### Post by 2hot6ft2 on 2009-01-11
Wired thru ethernet try
```
sudo ifconfig eth0 release
```
followed by
```
sudo ifconfig eth0 renew
```
where eth0 is your ethernet connection which you would find using
```
ifconfig
```
if yours is something different then change the command accordingly

---

### Post by albinootje on 2009-01-11
> **hoejira said:**
> just tried that again and still no luck... i can access my router and change settings on it but i cannot access the internet which really doesnt make sense, is there any settings or anything that im missing

Is that machine 100 % Linux now, or a dual boot Linux/Windows ?

Did you restrict on MAC-addresses in the configuration of the router ?

Can you post the following from a terminal :
```

sudo dhclient
ifconfig -a

```
Please post the whole output. Thanks.

---

