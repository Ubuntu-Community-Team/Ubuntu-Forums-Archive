---
title: "networkmanager vs /etc/network/..."
date: 2010-11-20
forum: Networking &amp; Wireless
---

### Post by ljwobker on 2010-11-20
Just moved to 10.10 and networkManager is new to me... I'm building a set of servers for work and would greatly prefer to use the old style /etc/network/interfaces config files, as I have a number of scripts that help me configure things the way we need them...

so a couple of questions... I did search but didn't find what I needed, so if I missed it or there's a pointer somewhere that would also be fine.  ;-)


[LIST]
[*]what's the relationship between networkmanager and /etc/network/interfaces? is networkManager supposed to be a replacement, an enhancement, or something else?
[*]does a config in one have absolute priority over the other?  or is it a matter of which one is called first (or last?)
[*]long term, is there any reason to expect the /etc/network/interfaces config to go away?
[/LIST]

---

### Post by dineshs on 2010-11-20
[http://ubuntuforums.org/showthread.php?t=1620611](http://ubuntuforums.org/showthread.php?t=1620611)

---

### Post by chili555 on 2010-11-20
Thank you, dineshs, for the vote of confidence.> is there any reason to expect the /etc/network/interfaces config to go away?Not as far as I know, and for exactly the reason you articulate. Servers are usually run in runlevel 3 and headless. Network Manager is a GUI application. Therefor, in a server, the only method that is practical is manual configuration in /etc/network/interfaces.

I would have not the slightest hesitation to do:```
sudo apt-get remove --purge network-manag*
```

---

