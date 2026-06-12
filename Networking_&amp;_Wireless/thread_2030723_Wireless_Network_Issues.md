---
title: "Wireless Network Issues"
date: 2012-07-21
forum: Networking &amp; Wireless
---

### Post by Dalek Draco ON LINUX on 2012-07-21
So recently my ssd...crapped itself...I got a new hdd, downloaded a new copy of 10.04 and installed. 

Now I'm having issues with my wireless, previously it connected fine, but now whenever the network drops out or if I restart the router, I am forced to restart my computer for to "find" my wireless network again. 

If I turn wireless off and then put it back on, my network will not show up until I restart the computer. Logging out and logging back in, it will try to connect again but will just keep trying (and failing). 

Any hints/suggestions/anything would be appreciated.

---

### Post by NikTh on 2012-07-21
Hi , 
sorry that i have not any helpful suggestion about your problem. 

I have only a possible workaround with the problem of 

> **Dalek Draco ON LINUX said:**
> I am forced to restart my computer for to "find" my wireless network again.

If problem appears again , then do not restart your pc , open a terminal and 
```
sudo /etc/init.d/networking restart && sudo service network-manager restart
```Regards

---

### Post by Dalek Draco ON LINUX on 2012-07-22
Thanks for your reply, unfortunately it doesn't seem to fix the issue, I still need to restart the computer to get the wireless connected again :(

---

### Post by Dalek Draco ON LINUX on 2012-07-24
Bump   Any suggestions?

---

