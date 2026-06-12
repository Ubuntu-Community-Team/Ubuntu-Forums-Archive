---
title: "Ubuntu firewall server in OpenStack"
date: 2013-03-28
forum: Networking &amp; Wireless
---

### Post by MasterOfBinary on 2013-03-28
Hey guys. I'm trying to setup an Ubuntu firewall machine in OpenStack. I've found loads of information on it, such as [http://ubuntuforums.org/showthread.php?t=926001](http://ubuntuforums.org/showthread.php?t=926001), which I followed mostly. However, most places say you need two network cards, which (AFAIK) isn't possible. Well, from some documentation I found, it seems like it is possible but not trivial. I may be wrong.

Basically what I would like to do is set up a server that my other OpenStack servers could route the incoming and outgoing traffic, but with only one network card. Could someone suggest a strategy to use - what package, some documentation somewhere, or just how to adapt the two NIC tutorials to my needs?

I know it's an awkward setup, but it's for a university project. If that has any effect on how you answer.

---

