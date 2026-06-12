---
title: "wireless network on kubuntu 9.10 problem"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by grimslider75 on 2009-11-26
i'm new to linux, and don't know anything much about commands so fixing a problem is something completely different for me. 

my wireless internet connection does say that it is connected and that it is active, but, when i open a program such as konqueror or firefox, the internet doesn't connect. specifically it says that it cannot connect to the server. im not sure whether or not this is a DNS problem or something else. please help.

NOTE: when i first installed Kubuntu, the internet worked fine in both connections and actual use.

---

### Post by solar george on 2009-11-26
could you open a terminal (konsole) and try the following.
```
nslookup google.com
ping -c 5 google.com
```
And post the results.

---

### Post by lisati on 2009-11-26
On the rare occasion that I've used my mobile to connect my laptop to the internet wirelessly, I've sometimes had a similar problem. It was usually fixed by disconnecting, turning my phone off and on again, and then reconnecting.

---

