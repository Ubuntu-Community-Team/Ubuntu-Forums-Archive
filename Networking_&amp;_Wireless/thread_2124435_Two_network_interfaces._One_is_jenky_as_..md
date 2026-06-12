---
title: "Two network interfaces. One is jenky as ****."
date: 2013-03-11
forum: Networking &amp; Wireless
---

### Post by jkurtisr32 on 2013-03-11
Got two network interfaces, eth0 and vboxnet0 on a machine that hosts virtualbox machines. Default interface is eth0.

I am able to access virtual machines through vboxnet0, but only when I access them by IP address:
```
ssh 10.10.1.103
```
When I try to access virtual machines through vboxnet0 by hostname, the connection times out.

Would also like to force internet connections through vboxnet0 (I have a virtual router running that provides connections for machines in virtual environment). I have been playing around with routing options, but no luck yet.

Any help with this would be greatly appreciated.

Thanks,
Kurtis

---

### Post by trh51 on 2013-03-11
> [COLOR=#000000]Would also like to force internet connections through vboxnet0 (I have a virtual router running that provides connections for machines in virtual environment). I have been playing around with routing options, but no luck yet.[/COLOR]
I believe this has something to do with the physical mac address of your internet card.

---

### Post by jkurtisr32 on 2013-03-11
> **trh51 said:**
> I believe this has something to do with the physical mac address of your internet card.

Yeah, I just figured I'd ask here, because it's possible that Ubuntu can't utilize the vboxnet0 card the same way as a physical card. Was thinking someone here might have experience.

Will probably try to fix this while treating the vboxnet0 interface the same as any physical interface. Holla back if you got knowledge on this shiiiit.

-K

---

### Post by jkurtisr32 on 2013-03-11
I was able to get the internet connection to go through vboxnet0 using the following set of commands:
```
sudo route delete default eth0
sudo route add default gw 10.10.1.1
```
Cool. I will add this motherfukerr to my rc.local

Still trying to figure out how to get the hostnames to resolve properly. If you know the answer, don't hold out on me, bro.

-Kurtis

---

### Post by jkurtisr32 on 2013-03-11
What the fuckk do all these thinggys mean in the route table??
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0           10.10.1.1     0.0.0.0         UG    0      0        0 vboxnet0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
10.10.1.0       0.0.0.0         255.255.255.0   U     0      0        0 vboxnet0
```
metric = 1? What the shiit is this? Going to hit the Googler for a little bitttttt.

-K

---

### Post by jkurtisr32 on 2013-03-11
Took the bitchh route for the hostname resolving issue. Assigned static IPs to the VMs that I need to access from the host.

Also note:
The commands mentioned above did not work in rc.local. The final solution was to use network manager to edit the routes for eth0, checking the box that says "only use this motherfuck for network resources", or some shitt like that. Then you can add the one line:
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo route add default gw 10.10.1.1[/FONT][/COLOR]
```
to your rc.local

---

