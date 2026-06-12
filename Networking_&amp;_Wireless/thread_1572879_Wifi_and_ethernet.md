---
title: "Wifi and ethernet"
date: 2010-09-11
forum: Networking &amp; Wireless
---

### Post by jnfurst on 2010-09-11
Hi I have a theory question.

How does Ubuntu handle the situation where I am plugged into ethernet while also connected via wifi to a wireless access point? Assume that I have good connections to both and nothing between the computer and the internet.

My boils down to how does Ubuntu pick which interface to use? Does it use both? Does it split the traffic? Any information related to this scenario would be welcomed! 

Thanks

---

### Post by BkkBonanza on 2010-09-11
I believe it doesn't split traffic by default but not sure which it chooses. Probably can set that. I use Wicd and can config priority but not sure about default Network Manager. It probably chooses wired LAN over wifi though.

It is possible to configure combining bandwidth through either bonding or routing tables. It's a bit of command line work and knowledge.

---

### Post by MaindotC on 2010-09-12
It definitely doesn't split the traffic.  Any time I've been on wireless and then I plugged into wired NetworkManager chose the wired connection.  I don't know where this is defined or configured - it must be somewhere - but it probably does some type of internal diagnostic looking for whichever is the fastest connection.

---

