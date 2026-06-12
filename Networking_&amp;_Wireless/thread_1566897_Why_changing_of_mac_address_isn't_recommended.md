---
title: "Why changing of mac address isn't recommended ?"
date: 2010-09-03
forum: Networking &amp; Wireless
---

### Post by sulekha on 2010-09-03
Hi all,


 Why changing of mac address isn't recommended ?

 The possible reasons that i can find is 

 1) it can break firewalls
 2) it can break some DHCP implementations ?


Is there any other reasons that i have missed ?

---

### Post by BkkBonanza on 2010-09-03
I've never heard either of those reasons. I've changed MAC addresses without any problems many times. Do you have examples of firewalls or dhcp servers that actually can even tell if a MAC address has been changed? I don't see how they can tell. Unless you're talking about configuring a system and then changing the addresses afterwards which cause your config to break?

---

### Post by sulekha on 2010-09-04
> **BkkBonaza said:**
> I've never heard either of those reasons. I've changed MAC addresses without any problems many times. Do you have examples of firewalls or dhcp servers that actually can even tell if a MAC address has been changed? I don't see how they can tell. Unless you're talking about configuring a system and then changing the addresses afterwards which cause your config to break?




An example situation is given in the book "Linux system administration book" by evi nemeth et al as follows


At one time , 3com duplicated ethernet numbers among cards with different types of network connectors; they assumed that customers would order only a single type, this shortcut raised havoc at sites that were transitioning bw media and even caused problems on 3coms own internal network. mac address conflicts are deadly on the same nw

---

### Post by BkkBonanza on 2010-09-04
Ah, but that is because of duplicate MAC addresses, not "changed" MAC addresses. Duplicate addresses will definately cause major problems. So, to be sure, DO NOT change MAC addresses if it will result in **duplicates**. 

I can't believe 3com did that... how silly. I suppose they had some rationalization but as they soon saw it was obviously not a good one.

The first part of a MAC address is a vendor code so if you want to choose alternate MAC addresses to use and be sure they don't conflict then change the first part to some obscure vendor whose products you are sure will never end up on your network. 

this list may give you some ideas... 
[http://www.cavebear.com/archive/cavebear/Ethernet/vendor.html](http://www.cavebear.com/archive/cavebear/Ethernet/vendor.html)

I like "de-ad-be-ef-xx-xx" as these are not assigned (AFAIK). I've usually only changed MAC addresses when I want to mimic a specific device and then it would be dumb to also put that device on the same network (unless the intention is to see how duplicate addresses behave).

---

