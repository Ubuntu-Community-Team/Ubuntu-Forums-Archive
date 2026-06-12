---
title: "Network Issues"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by sjefsape on 2009-03-09
Hi there..
I can`t get my computer to connect to the router.
I have Realtek RTL 8111b onboard pcie card.
Ubuntu 8.10
Anyone who can help?

---

### Post by jonobr on 2009-03-09
You need to supply more info,

Are you using DHCP or static IP addresses,
whats the result from 

```
ifconfig
```

Is the device being recognized by the machine?
I also believe the Realtek is a Gig ethernet card,
Im wondering if what your connecting to supports that...
Is the router your connecting 10/100 only and maybe the two wont talk to each other?

---

### Post by sjefsape on 2009-03-09
> **jonobr said:**
> You need to supply more info,

Are you using DHCP or static IP addresses,
whats the result from 

```
ifconfig
```

Is the device being recognized by the machine?
I also believe the Realtek is a Gig ethernet card,
Im wondering if what your connecting to supports that...
Is the router your connecting 10/100 only and maybe the two wont talk to each other?

I am using DHCP. I will get the result once I get home and try it. 
It is a gig ethernet card yes. My router is only 10/100.
Doesn`t it choose speed and duplex it self? Or do I have to set it to 100mbit?
If so, how do I do that?

---

### Post by jonobr on 2009-03-09
I had a look at the realtek site and it seems the device supports the 10/100 router you may have
This is from the realtek site

> The device supports the PCI Express 1.0a bus interface for host communications with power management and is compliant with the IEEE 802.3u specification for 10/100Mbps Ethernet and the IEEE 802.3ab specification for 1000Mbps Ethernet. It also supports an auxiliary power auto-detect function, and will auto-configure related bits of the PCI power management registers in PCI configuration space.

So, you should be good to go,
performing the  following commands will show what you have on there so far

```
ifconfig
```

and

> cat /etc/resolv.conf

and

```
ping 127.0.0.1
```

if you get a response to that,
then ping the ip address you are issues

> ping <ip address>

---

### Post by sjefsape on 2009-03-09
I forgot to say that I have windows XP on the same machine.
But on a different disk. Read somewhere that windows could deactivate my NIC when I shut it down. But I can`t seem to find a choise to turn on Wake On Lan in the advanced menu. 
I will try those commands and paste them here when I get home.

---

### Post by sjefsape on 2009-03-09
hmm.. Could it be the 64bit version that does it? 
Thinking of downloading 32bit version when I get home..

---

