---
title: "Packet Forwarding and IP Changing"
date: 2009-03-14
forum: Networking &amp; Wireless
---

### Post by TrickerZ on 2009-03-14
I'm not sure if this can even be done without writing my own program, but I need packets taken in on one interface from a specific IP to be forwarded out a second interface with the source IP changed and vice versa.  Basically I need to get a computer to think it's talking to a different IP than it really is without changing the way the packets work at all.  The system uses CORBA, so NAT will not work and there is no way for me to change the IP at all.  The device also does not use a gateway.  I'm thinking certain firewall software may be able to accomplish what I'm looking for.  Any help or recommendations would be much appreciated.

---

### Post by Roofdaddy on 2009-03-14
> **TrickerZ said:**
>   Basically I need to get a computer to think it's talking to a different IP than it really is without changing the way the packets work at all.  The system uses CORBA, so NAT will not work and there is no way for me to change the IP at all.


I'll give you a link but .....what you do with it is up to you. 

[http://www.iss.net/security_center/advice/Underground/Hacking/Methods/Technical/Spoofing/default.htm](http://www.iss.net/security_center/advice/Underground/Hacking/Methods/Technical/Spoofing/default.htm)



[B][COLOR=Red]
[SIZE=4]FREE KEVIN[SIZE=2] ....

[COLOR=Black]W¤¤t...!!! 1 f¤®g¤t..........h3'$ @ll®3@Ð¥ f®33.#-o[/COLOR]



[/SIZE][/SIZE][/COLOR][/B]

---

### Post by fixitdude on 2009-03-14
You want to look up packet spoofing. Other keywords would be packet header rewrite.

---

### Post by buldozerceto on 2009-03-14
You can use iptables to do this:
try this:
iptables -t nat -i eth0 -o eth1 -j SNAT --to 10.4.4.2

---

### Post by TrickerZ on 2009-03-15
If it uses NAT, it will not work.  Just an FYI, what I'm doing is not illegal in any way.  We have a problem where we have multiple devices that all have the same IP addresses to control them (which we cannot change due to them being hard coded) which means we can only talk to one at a time.  I need to make the computer think that each device has a different IP without using NAT since NAT screws up the CORBA connections (CORBA listens on a port, then sends a port it would like to connect to and NAT will change the port making it useless).  Is that iptables command actually NAT, or will it only change the source IP?  

I will see what I can find on IP spoofing.  If I can do a man-in-the-middle and have it just change the source IP in both directions, that would be perfect.  Not having a gateway on the device is the biggest PITA.  Everything is done Layer 2, so it can only ARP for the router between the computer and device.

---

