---
title: "One network cable, two computers. Is it possible?"
date: 2009-03-29
forum: Networking &amp; Wireless
---

### Post by El Potro on 2009-03-29
Hello everyone,

In my home we use a wired network, and there are four computers already connected to one eight ports hub (also the router is connected). 

I'm about to add a computer to my current home network, but the problem is that for setting it up, I need a very long cable in order to connect it directly to the hub.

I already have one computer just next to the one that I want to add to the network, (so there is one cable that reaches there already).

I hope I made myself clear so far,

My question is: Can I somehow split the cable that is already there, so that I will be able to use THE SAME NETWORK CABLE CONNECTED TO ONE PORT OF THE HUB in two computers at the same time?

Is it physically possible?

Thank you a lot!

Mauricio

---

### Post by sinclair86 on 2009-03-29
[http://www.amazon.com/NETWORK-PAIR-SPLITTER-10BASE-T-CAT5/dp/B001H9AK1M/ref=sr_1_1?ie=UTF8&s=electronics&qid=1238311693&sr=1-1 ]("http://www.amazon.com/NETWORK-PAIR-SPLITTER-10BASE-T-CAT5/dp/B001H9AK1M/ref=sr_1_1?ie=UTF8&s=electronics&qid=1238311693&sr=1-1")
Like that?


if one has 2 NIC cards you could nat them as well....

---

### Post by El Potro on 2009-03-29
I meant exactly that!

I'm sorry, but I don't know too much about networks.  (I don't understand what is TO NAT something and a NIC card.

The computers have regular 10/100 mbps network cards.

Thank you very much for helping!

---

### Post by manpaz on 2009-03-29
In a standard home network I think you may have a class C network with

```
Network 192.168.1.0 
Netmask 255.255.255.0
```

That means, you must be able to have up to 253 hosts, what you are doing is broadcasting internet over the cable, so I think what you mean is if you are able to split the internet signal instead the cable, the answer is yes, just add all the hubs you need in order to accomplish your needs, even to enhance the signal in the middle of the large cables.

---

### Post by tuskenraider on 2009-03-29
buy a switch....  30 bucks... and you can have up to 5 computers in that room.

thats what i did... heck with allthat crazy multiple network cards or special splitters...  


tusken

---

### Post by Iowan on 2009-03-29
Unless the (nearby) computer already has two NIC's, you're gonna be buying hardware - it would seem more practical to invest in a switch than another NIC.  There is a limit to how many switches can be daisy-chained... but it's more than two.

---

### Post by SoftwareExplorer on 2009-03-29
Ok, I think I know what you are asking. Let me get this straight: you have an extra port on you switch. You have one cable and you don't want to have to run another right next to it. If that's the case, you can do it, I've done that to set up a network at school. See, there are 8 wires in a network cable. Only four are used for the network. There are four left over for when we decide that 1000 Gb/s isn't fast enough or something. Well, with a little work those extra four can be used as another cable!

---

### Post by BkkBonanza on 2009-03-30
People got it right here. Just buy a cheap switch and plug the two computers into it oalong with the end of the long run. No messy nat or special routes etc. Switches run for < $10 on ebay.

---

### Post by Bradh616 on 2009-03-30
> **BkkBonaza said:**
> People got it right here. Just buy a cheap switch and plug the two computers into it oalong with the end of the long run. No messy nat or special routes etc. Switches run for < $10 on ebay.

A good crimping tool and the new cat 5 cable ends will cost as much as a cheap hub or switch. Buy a switch is the best advice you could get.

---

### Post by El Potro on 2009-04-04
I guess I'll end up buying a switch.

Thank you all very much.

---

