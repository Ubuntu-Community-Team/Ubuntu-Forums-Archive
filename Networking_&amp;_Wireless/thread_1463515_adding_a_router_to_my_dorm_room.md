---
title: "adding a router to my dorm room"
date: 2010-04-27
forum: Networking &amp; Wireless
---

### Post by Tpolich on 2010-04-27
I am currently attending college and living in the dorms we have 3 either-net ports and 3 people in one room. So we bought a router so we could have more then three things plugged in. I figured out via wikis how to set it up to run as a switch but I would like to run it as my own subnet. 

I have search far and wide for a guide or explanation on how to do this but the only one that seemed to be what I wanted was a bit beyond me.
```
 Picture of how we get internet
      
      internet comes in through wall from schools router(s)

    |        ___
====|=======|___|==several pcs plugged into router
    |      
      Linksys router running dd-wrt    

 Connection-specific DNS Suffix  . : ******.edu
 Description . . . . . . . . . . . : NVIDIA nForce Networking Controller
 Physical Address. . . . . . . . . : 00-15-58-A4-B6-71
 Dhcp Enabled. . . . . . . . . . . : Yes
 Autoconfiguration Enabled . . . . : Yes
 IP Address. . . . . . . . . . . . : 75.102.203.100
 Subnet Mask . . . . . . . . . . . : 255.255.254.0
 IP Address. . . . . . . . . . . . : fe80::215:58ff:fea4:b671%7
 Default Gateway . . . . . . . . . : 75.102.202.1
 DHCP Server . . . . . . . . . . . : 140.192.141.242
 DNS Servers . . . . . . . . . . . : 140.192.0.2
                                     140.192.239.2

```

If anyone could help I would be really thankful.

---

### Post by P4man on 2010-04-27
ahm.. if you want to do subnetting, you should configure the router as.. router, and not as a switch?  Its should be as simple as plugging the router in and connecting your machines, since every router Im aware off will be configured to do NAT addressing and DHCP out of the box.

---

