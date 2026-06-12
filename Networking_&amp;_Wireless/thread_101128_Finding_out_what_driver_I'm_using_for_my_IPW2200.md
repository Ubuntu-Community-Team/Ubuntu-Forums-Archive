---
title: "Finding out what driver I'm using for my IPW2200"
date: 2005-12-09
forum: Networking &amp; Wireless
---

### Post by daller on 2005-12-09
Hi There,

How do I find out what driver ubuntu uses with my IPW2200?

According to this:

[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards#head-f4ec44818f740e901d4f5d3368a4a96f4607696d](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards#head-f4ec44818f740e901d4f5d3368a4a96f4607696d)

...It uses the 0.19, and I should manually update the driver to at least 1.0.0!

What I wanna know, is if the wiki-solution is obsoleted?!

---

### Post by domo on 2005-12-09
I check the driver version on my breezy 2 days ago and it was the 1.0.6 version, so the wiki must be obsolete.

This one cause me hanging problems when the signal is low.
I think about upgrade them to 1.0.8

---

### Post by lcg on 2005-12-09
[QUOTE=daller]How do I find out what driver ubuntu uses with my IPW2200?[/QUOTE]
```
modinfo ipw2200
``` is the command you're looking for. AFAIK breezy comes with 1.0.6.

HTH,
Lars

---

