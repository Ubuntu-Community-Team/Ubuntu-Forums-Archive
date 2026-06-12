---
title: "Linux switch?"
date: 2011-11-29
forum: Networking &amp; Wireless
---

### Post by Groggster on 2011-11-29
Hey guys! I was just wondering what exactly I need to do in order to get my Linux machine to switch packages based on their MAC-addresses, just like an ordinary switch? I have four network cards. Can it be done? Maybe i can get a hold on the software from one of those Linux based store switches?

Thanks in advance!

---

### Post by Groggster on 2011-11-30
Ubumpu.

---

### Post by haqking on 2011-11-30
> **Groggster said:**
> Hey guys! I was just wondering what exactly I need to do in order to get my Linux machine to switch packages based on their MAC-addresses, just like an ordinary switch? I have four network cards. Can it be done? Maybe i can get a hold on the software from one of those Linux based store switches?

Thanks in advance!

what ?

What do you mean by switch packages ?

---

### Post by Groggster on 2011-11-30
Well, to move packages through my network from it's source to it's destination based on MAC-addresses in a MAC-address table and or by a broadcast, given that the path is not known by the switch.

---

### Post by haqking on 2011-11-30
> **Groggster said:**
> Well, to move packages through my network from it's source to it's destination based on MAC-addresses in a MAC-address table and or by a broadcast, given that the path is not known by the switch.

you mean packets then not packages.

and packets are sent based on mac address using ARP and source/destination.

I dont understand what you mean.

---

### Post by Groggster on 2011-11-30
Well, do you know how a switch works to begin with?

---

### Post by SeijiSensei on 2011-11-30
Time for a brief review of the hoary [OSI model]("http://en.wikipedia.org/wiki/OSI_model") of networking and layers.

**Switches** work at Layer 2, the data link layer.  They include electronics that determines the destination device of the packet based on information available from Layer 1, the physical layer.

**Routers** operate at Layer 3, where packets are directed by software protocols like TCP/IP.  Routers are used to interconnect Layer-2 networks. A PC running Linux makes a fine router, but it doesn't have the specialized electronics of a Layer 2 switch.  

So what precisely is it that you're trying to accomplish?  If you just want to network a bunch of devices together, use a switch.  If you need to interconnect networks, use a router.

---

### Post by btindie on 2011-11-30
You may be able to do what you want by creating a software bridge between all the interfaces, though it'll be more like a Hub than a Switch. [https://help.ubuntu.com/community/NetworkConnectionBridge](https://help.ubuntu.com/community/NetworkConnectionBridge).

Have you tried google?? It turns this up [http://lisa.mindbit.ro/](http://lisa.mindbit.ro/), even if it is a little old.

Or you could splash out on an [Arista]("http://www.aristanetworks.com/") switch which runs Linux. If that's beyond your budget there are Linksys switches running Linux and various replacement distros so it may be worth looking at them. But switching is generally done in hardware for speed.

---

### Post by haqking on 2011-11-30
> **Groggster said:**
> Well, do you know how a switch works to begin with?

yes, is that what you want to know then ?

because before i type out what you can google for yourself it needs to be clearer what you want to do.

There are different types of switch, layer 2, layer 3 or multilayer

however there real sole purpose is to avoid collisions at the basic level

---

### Post by Groggster on 2011-11-30
I want my Linux machine equipped with four separated network cards to interconnect my LAN at layer 2. Meaning, I want it to act similarly to a common Netlink or Dlink switch. Can this be accomplished?

---

### Post by Groggster on 2011-12-01
> **btindie said:**
> You may be able to do what you want by creating a software bridge between all the interfaces, though it'll be more like a Hub than a Switch. [https://help.ubuntu.com/community/NetworkConnectionBridge](https://help.ubuntu.com/community/NetworkConnectionBridge).

Have you tried google?? It turns this up [http://lisa.mindbit.ro/](http://lisa.mindbit.ro/), even if it is a little old.

Or you could splash out on an [Arista]("http://www.aristanetworks.com/") switch which runs Linux. If that's beyond your budget there are Linksys switches running Linux and various replacement distros so it may be worth looking at them. But switching is generally done in hardware for speed.

Yes, Lisa seems to be what I am looking for, however this software seems to be somewhat outdated. I will try it out later and report back with my findings...

---

### Post by Groggster on 2011-12-01
> **Groggster said:**
> Yes, Lisa seems to be what I am looking for, however this software seems to be somewhat outdated. I will try it out later and report back with my findings...

Ehm, nope. The the downloads are down. I would suspect that the project is dead, and has been for some time. Anything else?

---

### Post by haqking on 2011-12-01
> **Groggster said:**
> Ehm, nope. The the downloads are down. I would suspect that the project is dead, and has been for some time. Anything else?

is there a reason you cant just get a switch ? they are like $30 ?

or is this a project ?

to be honest all you need to is build your routing tables, a router is a layer 3 switch [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

---

### Post by Groggster on 2011-12-01
> **haqking said:**
> is there a reason you cant just get a switch ? they are like $30 ?

or is this a project ?

to be honest all you need to is build your routing tables, a router is a layer 3 switch [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

Yes, it is for a project, and i really have to work at layer 2.

---

### Post by bab1 on 2011-12-01
> **Groggster said:**
> Yes, it is for a project, and i really have to work at layer 2.

If you want to connect multiple machines via layer 2 (without an external switch) you can create a bridge interface (br0),  See [**_[COLOR="Green"]here[/COLOR]_**]("http://www.linuxfoundation.org/collaborate/workgroups/networking/bridge") for some info.

---

### Post by Groggster on 2011-12-01
> **bab1 said:**
> If you want to connect multiple machines via layer 2 (without an external switch) you can create a bridge interface (br0),  See [**_[COLOR=Green]here[/COLOR]_**]("http://www.linuxfoundation.org/collaborate/workgroups/networking/bridge") for some info.

That is AWESOME! Exactly what I am looking for. Thank you so much!

---

