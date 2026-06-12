---
title: "bypassing the local host for testing purposes"
date: 2010-01-18
forum: Networking &amp; Wireless
---

### Post by EricPope on 2010-01-18
I have a computer with multiple Ethernet interfaces that I want to use for testing network devices. I ran into a snag that I hope you can help me with. When I try to send network traffic through the unit under test to another interface on my PC the traffic goes through the local host interface instead. 

For example I want to send a ping from eth0 through the UUT to eth1 but in Wireshark I can see the ping packets being sent and received on the 'lo' interface. 

I am being outsmarted by my PC's routing function! How do I get these packets to go the 'long way' through my test network?

Thanks, 
Eric

---

### Post by bab1 on 2010-01-18
> **EricPope said:**
> I have a computer with multiple Ethernet interfaces that I want to use for testing network devices. I ran into a snag that I hope you can help me with. When I try to send network traffic through the unit under test to another interface on my PC the traffic goes through the local host interface instead. 

For example I want to send a ping from eth0 through the UUT to eth1 but in Wireshark I can see the ping packets being sent and received on the 'lo' interface. 
How is Wireshark setup?  

See Wireshark's take on loopback interfaces [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://wiki.wireshark.org/CaptureSetup/Loopback"). > 
I am being outsmarted by my PC's routing function! How do I get these packets to go the 'long way' through my test network?

Thanks, 
Eric
Can you show us the Wireshark display?

Edit: If you are monitoring any physical NIC (interface) you should not see any lo packets.

---

