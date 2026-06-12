---
title: "Efficient Multicast Fail (Cisco, IGMP Snooping, CGMP)"
date: 2012-06-26
forum: Networking &amp; Wireless
---

### Post by asmoore82 on 2012-06-26
SOS! Real Old School Cisco Network Engineering Wisdom Needed :D.

So we've got 100's and 100's of PC's to re-image. I've had several Clonezilla servers successfully installed on top of Ubuntu 10.04 for quite some time now and we've got lots of WDS servers lying around too.

A couple of the clonezilla servers can already multicast all day long but they service only isolated switches and then provide NAT Routing to the outside world. We'd really like to use multicast more effectively on the production network. Of course "more effectively" brings us to the great mystery of how to constrain the multicast from flooding all the local switch ports.

I've dug down into this far too deep and the scary thing is that now when I google the problems we have now I find lots of old stale threads with folks asking questions that I already know the answers to. I really want to reply there but the threads are far too old.

So I know that IP Multicast and IGMP are layer 3 operations and the switch flood is a layer 2 problem. And I know that IGMP Snooping is a layer 2½ solution. I know that all the newer Cisco equipment supports snooping out of the box and it's enabled by default. I also get that it will be entirely dormant until there is a true layer 3 device sending regular IGMP Queries to be snooped upon.

Well, some of our locations fully support IGMP snooping with Cisco 2950's and 2960's. Other locations are a mix of 2950/2960's and older 2924's and 2900's. These less-than-or-equal-to 2924's do not support IGMP snooping but they do support the Cisco ancestor: CGMP. CGMP is a true layer 2 communication whereby a layer 3 device, again the designated IGMP Querier, directly maps client MAC addresses to multicast MAC addresses and sends this info out to the layer 2 switches.

You remember how I said I've already dug into this way too deep? Well, using libpcap, pypcap, and python-dpkt, I've written a cross platform IGMP Querier and CGMP Server in python. It actually works and is very effective at stopping the layer 2 flood.

Oh but the solution is short lived. Neither WDS nor Clonezilla can reliably complete a multicast under this scheme. WDS stops without explanation or error message and bumps the clients down to unicast. Clonezilla fails with a CRC Error message. After tug-of-war with this for a week I finally broke down last night and attempted to use a real physical Cisco 2800 router.

I got the exact same results so that makes me feel way better about my python code; but what's going on? Googling CGMP leads to a lot of dead ends as the world has moved on to IGMP, but I just have to know why it's not working. The same switches can unicast just fine and multicast fine with a flood. But it would appear that attempting any CGMP optimizing causes the switches to corrupt the multicast stream.

---

