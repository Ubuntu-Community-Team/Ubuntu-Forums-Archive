---
title: "bcm43xx - 54 mbps??"
date: 2006-07-02
forum: Networking &amp; Wireless
---

### Post by munsell on 2006-07-02
Hello,

I have the following broadcom card:
```

0000:01:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)
        Subsystem: Hewlett-Packard Company: Unknown device 1360
        Flags: bus master, fast devsel, latency 0, IRQ 233
        Memory at c3000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

```

I am using the new broadcom driver (kernel) but I cannot seem to get it to work at rate = 54M.  I have tried to specify this using iwconfig but it always defaults back to rate=11M.  It appears that it is only working for 802.11b and not 802.11g. 

Does the broadcom driver support 802.11g yet?  I have read numerous posts on the forum but I cannot determine whether or not this is the case.  If rate=54M is possible, can you please let me know how? :)  Thanks for any help in advance.

---

### Post by DarthMandeep on 2006-07-03
The guides I've seen for the bcm43xx driver say to use 11M for now. If you want a 54mbps connection, try ndiswrapper with the latest Windows drivers.

That's what I'm using, connected at 54 right now.

---

### Post by Rob_H on 2006-07-03
Is there any drawback to using NdisWrapper over the "native" driver? Since the latter is restricted to 11 Mbps, I don't understand why someone would choose it. Thanks.

---

### Post by munsell on 2006-07-03
[QUOTE=Rob_H]Is there any drawback to using NdisWrapper over the "native" driver? Since the latter is restricted to 11 Mbps, I don't understand why someone would choose it. Thanks.[/QUOTE]

I have tried using ndiswrapper (compiled from source and .deb packages) but it constantly drops connection (I have only had this problem using Dapper) :( If you can get ndiswrapper to work consistently I would pernsonally use it over the broadcom driver at this point in time.

---

### Post by ubunturules on 2006-07-04
Use Ndiswrapper because it can get 54 Mpbs and the firmwirecutter can only get 11 Mpbs which sucks and nobody wants.

---

### Post by Eversmann on 2006-07-05
I only use ndiswrapper with broadcom wifi cards. Native ones some some problems (but i'm sure in the future will be great).

Connection dropping can be something else, try with a different ap, open connection and things like that.

---

### Post by DarthMandeep on 2006-07-08
> **Rob_H said:**
> Is there any drawback to using NdisWrapper over the "native" driver? Since the latter is restricted to 11 Mbps, I don't understand why someone would choose it. Thanks.

The benefit of the bcm43xx driver is that it's truly free software. In addition, I believe you can use the kismet wireless scanner with it, something you can't do with ndiswrapper.

I just use an old 802.11B prism card for kismet and the Broadcom card with ndiswrapper for my actual connection.

---

### Post by Breathe on 2007-09-13
> **ubunturules said:**
> Use Ndiswrapper because it can get 54 Mpbs and the firmwirecutter can only get 11 Mpbs which sucks and nobody wants.

firmwirecutter... hahahaha... XD

---

