---
title: "networking issue (could use some advice)"
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by alfonzo227 on 2009-03-27
This may seem lengthy but in all likelihood i am just being an idiot.


I'm having trouble setting up an ad-hoc network between my two laptops running Ubuntu. Both have working wireless cards, and both can connect to my home wireless network (internet->cable modem->router w/ wireless, and then one wire running to one of the laptops). I'm trying to get the other laptop, which is next to the one with an ethernet connection to the router, some internet as well. I thought that the best way to do this was by setting up an ad-hoc network in my room and then share my internet connection somehow (i'm not using the home wireless because it has a rather weak signal).

First question: Is there a better way to get both my computers connected to the internet from one ethernet cable? i would rather not purchase a wireless access point; is it possible to have one laptop with an internet connection act as a WAP?

Other than that, I can't seem to get an ad-hoc network working. 

These are the laptops
DELL
dell latitude c600 running ubuntu intrepid ibix. 
old wireless card in pc card slot 
from lshw:
description: Wireless interface
          product: ADM8211 802.11b Wireless Interface
          vendor: ADMtek
          physical id: 1
          bus info: pci@0000:06:00.0
          logical name: wmaster0
          version: 20
          serial: 00:04:e2:7f:f6:de
          width: 32 bits
          clock: 33MHz
          capabilities: pm bus_master cap_list logical ethernet physical wireles


EEE PC
asus eee pc 1000 running ubuntu 9.04 jaunty netbook remix beta
from lshw:
network
                description: Wireless interface
                product: RT2860
                vendor: RaLink
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: ra0
                version: 00
                serial: 00:15:af:bc:ed:30
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rt2860 ip=192.168.1.107 latency=0 module=rt2860sta multicast=yes wireless=RT2860 Wireless

How do I set up an ad-hoc network between these (if that's even the right thing to do)? Any network set up by one of the laptops is not noticed by the other, and i've created the same network simultaneously on both, attempted to join a hidden network by the same name...

Any help at all would be hugely appreciated. Thanks in advance.

Hans

---

### Post by mark1692 on 2009-04-26
I need some help with the new Ubuntu 9.04 Remix on a Asus PC100HE.

The network is up and working as far as Internet connecting but whenever I attempt to connect to any of my other networked devices or computers I get this message ( UNABLE TO MOUNT SOURCE ).

I Also get this same message when trying to setup a networked printer.  This same PC1000HE when running Windows XP has no problems connecting to these same devices or computers.   

I have setup two other laptops and Desktop systems with the 9.04 standard edition and they have no problems with the networking connections or sharing there resources.

Is there something I am missing or is there a bug in this somewhere?

Mark

---

### Post by mark1692 on 2009-05-12
This question is directed to ( _**alfonzo227**_ );

If I understand your question correctly:
   "" Both have working wireless cards, and both can connect to my home wireless network (internet->cable modem->router w/ wireless"".  
   You have everything you need already.   You do not need to setup a ad-hoc network.   Just run a cat 5 cable from the router to each computer/laptop or connect wirelessly with the router.  You will have to enable file sharing on both computers.   Since both computers are able to connect to the internet they should also be able to see and talk to each other. 
You can add an inexpensive wireless bridge for under $20.00 on eBay that will greatly extend your wireless routers range.

I hope this helps;  mark1692

---

