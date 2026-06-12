---
title: "network recording, multiple network cards, sigh.."
date: 2009-12-13
forum: Mythbuntu
---

### Post by TehSnarf on 2009-12-13
Alright, I've got a Mythbuntu installation as a xenserver guest (I've tried it as a straight install as well...). I have two ethernet cards, eth0 on a 192.168.1.0 (getting 192.168.1.47 via DHCP) network, eth1 on a 10.12.5.0 (getting 10.12.5.35 via DHCP) network. I'm trying to get mythbuntu to record a stream from 225.3.0.3:2001. if eth0 is turned off, the video works. if eth0 is turned off, internet works, but no video. I have added a "sudo route add -net 224.0.0.0/4 gw 10.12.5.1", but still no go.

I'm not really sure what else to try at this point, other than to turn off eth0 when I'm wanting to record or watch tv.

Anyone think of anything I'm missing?

---

### Post by TheCook on 2009-12-17
Teh,
two things:
a.   Check your sub net.  At one point you say 225.3.0.3 and then you say 224.3.0.3.  They are both multicast addresses and the mask should cover the different address but its worth a try. 
b.  Probably of more help is to add a device to your route command.  Try adding one more bit to your route command
route add -net 225.0.0.0/4 gw 10.12.5.1 **dev eth1**

Might help if you try sudo route and send the results

---

