---
title: "wlan0 Problem"
date: 2011-06-08
forum: Networking &amp; Wireless
---

### Post by Liova99 on 2011-06-08
i know tha this question asked 100 times before me, but i don't find a solution. i whant to change the wlan0 channel. now is 12 and i want to make it 1

P.S. Sorry for my englesh :)

---

### Post by fractalman on 2011-06-08
open a terminal and type the folllowing codes

```
sudo ifconfig $IFACE down
sudo iwconfig $IFACE mode managed
sudo ifconfig $IFACE up
sudo iwconfig $IFACE channel x
sudo ifconfig $IFACE down
sudo iwconfig $IFACE mode monitor
sudo ifconfig $IFACE up
```

$IFACE = your interface, replace with 'wlan0'

x = new channel number, so for yourself just add '1'

---

### Post by Liova99 on 2011-06-08
thanks for reply i will try this!:-k

---

