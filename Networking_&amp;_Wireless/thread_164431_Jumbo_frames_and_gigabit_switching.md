---
title: "Jumbo frames and gigabit switching"
date: 2006-04-22
forum: Networking &amp; Wireless
---

### Post by matsur on 2006-04-22
Hi All,

I'm considering buying a Netgear [GS716T](http://netgear.com/products/details/GS716T.php) to complete a recent home wiring installation.

For a few reasons that are out of my control, the cable modem is located in a portion of the house inaccessible by a Cat5e drop. To link it to the keystones the modem is plugged into a wrt54g, which is linked to another wrt54g (via wds) located in the central wiring closet. The system works fine in the current setup but I'm a little worried about adding the gigabit switch. I'd like to set MTUs on the gigabit capable NICs to 9600 bits once they are plugged into the netgear. However, will outgoing network traffic be adversely affected by the fact that the wrt54g can only handle maximum frame sizes of 1500 bits?

Secondly, is the GS716T my best option for the switch? I chose it because it was cheap and seemed to have a decent set of management tools. Is an unmanaged switch adequate for my needs? I'd like to fiddle with snmp w/ cacti and QoS, but these features are more gravy and are not essential to the operation of my network.

Any advice would be appreciated.
matsur

---

### Post by johnny2211 on 2006-04-22
IMHO any switch will do. I also don't see a reason to change the MTU. I use the exact same configuration with an unmanaged switch and two (WDS) Asus routers. Behind them is a complex network (ubuntu only servers ofcourse:cool: ) with high bandwith usage. Everything works fine, so far;)

---

### Post by mips on 2006-04-24
Forget about the jumbo frames, no need for it and you will most likely have hassles with the wireless.

Forget about QoS as in your environment it does not mean much.

Snmp is also not needed. Simple web interface is fine.

Personally I would go for a cheap switch that offers a basic web interface to configure the ports etc.

---

