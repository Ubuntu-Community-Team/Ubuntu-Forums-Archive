---
title: "Help with Shorewall traffic shaping"
date: 2006-04-27
forum: Networking &amp; Wireless
---

### Post by virx on 2006-04-27
Hi

Can somebody help me to get shorewall traffic shaping working. I have cable connection with upstram 256 kbit/s and downstream 1 mbit/s

No matter what i do, shorewall tc won't shape. I have dapper drake with kernel 2.6.15-20-386, which should have qos support.

I have set
TC_ENABLED=Internal
CLEAR_TC=Yes
from shorewall.conf file

My 
tcdevices
```

#INTERFACE      IN-BANDWITH     OUT-BANDWIDTH
eth0            800kbit         100kbit

```

My
tcclasses
```

#INTERFACE      MARK    RATE    CEIL    PRIORITY        OPTIONS
eth0            1       full/2  full    0               tcp-ack,tos-minimize-delay
eth0            2       full/3  full/2  1               default

```

My
tcrules
```

#MARK   SOURCE          DEST            PROTO   PORT(S) CLIENT  USER    TEST
#                                                       PORT(S)
1       $FW             0.0.0.0/0       icmp    8
1       $FW             0.0.0.0/0       tcp     80
1       $FW             0.0.0.0/0       tcp     -       80
2       $FW             0.0.0.0/0       tcp     4662
2       $FW             0.0.0.0/0       tcp     -       4662

```

---

### Post by virx on 2006-04-28
Edit to new topic.

---

### Post by virx on 2006-05-22
Still in trouble.

---

