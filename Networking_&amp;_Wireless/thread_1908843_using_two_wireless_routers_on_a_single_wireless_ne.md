---
title: "using two wireless routers on a single wireless networkl"
date: 2012-01-14
forum: Networking &amp; Wireless
---

### Post by jarrah-95 on 2012-01-14
I have got two routers here, and due to the distances between them I would like to set each up to create a roaming wireless network (can walk between the two without disconnecting).
Thus far I have set both routers up with the same wireless settings, and different channels, but when I move between the two, my phone and kindle don't switch to the better one. 
I think this may be to do with the DCHP set-up, as I have found it necessary to run a DCHP server on both routers, as the second one does not pass on the server. 
Is there any way I can make it do this? 
(for your information, the main router is a Netgear DG834GUv5 and the second is a d-link dir-635)

Thanks.

---

### Post by Jive Turkey on 2012-01-25
What you are trying to do is set up a WDS, check the docs for your routers/firmware.

---

### Post by Drenriza on 2012-01-25
I got this solution at home. Tho i have a wireless router with a access point connected to it.
But first thing first. Are you trying to extend the signal from the first router
With the second router? Or does each router have its own wan (internet)
Connection?

---

### Post by catsrules on 2012-01-25
Yes, please explain more, 
I am doing this as well, and it works fine. But mine are all on the same network with one DHCP server. 
You don't want to use the WAN port because that will separate the networks. It should be all LAN ports between the two routers.

---

