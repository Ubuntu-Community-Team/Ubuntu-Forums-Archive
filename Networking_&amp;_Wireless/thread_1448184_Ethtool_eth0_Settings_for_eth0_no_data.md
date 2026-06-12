---
title: "Ethtool eth0: Settings for eth0 no data ??"
date: 2010-04-06
forum: Networking &amp; Wireless
---

### Post by wilvin on 2010-04-06
hi everybody,

i am new to ubuntu and i wanted t make a little 
web server 
as i was setting up some things i wanted to change some option in my internet interface:
eth0 

but when i use:
```
sudo ethtool eth0
```it returns:
```
Settings for eth0: 
No data available

```i find this verry strange cause i can go on internet so the interface is working 
and my ifconfig also returns that it is working good .. except for a few errors 

please can somebody help me ?

---

### Post by Iowan on 2010-04-06
Curious... It works on this Hardy box, but **ethtool** doesn't exist on my Lucid box. Is the option you want to change available via **ifconfig**?

---

