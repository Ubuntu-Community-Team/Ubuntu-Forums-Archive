---
title: "Combine 2 connections?"
date: 2011-11-30
forum: Networking &amp; Wireless
---

### Post by SantanuBarai on 2011-11-30
[B][COLOR=DarkOliveGreen][B][FONT=Courier New][SIZE=4]I have 2 LAN cards. So 2 LAN ports. I have 2 different Internet connections.
 
 Now I want to combine 2 connections so that I can get combined speed.  That means if I have 1 MBps and 2 MBps connections the combined speed  will be 1+2=3 MBps.
 
 Is this possible? If yes then please tell me how.[/SIZE][/FONT][/B][/COLOR][/B]

---

### Post by jonobr on 2011-11-30
Open to correction and my information may be dated, 
but I used to work for a vendor company that used to make remote access head-end equipment for telcos for DSL, Cable and dial up access. Basically the euipment you connect to when your connecting to the internet
In most cases, the idea of link aggregation or bonding (or with dial up called MLPP- Multilink PPP) required all the calls, and connections to terminate on the one device and the device/ISP had to support it. 

The device has to know the two channels belong to the same session and needs to know either to round robin data to the combined pipe or load balance data between the two.

Im not sure a lot has changed since then, but again , adding your two wan connections together used to require a lot more complexity and support from the carrier side the just bonding two ethernet connections as described [here]("https://help.ubuntu.com/community/UbuntuBonding")

---

### Post by SantanuBarai on 2011-12-01
> **jonobr said:**
> Open to correction and my information may be dated, 
but I used to work for a vendor company that used to make remote access  head-end equipment for telcos for DSL, Cable and dial up access.  Basically the euipment you connect to when your connecting to the  internet
In most cases, the idea of link aggregation or bonding (or with dial up  called MLPP- Multilink PPP) required all the calls, and connections to  terminate on the one device and the device/ISP had to support it. 

The device has to know the two channels belong to the same session and  needs to know either to round robin data to the combined pipe or load  balance data between the two.

Im not sure a lot has changed since then, but again , adding your two  wan connections together used to require a lot more complexity and  support from the carrier side the just bonding two ethernet connections  as described [here]("https://help.ubuntu.com/community/UbuntuBonding")

Thanks a lot for your king information. Let me check it out.

---

### Post by jonobr on 2011-12-01
Hello

Just to reiterate,

Check with your ISP

If wan connections are supplied by the one ISP there may be a chance to bond or aggregate.
In the old (10 years ago) days, we used to support up to 16 bonded 64 k ISDN channels.

---

