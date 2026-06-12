---
title: "Set wireless speed"
date: 2011-04-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by amiba on 2011-04-02
How do you set wireless speed in natty? I've tried 
```
sudo iwconfig wlan0 rate 54M
```
but nothing happens. 
I've tried this with wireless enabled and disabled (using network-manager), with and without the module loaded (ath9k) and using the solution provided in some forums (adding the command in /etc/rc.local and in a script in /etc/network/if-up.d) but to no avail... link speed always shows up as 65M.
Thanks 

Nelson

---

