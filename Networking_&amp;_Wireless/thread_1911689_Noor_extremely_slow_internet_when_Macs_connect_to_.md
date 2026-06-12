---
title: "No/or extremely slow internet when Macs connect to the local network."
date: 2012-01-19
forum: Networking &amp; Wireless
---

### Post by nasos on 2012-01-19
Dear all,
For like a year now, we have been experiencing a very awkward problem with the internet connection on all our Ubuntu machines (varying hardware). 

Our local network is connected with a D-Link DSR-500 to our workplace WAN and our machines connect to the local network through Netgear GS108 gigabit switches (all wired). The Ubuntu releases our machines run on range from 10.04 to 12.04(dev). 

A few minutes after we hook MacBook Pros on the network ALL the Ubuntu machines, although they can access the local network (through samba and ssh), they cannot access the internet (or they are EXTREMELY slow - like 3 minutes to load a page). This problem does not appear on Windows or Mac machines (although Macs are a bit laggish). 

We tried (maybe a few other things I don't remember atm):

1. Disabling ipv6 using a number of ways (firefox only, grub, ubuntu networking etc.)
2. Testing various MTU values
3. Changing the router, the switches and generally rearranged the network topology.
4. Hooking machines directly on the d-link router.
5. Lynx, and Chrome.
6. DNS work-arounds (at least as many we could find spending reasonable time searching the internet).

Notes and observations:

A. Although there seems to be some DNS issues, (traceroute is much faster without dns lookup), we could not pinpoint or resolve the issue as such. Additionally directly browsing with IP addressing on Firefox does not really make things better.

B. Pinging [www.google.com](www.google.com) can return up to 60% packet loss. (Non deterministic behavior)

C. 0% loss on local network pings

D. Some websites behave better than others.

F. The problem may start appearing very soon after a mac is connected to the network, or it may take sometime.

There seems to be only one solution: disconnect all the Mac machines from the network.

Does anybody else experience such a problem? 
Does anybody have a hint from where to start?

Thanks!
Nasos

---

### Post by jsra on 2012-01-19
Hello,
try to use wireshark for network diagnostics. Does this problem occurs when you connect the very same Macs clients in other network?

---

### Post by nasos on 2012-01-19
> **jsra said:**
> Hello,
try to use wireshark for network diagnostics. Does this problem occurs when you connect the very same Macs clients in other network?

The Macs seem to behave in other networks. Ubuntu laptops behave on other networks as well...

I will check wireshark and see if I can figure out anything.

---

### Post by nasos on 2012-02-02
> **nasos said:**
> The Macs seem to behave in other networks. Ubuntu laptops behave on other networks as well...

I will check wireshark and see if I can figure out anything.

Unfortunatelly wireshark doesn't show any suspicious activity from the Macs, just some name queries and MDNS broadcasts. I disabled Bonjour on the Macs to prevent MDNS but it didn't fix the problem :(.

---

### Post by squenson on 2012-02-02
This reminds me a similar problem when I tried to connect a desktop by ethernet and a laptop by wi-fi at home: somehow, the two machines acquired the same IP address and this made the surfing on Internet extremely slow.

Therefore, I suggest that you check the IP on all the machines and see whether there is a conflict somewhere.

---

### Post by nasos on 2012-02-07
> **squenson said:**
> This reminds me a similar problem when I tried to connect a desktop by ethernet and a laptop by wi-fi at home: somehow, the two machines acquired the same IP address and this made the surfing on Internet extremely slow.

Therefore, I suggest that you check the IP on all the machines and see whether there is a conflict somewhere.

All machine IPs are distinct, so this doesn't seem to be a problem.

---

### Post by nasos on 2012-02-09
I also noticed that Internet is working fine in a Windows guest through Virtualbox with bridged networking. On the opposite with NAT networking the internet on the same Windows guest is not working (host is Ubuntu in both tests).

This problem is really frustrating.

---

