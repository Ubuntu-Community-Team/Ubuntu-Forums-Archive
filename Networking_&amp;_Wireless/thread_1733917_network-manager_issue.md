---
title: "network-manager issue"
date: 2011-04-19
forum: Networking &amp; Wireless
---

### Post by tanyeun on 2011-04-19
hi forks :D ,

recently, I got kick off by my own wireless router constantly
(I use nm-applet and network-manager for wireless)
I checked my phone and it was still connected
so the wifi should be working correctly

At the moment,
I have to restart the network-manager to make it work again
```

$ sudo service network-manager stop
$ sudo service network-manager start

```
this is really inconvenient

any ideas what's going on?

thx

---

### Post by uncaspi on 2011-04-19
What signal strength do you have? sudo iwlist scan

---

### Post by tanyeun on 2011-04-20
it's acting normal again
I have no idea

the iwlist scan result about signal stregth is as follows:
> 
Frequency:2.437 GHz (Channel 6)
Quality=66/70  Signal level=-44 dBm 


---

