---
title: "network traffic counter"
date: 2009-09-21
forum: Networking &amp; Wireless
---

### Post by Dedi Landsman on 2009-09-21
Hi.                     I'm subscribed for a cellular Internet package of 5Gigabytes per month with a cellular service provider, to keep an eye that I'm not over-downloading the 5 Giga [and being charged heavy extras by the cellular company], I installed on my Ubuntu a software called gtraffic in [http://www.gnomefiles.org/app.php/gtraffic](http://www.gnomefiles.org/app.php/gtraffic), which is a simple traffic counter for 3G USB cellular modems, with a graphic interface, and is having the possibility to reset the count at any given time [this is important as my 5 Giga count starts at the17'th of each month -the day I first signed with the cellular company], So far so good. Recently I bought a special cellular router, that is a router to which the 3G USB modem connects to it, and then the router is connected to the PC by a wire, as soon as I plugged the wire to the PC, Ubuntu recognized it out of the box- Ubuntu is online, So far so good. The connection then appears in the Network Connection as “Wired”- Auto Ethernet [and not Mobile broadband as when the 3G cell modem is connected directly to the PC], so far so good. The problem is that now the above mentioned software, Gtraffic doesn't respond- no download counting, so my question is: does anyone knows of an alternative application [with a graphic interface- because I'm such a newbie] for network traffic counting, that is working for wired Internet? Thanks for any help.

---

### Post by badger_fruit on 2009-09-21
Does your new router support SNMP (Simple Network Management Protocol)?
From previous experience (where I wanted to do the same thing), this is what is needed to do such a thing.

---

### Post by Dedi Landsman on 2009-09-21
Hi, thanks for helping. The router I'm using is: Edimax 3G 6200 WG. Whether it supports SNMP, I don't know really, it doesn't mention about it on it's box/ packet. The router comes with an installation CD, of a wizard and a complex vast manual. Quickly going through the manual, I did notice SNMP somewhere but not necessarily in the context of support, it is unclear, it appears in the section of security settings [firewall].  The wizard has many configurations options, can it run in Ubuntu too? The router home page is at:           
 [URL="http://www.edimax.com/en/produce_detail.php?pd_id=279&pl1_id=3&pl2_id=18"]http://www.edimax.com/en/produce_detail.php?pd_id=279&pl1_id=3&pl2_id=18 
[/URL]
 Thanks for any help.

---

### Post by badger_fruit on 2009-09-21
I've had a check of the manual and data sheets and there's no mention of if it has SNMP on it (it's unlikely though as it's not an "everyday" feature).

You see the problem is if you install any "local" software it will monitor the traffic between your PC and the router, if there are other users connected to the router, their traffic is going to go un-accounted for.  I'm sorry but I don't have any other suggestions on how to proceed; perhaps the IS provider may be able to alert you by SMS at a certain time each day on your useage?

Regards and good luck with your search!

---

### Post by Dedi Landsman on 2009-09-21
> You see the problem is if you install any "local" software it will monitor the traffic between your PC and the router, if there are other users connected to the router, their traffic is going to go un-accounted for.Hi and thanks again. it is only me who is using this router [for the reason of using such router see the first post at the thread in
 [http://www.linuxquestions.org/questions/linux-networking-3/wireless-3g-router-751439/#post3686322](http://www.linuxquestions.org/questions/linux-networking-3/wireless-3g-router-751439/#post3686322)  if you like] so there is no problem of traffic goes unaccounted for. if you know any "local" software to monitor the traffic, please, mention it. Thank you so much for any help.

---

### Post by badger_fruit on 2009-09-21
[http://www.ubuntugeek.com/network-traffic-analyzers-for-ubuntu-system.html](http://www.ubuntugeek.com/network-traffic-analyzers-for-ubuntu-system.html)

---

### Post by Dedi Landsman on 2009-09-21
Thanks. I'm gonna check it

---

