---
title: "DHCP assigning correct static internal IP but it's not correct on my machine"
date: 2012-07-14
forum: Networking &amp; Wireless
---

### Post by tarahmarie on 2012-07-14
So I have the DHCP server on my router set to assign 192.168.1.XX4 on my Kubuntu 12.04 box. A couple of weeks ago, my machine stopped correctly registering that as the internal ip address, and started believing it was living at .XX1. Here's ifconfig:

```

/ Greetings, Madam. $ifconfig
eth0      Link encap:Ethernet  HWaddr XXXXXXXXXXXXX  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f7400000-f7420000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:228 errors:0 dropped:0 overruns:0 frame:0
          TX packets:228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23947 (23.9 KB)  TX bytes:23947 (23.9 KB)

wlan0     Link encap:Ethernet  HWaddr XXXXXXXXXXXXXXXX 
          inet addr:192.168.1.XX1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2002:47e7:b470:1234:6948:f341:3b10:39a0/64 Scope:Global
          inet6 addr: 2002:47e7:b470:1234:218:e7ff:fee0:2729/64 Scope:Global
          inet6 addr: fe80::218:e7ff:fee0:2729/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1207 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1618 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:566912 (566.9 KB)  TX bytes:216367 (216.3 KB)


```

Yes, the MAC addresses are set properly in the router's DHCP server. Under wlan0, you can see that the IP address isn't routing properly to .XX4. This behavior persists across router reboots and machine reboots. 

This may have to do with me installing vsFTP a week ago and then killing it. Yes, I've tried disabling UFW; that's not the problem, as another machine with the exact same rules (except a different port) and which is assigned its static internal ip the same way by the same router is working perfectly when I ssh into it. Unsurprisingly, the error I get when attempting to ssh into this box is "No route to host". 

I think that what may be wrong is that somehow the static ip route has been overwritten or rendered inoperative, but all the guides assume deep knowledge of internal routing. Can I get a recommendation on an easier tutorial to start with? Or a suggestion on how to use iptables to find the issue?

---

### Post by Cheesehead on 2012-07-14
DHCP usually isn't hard to troubleshoot.

It's either your local machine's MAC address has changed (new hardware, failing hardware, deliberate spoofing for another purpose, changed to static IP).

Or it's another machine on the network (accidental or deliberate MAC spoofing) occupying the address.

Or the router's MAC list for IP assignments has changed (typo or erroneously turned off).

It's usually nothing "deep." Log into your router and see how many of those possibilities you can rule out. Every time it's happened on my networks has been a typo on the router's MAC list.

---

### Post by tarahmarie on 2012-07-14
> **Cheesehead said:**
> DHCP usually isn't hard to troubleshoot.

It's either your local machine's MAC address has changed (new hardware, failing hardware, deliberate spoofing for another purpose, changed to static IP).

Or it's another machine on the network (accidental or deliberate MAC spoofing) occupying the address.

Or the router's MAC list for IP assignments has changed (typo or erroneously turned off).

It's usually nothing "deep." Log into your router and see how many of those possibilities you can rule out. Every time it's happened on my networks has been a typo on the router's MAC list.

I already checked to make sure the MAC address was correct; I wanted to make sure that it wasn't something that simple before I posted here, which is why I noted it in my original post.

---

### Post by Cheesehead on 2012-07-14
You certainly did. What else on that list have you been able to rule out?

---

### Post by papibe on 2012-07-14
Hi tarahmarie.

Just to make sure: remember that both cards, ethernet and wireless, have different MACs. So if you set and static IP address for your ethernet, it won't be valid if you connect wireless.

Just a thought.
Regards.

---

### Post by tarahmarie on 2012-07-17
> **papibe said:**
> Hi tarahmarie.

Just to make sure: remember that both cards, ethernet and wireless, have different MACs. So if you set and static IP address for your ethernet, it won't be valid if you connect wireless.

Just a thought.
Regards.

Well, it was the thought that counted ;-) I was indeed using the eth0 MAC instead of wlan0 MAC. The DHCP server had always randomly assigned me the correct internal IP address--this was the first time that it hadn't, and now I know why. Thanks!

---

