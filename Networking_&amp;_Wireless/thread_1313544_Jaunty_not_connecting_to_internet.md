---
title: "Jaunty not connecting to internet??"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by Goveynetcom on 2009-11-03
(Had to post from my Windows Machine), Suddenly my Linux machine will not connect to the internet. My linux machine is plugged in through a router,via ethernet, and then the router is plugged into a box that is hooked through a cable to a small receiver on my roof which gets internet via satellite. About 2 days ago I couldn't get my Linux to display any internet pages. Then today I checked and it establishes with the router but doesn't recieve **any** incoming data. My Windows is hooked wirelessly through a small USB Adapter, and that is working fine, so what is going on? I have checked and rechecked my router settings and nothing... I need to fix this ASAP!!!

---

### Post by Goveynetcom on 2009-11-04
Does any one have any info to contribute to my predicament?

---

### Post by werecatomega on 2009-11-04
hmm. this is odd. can you connect to the internet using a live cd?

---

### Post by Iowan on 2009-11-04
**route** shows proper gateway?
Can you access router setup page?

---

### Post by Goveynetcom on 2009-11-04
i can access the router page from my Windows Computer. I did not check the ***route*** in terminal because I didn't know that command. I will start to take a further look and post my type of router if I can't get this fixed.

---

### Post by Goveynetcom on 2009-11-05
Tell me if this helps:

I found some info through the route command and I think it is not routing correctly

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
XXX.XXX.X.X  *                    XXX.XXX.XXX.X     U          1       0        0 eth0
link-local        *                    XXX.XXX.X.X         U       1000     0        0 eth0
default           XXX.XXX.X.X   0.0.0.0                  UG        0       0        0 eth0
```The first destination is somewhat a local IP address and it seems to be one I have never seen. That and link-local have the basic Subnet Mask for GenMask. default is the one I believe that is my internet connection. The gateway seems to be correct I think (the address was that of my router and I think it should be that). Although the Gen Mask is set to 0.0.0.0 and that seems wrong, I'm assuming that the Gen Mask is similair to the Subnet Mask but I have absoultely no idea. This command leads me to believe something is setup incorrect and I have tried again and again to fix this but no luck. If someone knows what is wrong please tell me, and explain my results. 

I think I am safe blocking the information (although they were all local IP's not Internet IP's). 

HELP IS NEEDED DESPERATELY!!!

Thank you for your time...

---

### Post by Goveynetcom on 2009-11-05
I need to know what that info means. Please Help!

---

### Post by Iowan on 2009-11-05
> **Goveynetcom said:**
> i can access the router page from my Windows Computer. If you can't connect **to** the router (from Ubuntu box), you probably can't connect **through** it (although several possible exceptions come to mind.)
The last line of the **route** command shows the default gateway. It *should* point to your router. **ifconfig -a** should show an IP address similar to the router's address (not 169.254.X.X). With a valid address, you *should* be able to **ping** the router (and probably the Windows box, too).

---

