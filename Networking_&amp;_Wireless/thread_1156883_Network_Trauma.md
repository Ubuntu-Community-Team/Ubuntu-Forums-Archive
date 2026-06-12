---
title: "Network Trauma"
date: 2009-05-12
forum: Networking &amp; Wireless
---

### Post by Sum Guy on 2009-05-12
I am having a persistent network problem, that is really pushing me to the edge. Some of you may have seen a thread about my failed attempts to get a WiFi connection to my D Link DSL-G604T. I gave up on this, replaced the router with a Netgear DG834G v5 Modem Router (basically Netgear's version of the same thing) and the problem is worse. Now, the computer can't even see the network, let alone connect. In addition, the router mentions setup for linux users, so unlike the D Link it shouldn't refuse access. What's wrong this time?

Thanks in advance.

---

### Post by Sum Guy on 2009-05-12
UPDATE: This router now connects from within 2 feet of the comp, but won't connect further away in range. Also, for some reason, when the Netgear is near my comp the D Link becomes able to establish a connection. Interesting Note: The router causes an old Windows Tablet to constantly reboot, regardless of connection status. I need to fix this or at least identify a hardware config problem. WHAT IS GOING ON!?!:confused:

---

### Post by Sum Guy on 2009-05-12
I really need some help here. If i can't solve this, i won't be back until 10.10 when Ubuntu might have D Link connectivity, if you can help me fix it now, I can finally ditch Windows.

Thanks in advance.

---

### Post by mikezila on 2009-05-12
What channel is the router set to use?  Sounds like textbook heavy interference.  Try setting it to another channel, something (cordless phone, microwaves, lots of other stuff) may be jamming up your signal and causing all kinds of wierdness.

---

### Post by Sum Guy on 2009-05-13
Awesome, its online! Thanks. Also, just to satisfy my curiosity, why could two netbooks connect? Did they compensate for the interference better than Ubuntu? Thanks again, and don't worry about this, the problem is solved.

Incidentally the router's channel was on Auto for others with the same problem.

**UPDATE:** The router was correctly compensating for interference after me changing the channel from Auto to 11 (the D Link was on 11) but it seems that Ubuntu has a lower tolerance for interference than Windows, as, when I rebooted, I could not connect until I moved the comp. closer and set the channel back to Auto, where the comp. connected and stayed connected further away. Additionally, the Windows netbook I used for config. lost its net connection (not the WiFi). To make it easier to diagnose, the hardware setup:
Netgear router (replacing D Link) on a head high shelf set to Auto channel
1.8GHz Wireless phone base station next to it
Both are run through a filter to the phone line.

Any further suggestions?

---

### Post by mikezila on 2009-05-13
It's likely not the OS that's having causing varied reactions, but rather the wireless hardware in the different computers.  Not all wireless cards (chipsets, really) handle interference well.  The one laptop that's having trouble in Linux but not Windows might need to have it's config adjusted (for the change in channel) for it to pick up on it.  Try chaning the SSID on the router so that the computer sees it as a totally new network.  It could be that it's seeing a familiar name and trying to use the settings it used last time, which would be wrong now that the channel is different.

Though for detailed network setup I can't really be much help.  All of the wireless cards I've used under Linux have "just worked".

---

### Post by kryptikos on 2009-05-13
> **Sum Guy said:**
> Awesome, its online! Thanks. Also, just to satisfy my curiosity, why could two netbooks connect? Did they compensate for the interference better than Ubuntu? Thanks again, and don't worry about this, the problem is solved.

Incidentally the router's channel was on Auto for others with the same problem.

**UPDATE:** The router was correctly compensating for interference after me changing the channel from Auto to 11 (the D Link was on 11) but it seems that Ubuntu has a lower tolerance for interference than Windows, as, when I rebooted, I could not connect until I moved the comp. closer and set the channel back to Auto, where the comp. connected and stayed connected further away. Additionally, the Windows netbook I used for config. lost its net connection (not the WiFi). To make it easier to diagnose, the hardware setup:
Netgear router (replacing D Link) on a head high shelf set to Auto channel
1.8GHz Wireless phone base station next to it
Both are run through a filter to the phone line.

Any further suggestions?

This isn't an OS based issue. Chipsets used in the various wireless hardware are more finicky as to interference. Are these Broadcom AirForce One type cards, Linksys PCMCIA cards, Intels? Without knowing hardware types that does limit troubleshooting. 

Also, why do you have your wireless router right next to a wireless phone? And you said that you have both going to a phone line? I am guessing you have DSL as your ISP method? 

The issue here is most wireless phones walk/float/scan for the best channel. They tend to blast away at the highest power setting as well and will easily interrupt a home-office wireless router. I would look at:

* setting the channel if possible for your wireless phone. Set it to 1 and your router to 11. 
* Upgrade your phone to the 5.8 GHz models. 
* Check power settings on the router. It may not be at full strength and is getting run over by the phone. 
* Separate the phone and router by at least 5 feet. 
* Adjust the antennas away from each other.

---

### Post by mikezila on 2009-05-13
You can test this really easily by unplugging the cordless phone and seeing if it improves the situation.

---

### Post by kryptikos on 2009-05-13
And pull the battery backup if so equipped.....

---

### Post by Sum Guy on 2009-05-13
The two are next to each other because there is only one phone line, and yes, it is DSL, but the phone is .6 GHz below the router's frequency. The tablet that is getting bumped is a different computer to the linux box, as my dual boot XP won't boot its wireless drivers after getting some kind of virus. The card is an Intel 3945 abg internal, I believe the netbooks use Intel Atheros cards. Thanks for the input, I'll try the solutions asap (I need to leave in a few minutes). You've been very helpful:D

---

### Post by Sum Guy on 2009-05-14
OK, the router doesn't work even with the phone off, and none of the settings changes worked. The router remains invisible. I'm returning the router, but I would appreciate input on routers that work (with internal DSL modems). Thanks.

---

### Post by mikezila on 2009-05-14
This is very peculiar.

Does the laptop in question work with other networks (under Linux)?  Like, could you take it to Starbucks, or Panera or something to see if it works at all?

---

### Post by Sum Guy on 2009-05-14
I don't have access to public hotspots, not living in a big city or in the US, but after forcing an address on the D Link through a wire it works fine (in fact, thats mostly what I've been using). Could someone point me toward the Windows 3945 driver, and I'll try that. Thanks.

EDIT: Possibly the router is damaged in some way, as it seems to dislike the Windows Tablet I mentioned earlier as well (a second pc)

EDIT 2: Disregardb above requests, I have decided on a solution. I am going to use an old tower as a server with a wireless hotspot on it, to relay the net connection. This will also give me a server, with all of the associated benefigts. Thanks again for your help.

---

