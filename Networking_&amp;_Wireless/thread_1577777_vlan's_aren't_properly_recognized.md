---
title: "vlan's aren't properly recognized"
date: 2010-09-19
forum: Networking &amp; Wireless
---

### Post by wiz561 on 2010-09-19
Hi,

I have a goofy question.  I just started dabbling with vlan's, so I don't know if it's something I'm doing wrong or what.  I'm running Lucid Server and there's two vlan's going to that box...

vlan120
vlan140

VLAN120 is suppose to be on 192.168.120.0/24 and vlan140 is on 192.168.140.0/24.  I have dhcp configured to hand out those addresses and set ubuntu to dhcp.  

However, it seems like my wires are crossed because the vlan120 interface receives a 192.168.140.0/24 address and vlan 140 receives a .120 address.  I followed the ubuntu wiki guide on configuring ubuntu for vlan's. 

Is there something on ubuntu that's preventing this from properly working, or is it somewhere else on the network?  I haven't fully diagnosed it yet, but plan on doing more work tomorrow.  I figured I'd take a day break.  :)

thanks...

---

