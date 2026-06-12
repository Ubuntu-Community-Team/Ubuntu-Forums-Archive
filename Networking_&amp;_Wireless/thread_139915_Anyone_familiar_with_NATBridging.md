---
title: "Anyone familiar with NAT/Bridging?"
date: 2006-03-05
forum: Networking &amp; Wireless
---

### Post by woedend on 2006-03-05
My question isn't how to do these, but if there are noticeable latency effects.  That is to say, if computer B was hooked to my computer A shared, either by ICS or bridge, and computer A was inactive, would computer B have a higher ping time/other latency issues than if hooked say into the router directly?  I know it has to have a bit of delay(in nanoseconds maybe?), but would it account for any millis?  Computer B would be used as online games, which is why I ask in the first place.  Thanks if anyone knows,
alex.

---

### Post by alamba on 2006-03-05
AFAIK...nope. Not any percievable effect. Like you said, nanoseconds maybe. The thing to consider here is that your bandwidth to your ISP is going to be far lower than between Computer A and Computer B. e.g. 512 kbps vs 5.5 mbps (wireless), or 10 mbps (wired)...if not higher. The effect of that extra hop is hardly noticable unless the distance between the 2 hops is really large.

Which is generally not the case at home/office networking scenarios.

Cheers!
Akshay

---

