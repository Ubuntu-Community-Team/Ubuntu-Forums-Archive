---
title: "Problem with Lubuntu 10.10 (Wireless)"
date: 2010-11-10
forum: Networking &amp; Wireless
---

### Post by Roush 427r on 2010-11-10
Files are uploaded, this is a pretty lame problem. Thanks!
 
[RIGHT]~Derek[/RIGHT]

---

### Post by uncaspi on 2010-11-10
Please post /etc/network/interfaces

Do you see the cards in network-manager upper panel?

---

### Post by Roush 427r on 2010-11-15
> **uncaspi said:**
> Please post /etc/network/interfaces
 
Do you see the cards in network-manager upper panel?
 
 
Can't find 'network-manger', but this is what I saw in /etc/network/interfaces:

---

### Post by Roush 427r on 2010-11-15
Also, it now cannot find the network, even though it is easily within range. I doubt it's the card because it worked, and lspci lists it.

---

### Post by docfred on 2010-11-15
Hi

Thanx in advance
I have installed ubuntu 10.10 on my acer aspire 1683 laptop.In network manager it says wireless is disabled.I tried some of the commands n other threads but hasnt worked out.Please help me set it up as i am completely new to this.Much appreciated.

---

### Post by Roush 427r on 2010-11-16
> **docfred said:**
> Hi
 
Thanx in advance
I have installed ubuntu 10.10 on my acer aspire 1683 laptop.In network manager it says wireless is disabled.I tried some of the commands n other threads but hasnt worked out.Please help me set it up as i am completely new to this.Much appreciated.
 
 
Please don't hijack my thread, start your own, thanks!

---

### Post by SteveDee on 2010-11-17
> **Roush 427r said:**
> Files are uploaded, this is a pretty lame problem. Thanks!
 
[RIGHT]~Derek[/RIGHT]

Here are a few comments/questions;

In your "description" pdf you indicate (I think) that the wireless access point is not yours, but is located in a nearby "shop". How do you know that the access point is running and within range?

Your output from iwlist is "No scan results" which normally indicates that the wireless interface is not receiving a useful (radio frequency) signal.

If you are living in a built up area, iwlist would normally show several access points, as long as the buildings, walls & appliances are not attenuating the signal too much.

As I sit here with my laptop, I can see 6 access points with signal levels from 16 - 79%. But if I walk the short distant into my garage, I get "No scan results" from iwlist, because the local wifi signals are serverly attenuated.

---

### Post by Roush 427r on 2010-11-21
> **SteveDee said:**
> Here are a few comments/questions;
 
In your "description" pdf you indicate (I think) that the wireless access point is not yours, but is located in a nearby "shop". How do you know that the access point is running and within range?
 
Your output from iwlist is "No scan results" which normally indicates that the wireless interface is not receiving a useful (radio frequency) signal.
 
If you are living in a built up area, iwlist would normally show several access points, as long as the buildings, walls & appliances are not attenuating the signal too much.
 
As I sit here with my laptop, I can see 6 access points with signal levels from 16 - 79%. But if I walk the short distant into my garage, I get "No scan results" from iwlist, because the local wifi signals are serverly attenuated.
 
Access point- Because I am on it currently with my stepdad's laptop, my mom is using it on my sisters laptop, I was on the network with that PCi and USB card before at the same location.
 
No scan results- I am aware of this, I have disconnected the antennae because I think the problem is that the cable was somehow interuppted. I think I answered my question, to which why it stopped connecting to the internet anyway. Thanks!

---

