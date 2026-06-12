---
title: "setup a 2 network question"
date: 2011-09-11
forum: Networking &amp; Wireless
---

### Post by pythonsyntax on 2011-09-11
I want to setup a network but first i useing a linksys WR150N router and iwant to setup a network down stairs with a differnet router but does it matter what router i get or do i need what cables and hardware to do this with ubuntu?
 
Can this be done with cable internet and how would i set this up?

---

### Post by pythonsyntax on 2011-09-11
Someone got to know something on this forum?

---

### Post by Joebewan on 2011-09-11
Lots of folks know lots of stuff, but may not have seen your question yet, and may not at all since some don't even look at the cafe.

First; try closing, or asking a mod to close, this thread and opening a new one in a support forum, such as "networking and wireless".

Second; Unless your cable provider will allow you two modems (not likely) you'll need to decide that one of your two routers is to be the "master" so to speak and the other the "slave" router which would get its connection from the master.  Then connect your clients as you please.

Just make sure the two routers don't use the same subnet.  That won't work.

---

### Post by tubezninja on 2011-09-11
What you will need is a router that connects to your cable modem, and a network bridge (also commonly known as a "range extender."  This wil connect to your first router and act as part of the same subnet.

You might also get away with just stringing two routers together, but you'll basically have a NAT within a NAT would could cause some issues depending on what you're trying to do.

---

### Post by Old_Grey_Wolf on 2011-09-11
Linksys sells range extenders. They used to sell Workgroup Switches; however, I don't know if they still do or if they call them something else these days.

---

### Post by pythonsyntax on 2011-09-11
I thought all you need is a 2 router and some cat 6 cable?

---

### Post by Old_Grey_Wolf on 2011-09-11
> **pythonsyntax said:**
> I thought all you need is a 2 router and some cat 6 cable?

Well you can if the router supports the bridging you need. I did it with 2 Linksys WRT54G routers; however, it took me a while to figure out how to get it working. It was so much easier the next time I needed to set one up when I did it with a Workgroup switch that is intended for that purpose. Basically I connected the CAT 5 cable between the Linksys router/switch and the Workgroup switch and it worked.

---

### Post by cariboo on 2011-09-12
THis should really go in the Networking sub-forum. Moved.

---

### Post by SeijiSensei on 2011-09-12
> **Joebewan said:**
> Just make sure the two routers don't use the same subnet.  That won't work.

Put them on different channels as well to avoid radio interference.

---

### Post by cap10Ibraim on 2011-09-12
do you actually need to subnet and route, maybe it's enough to use an access point

---

