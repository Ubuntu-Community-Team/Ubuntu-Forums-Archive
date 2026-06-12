---
title: "VirtualBox virtual network and static route issue"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by eric.des.courtis on 2009-08-31
[FONT=System]Hi,

I am trying to simulate a networked environment that looks like this with Virtual Box:

     Internet
          | (NAT)
          | eth3
|--------------------------------------------|
|                                            |  
|  [/FONT][FONT=System]Ubuntu Server 9.04 (Router)[/FONT][FONT=System]  |\
|                                            | \
|--------------------------------------------|  \
  | eth0 (.1)         | eth1  (.1)          \   eth2 (.1)
  |                      |                         \
10.253.0.0/24    [/FONT][FONT=System]10.253.1.0/24         [/FONT][FONT=System]10.253.1.0/24 [/FONT]
[FONT=System]  |                      |                           |
  |                      |                           |
---------------        --[/FONT][FONT=System]---------------[/FONT]          [FONT=System]--[/FONT][FONT=System]---------------[/FONT]
[FONT=System]|  PC[/FONT][FONT=System](.2)   [/FONT][FONT=System]|       |     PC[/FONT][FONT=System](.2)[/FONT][FONT=System]  |          [/FONT][FONT=System]|     PC(.2)   |
[/FONT][FONT=System]---------------        -----------------          [/FONT][FONT=System]-----------------

I enabled ip forwading. And NAT on eth3 all PC's can get to the internet. But they can't see each other???

[/FONT][FONT=System]Virtual box networking is working correctly each PC can ping all interfaces on the ubuntu server.

[/FONT][FONT=System]Any ideas?


Eric
[/FONT]

---

### Post by eric.des.courtis on 2009-08-31
```

     Internet
          | (NAT)
          | eth3
|--------------------------------------------|
|                                            | 
|  Ubuntu Server 9.04 (Router)  |\
|                                            | \
|--------------------------------------------|  \
  | eth0 (.1)         | eth1  (.1)          \   eth2 (.1)
  |                      |                         \
10.253.0.0/24    10.253.1.0/24         10.253.1.0/24
  |                      |                           |
  |                      |                           |
---------------        -----------------          -----------------
|  PC(.2)   |       |     PC(.2)  |          |     PC(.2)   |
---------------        -----------------          -----------------


```

---

