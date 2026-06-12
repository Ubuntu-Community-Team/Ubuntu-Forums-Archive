---
title: "Ubuntu through Wireless and VM through Wired"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by EliteLegend on 2009-11-18
I am trying to do something like this:

[LIST]
[*]All networking connections originating from Ubuntu should go through my Wireless connection
[*]All the connections originating from within Windows (installed inside a VM) should go through the wired connection.
[/LIST]

Now, I was able to get the second one by bridging my VM's adapter to the eth0 interface. But whenever I connect the ethernet cable, Ubuntu refuses to use my wireless connection for any further connections. I am guessing that wired has a higher preference over wireless but is there some way I can achieve the above situation?

---

