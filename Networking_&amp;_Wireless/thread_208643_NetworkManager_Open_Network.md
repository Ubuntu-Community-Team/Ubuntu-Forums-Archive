---
title: "NetworkManager Open Network"
date: 2006-07-03
forum: Networking &amp; Wireless
---

### Post by phillip181 on 2006-07-03
I know I have brought this up before, but I still can't figure it out. 

First 
Dell Latitude
Broadcom 4306 internal wireless
Ndiswrapper

Issue. I still can't connect to open networks like coffeeshops or hotels with Network Manager. I can connect with Network Administrator but not with Network Manager. I can connect to my home network that has WEP with not problem and I haven't tried anything with WPA. 

This is the last bug I need to fix. Please help me.

---

### Post by queenorych on 2006-07-04
My rt2500 likes to default to restricted networks only (aka will not conenct to open).  This may be your problem.

iwlist security (should say open not restricted)

iwconfig wan0 key open
change wan0 to whatever your wifi interface is

---

### Post by ceaser on 2007-03-28
I have a similar problem, from what I can tell, there is some sort of compatability issue with the latest version of wpa_supplicant and ndiswrapper.

---

### Post by iamtherealwoody on 2007-03-29
I also have this problem.  How do we fix it? Anyone?

I can eventually get connected to the open network but i have to mess around with system>administration>network and I cant find a pattern with my actions and finally getting connected.  This is really annoying because this happens at school, im here everyday with my computer and it takes 10 minutes of fiddling to get back online.

---

