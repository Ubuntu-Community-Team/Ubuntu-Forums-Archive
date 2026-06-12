---
title: "How to route between interfaces without masquerading"
date: 2012-01-05
forum: Networking &amp; Wireless
---

### Post by MidnightJava on 2012-01-05
I need to make my Ubuntu system act as a router between the subnets on each of its ethernet interfaces. All the examples I find on-line do this with IP Masquerading/NAT, which is not what I want to do. I need the address on each interface to be routable to/from the other interface, with no address translation.

To explain further: The external interface of the Ubuntu system is a wireless interface to a NAT'd router. So the address of that interface is an internal address, that is being translated by the wireless router to my external Internet address, and of course is visible to other systems on my local LAN.

There is also a wired interface on the Ubuntu system, (on a separate subnet) connected to a device that runs Ethernet protocol from an embedded processor (it's an amateur software defined radio). I need the radio to be accessible from other systems on my local LAN. So I'd like to make Ubuntu route packets between the two interface cards in both directions, without any address translation, filtering, etc.

Is that possible?

---

### Post by Charlietje on 2012-01-06
What you need to do is run this command in terminal

```
echo 1 > /proc/sys/net/ipv4/ip_forward 
```


It will enable forwarding in the kernel.
Next you need to do is adjust your routing table, your pc will not know what to do with the packets

---

### Post by MidnightJava on 2012-01-06
Thanks for that. It worked nicely. I entered the following on the Ubuntu system

```
echo 1 > /proc/sys/net/ipv4/ip_forward
route add -net 192.168.2.0 netmask 255.255.255.0 dev eth0
route add -net 192.168.1.0 netmask 255.255.255.0 dev ra0
```Interface eth0 is the "internal" interface, on subnet 192.168.2.0, with address 192.168.2.1, and the radio controller at the other end of the cable is 192.168.2.2. Interface ra0 is my "external" interface, connecting to the NAT router and other devices on the local LAN.

On the other computer that I wanted to have access to the radio controller, I entered 

```
route add -net 192.168.2.0 192.168.1.224 255.255.255.0
``` (different format because it's a Mac), and I can now ping from the Mac to the radio controller.

Thanks again.

---

