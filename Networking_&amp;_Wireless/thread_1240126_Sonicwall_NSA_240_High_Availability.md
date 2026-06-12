---
title: "Sonicwall NSA 240 High Availability"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by Saghaulor on 2009-08-14
I'm not sure where to post this, so feel free to move it accordingly.

I'm looking to purchase a Sonicwall NSA 240 firewall for my office, to replace my Sonicwall TZ-180.

I found an appliance called the Sonciwall NSA 240 High Availability. I talked to the Sonicwall sales engineer, and he informed me that the High Availability appliance is intended as a redundant firewall in the event that the Sonicwall NSA 240 goes down.

So I asked him, if it is a redundant device, doesn't that mean that the High Availability appliance can do the very same functions that the NSA 240 can do? He said yes. So then I asked him why I would need the NSA 240 in the first place, he told me that the High Availability appliance must be connected to the NSA 240 via crossover cable. But if the NSA 240 failed entirely, then there wouldn't be a signal traveling through the crossover cable, so for all intents and purposes, the situation would be exactly the same as if there wasn't a NSA 240, but merely the High Availability appliance.

**My question is, is he lying to me? Or am I missing something that would make this puzzle fit together?**

The reason why I care is, the High Availability appliance is half of the price of the NSA 240, so why spend double the price if I don't have too. Any advice is welcome.

Thank you in advance.

---

### Post by Saghaulor on 2009-08-17
bump

---

### Post by ryarramaneni on 2011-02-28
> **Saghaulor said:**
> I'm not sure where to post this, so feel free to move it accordingly.
 
I'm looking to purchase a Sonicwall NSA 240 firewall for my office, to replace my Sonicwall TZ-180.
 
I found an appliance called the Sonciwall NSA 240 High Availability. I talked to the Sonicwall sales engineer, and he informed me that the High Availability appliance is intended as a redundant firewall in the event that the Sonicwall NSA 240 goes down.
 
So I asked him, if it is a redundant device, doesn't that mean that the High Availability appliance can do the very same functions that the NSA 240 can do? He said yes. So then I asked him why I would need the NSA 240 in the first place, he told me that the High Availability appliance must be connected to the NSA 240 via crossover cable. But if the NSA 240 failed entirely, then there wouldn't be a signal traveling through the crossover cable, so for all intents and purposes, the situation would be exactly the same as if there wasn't a NSA 240, but merely the High Availability appliance.
 
**My question is, is he lying to me? Or am I missing something that would make this puzzle fit together?**
 
The reason why I care is, the High Availability appliance is half of the price of the NSA 240, so why spend double the price if I don't have too. Any advice is welcome.
 
Thank you in advance.
 
____________________________________
 
It may be too late answering this.
While the Sales Engineer is talking about the functionality, your concern of price is, as you can see it is almost at 50% difference which is offered to customers who go for Hardware failover purchase. If you purchase a HF without Regular Purchase of Primary, that will have registration and licensing problems and SonicWALL can remove the HF registration if no primary purchase is determine. Provided if it was approved by SonicWALL Sales etc.

---

### Post by Calcartman on 2011-04-22
We are using the NSA 240 High Availability - and for all intents and purposes what you have are two seperate NSA 240's. You connect them via a crossover cable, and then all internet connections, wireless APs, etc are split and connected to each of them. 
For example:
The X8 interface is what we use for HA and has a crossover cable between the 2 sonicwalls.
The x3 interface on each is the 3MB internet connection
The x4 interface on each is the 5MB internet connection
The x1 interface on each connects to the primary switch.

They both contain identical settings, for instance firmware updates on one, and fails over then updates the other.
And when one unit fails, it switches over to functioning on the other unit.

It is not a different box, as far as i can tell, they are identical NSA 240's. You just save 50% on the second device ;)

Hope that helps. The system has been flawless for us.

---

