---
title: "Ideal SOHO Network"
date: 2012-06-07
forum: Networking &amp; Wireless
---

### Post by dbrooke on 2012-06-07
Hello,

My networking skills are probably beyond novice, but not much behond ;-)! Having said that, I am redoing my SOHO network. I am thinking about purposing an x86 box to create a DMZ. (I have a few extra x86 machines, so I thought it would be interesting/educational to configure a linux firewall rather than a commercially purchased firewall).  

I am gaining 5 static I.P.'s and will be hosting my own services in-house (Web Servers, DNS, Mail, etc..). Again, I am doing this for as much for educational purposes as for functional purposes. (I am a mad scientist at heart!) ;-) 

I will most likely separate out some of these services onto different boxes.. ie., mail on one box, DNS on another, and Web on another. 

Anyway, so yes, this a general thread about the ideal SOHO network, but I guess it all starts with a good firewall and DMZ plan. I'm hoping I can get some comments regarding this part at least. 

I currently have:
 - 7Mb DSL line (w/, 5 I.P.'s and a Westell "wirespeed" DSL modem)
 - 1Gb switch
 - 2 - 100Mb switch's
 - Airport wireless base station

Can the firewall box protect both the LAN and DMZ?
 ie, can I have 3Nic cards, where one card is connected to the DSL modem, one is the DMZ, and one is the LAN?

Something like:
-----------------------------------
DSL modem --> 100Mbs switch #1

..100Mbs switch --> Linux Firewall for LAN (All I.P.'s)
                 
....Linux Firewall--> 100Mbs switch #2
    
......100Mbs switch#2(DMZ)--> AirPort Router (and LAN) (Pub I.P.#1)
................................A.P. Router --> 1Gb Switch (LAN)
...........................--> DNS server (Pub. I.P.#2)
...........................--> Mail Server box (Pub. I.P.#3)
...........................--> Web Server (Other Pub I.P.'s)
------------------------------------

If this doesn't look feasible, what would you change/suggest?

Thanks much!,
Donovan

---

