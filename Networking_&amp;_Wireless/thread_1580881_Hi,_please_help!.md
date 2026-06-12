---
title: "Hi, please help!"
date: 2010-09-24
forum: Networking &amp; Wireless
---

### Post by hyn_shayan on 2010-09-24
Ok so I installed Ubuntu a week ago, and the Internet seems to be slow. I have an ALFA wireless detector. The one mentioned in the link :)

I found this link telling me how to fix it :
[http://mewcetti.com/2009/02/13/getting-the-alfa-awus036h-working-on-ubuntu/](http://mewcetti.com/2009/02/13/getting-the-alfa-awus036h-working-on-ubuntu/)


But the codes don't seem to work in Ubuntu. Can someone tell me how to work this code in Ubuntu as it's not doing anything in Terminal :

[I]sudo modprobe rtl8187


It justs goes on to another line after I press enter. Also this :

[/I][I]sudo iwconfig wlan0 txpower 50mW


[/I]"Where wlan0 is the name of your dongle."

What is a dongle and how do I find it's name?

---

### Post by dineshs on 2010-09-24
Please post the results of
```
sudo lshw -C network
```and ```
iwconfig
```

---

