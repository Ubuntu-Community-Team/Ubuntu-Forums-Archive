---
title: "ARP Cache"
date: 2010-04-07
forum: Networking &amp; Wireless
---

### Post by joelgsf on 2010-04-07
If someone has an answer, I would appreciate knowing who sets the timing for a dynamic information put into the ARP cache. Can we control this timing? How can we clear the ARP cache?
Everywhere where I looked for this information I could only have the general answer that the dynamic information collected by the ARP protocol is ephemeral. But how much time does that mean? Who controls it? I know that I can delete or set entries on a "by host" (IP) basis, using 'arp' tool. Can we delete the hole cache with a single command or action? Can I setup the "time to live" for the cached information?
Thanks for any hints.

Joel Guilherme

---

### Post by capscrew on 2010-04-07
> **joelgsf said:**
> If someone has an answer, I would appreciate knowing who sets the timing for a dynamic information put into the ARP cache. 

ARP is a protocol in the TCP/IP stack. The short answer is: It is a part of kernel.  But really the ARP cache is filled whenever a packet is sent to another host.  If the MAC address is local that MAC address is added to the ARP cache.  If the destination is not in the LAN then the defaut GW  is where the packet is sent.  The default GW's MAC should be already in the cache from bootup. 
> 
Can we control this timing?
No, and there is not reason to control it.  It is part of the glue that connects IP to Ethernet.> 
How can we clear the ARP cache?
With Linux you can use either the tool [FONT="Courier New"][COLOR="Green"]arp[/COLOR][/FONT] see ```
man arp
```

or you can use the tools in iproute2.  See [**_here _**]("http://linux-ip.net/html/tools-ip-neighbor.html").
> 
Everywhere where I looked for this information I could only have the general answer that the dynamic information collected by the ARP protocol is ephemeral. But how much time does that mean? Who controls it? 
As I said this is part of the TCP/IP stack and it is part of the OS kernel.  The actual spec's are different in the different OS kernels.  MS has their interpretation as does Linux, Sun, the BSD's, cisco IOS, etc. > 
I know that I can delete or set entries on a "by host" (IP) basis, using 'arp' tool. Can we delete the hole cache with a single command or action? 
It's really dependent on the capabilities and tools of the OS.  For instance cisco IOS ARP cache is configurable.  See [here]("http://www.ciscoarticles.com/Cisco-IOS/925.html").  But then, the OS is for a router and it can have thousands of neighbors.> 
Can I setup the "time to live" for the cached information?

Off the top of my head I would say no you can't configure the TTL other than *static or dynamic*.  In other words:  *always in the cache* (static) or determined by the TCP/IP suite.  I'll hazard  guess and say that the dynamic TTL is also variable under load.  It's that way in Windows.  See [**_here_**]("http://neworder.box.sk/newsread.php?newsid=5666").

---

### Post by joelgsf on 2010-04-10
> **capscrew said:**
> ARP is a protocol in the TCP/IP stack.
 ...

Many thanks, capscrew. You did supplied me with the information I was looking for.
I only disagree with you when you say that there is no point in setting up a different value for the ARP TTL. Depending on the number of hosts that you have in your LAN and the frequency that your host exchange messages with the others this may affect significantly the eficiency of the cache. If you have a too small timeout you will be flooding the network with ARP packages. On the other side, you will get an inflated cache. That is exactly what I was thinking of testing. But it seems it will be a little complex to be tapping into the Kernell for doing this job. I believe that someone has done this, to setup whatever value it is set today, isn't it?
Cheers,

   Joel Guilherme

---

### Post by capscrew on 2010-04-11
> **joelgsf said:**
> Many thanks, capscrew. You did supplied me with the information I was looking for.
I only disagree with you when you say that there is no point in setting up a different value for the ARP TTL. Depending on the number of hosts that you have in your LAN and the frequency that your host exchange messages with the others this may affect significantly the eficiency of the cache. 
If you have a too small timeout you will be flooding the network with ARP packages. On the other side, you will get an inflated cache. 

One slight error in perception.  The TTL has nothing to do with gathering MAC addresses in cache.  The cache is created on demand (e.g when data is transmitted).  The only need to drop entries from cache is the limitations of cache size.
> 
That is exactly what I was thinking of testing. But it seems it will be a little complex to be tapping into the Kernell for doing this job. I believe that someone has done this, to setup whatever value it is set today, isn't it?
Cheers,

   Joel Guilherme

These kernel parameters are very stable at this point.

If you want to see ARP working, install Wireshark and limit (filter) the packet capture to ARP.  As I am writing this I have Wireshark open and I am streaming a show from Hawaii.  I have less than 20 ARP requests per 10 minutes.

---

