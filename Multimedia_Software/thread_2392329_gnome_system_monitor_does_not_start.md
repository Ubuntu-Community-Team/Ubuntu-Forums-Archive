---
title: "gnome system monitor does not start"
date: 2018-05-19
forum: Multimedia Software
---

### Post by invisibleshadowghost on 2018-05-19
Hey guys,

I have a completely fresh Ubuntu 18.04 installation, having the problem that the gnome system monitor does not start.
Trying to run gnome-system-monitor in a terminal results in
```
You need to connect this snap to the gnome platform snap.

You can do this with those commands:
snap install gnome-3-26-1604
snap connect gnome-system-monitor:gnome-3-26-1604 gnome-3-26-1604

(the '3-26-1604' number defines the platform version and might change)


```

For me, this does not feel normal. Or is this intended to work like this?

Best regards
InvisibleShdowGhost

---

### Post by cruzer001 on 2018-05-19
IMO its better to use apt.
```
sudo apt install gnome-system-monitor
```

Or the GUI for apt
[https://www.google.com/search?client=ubuntu&hs=VpB&channel=fs&ei=9pAAW6y7H9GKjwOQxZnADg&q=synaptic+package+manager+ubuntu&oq=synaptic+package+manager+ubuntu&gs_l=psy-ab.12..35i39k1j0l3j0i67k1j0l3j0i67k1.17197.20836.0.25162.7.7.0.0.0.0.129.740.3j4.7.0....0...1.1.64.psy-ab..0.7.736....0.ZF8WiLiUC3E](https://www.google.com/search?client=ubuntu&hs=VpB&channel=fs&ei=9pAAW6y7H9GKjwOQxZnADg&q=synaptic+package+manager+ubuntu&oq=synaptic+package+manager+ubuntu&gs_l=psy-ab.12..35i39k1j0l3j0i67k1j0l3j0i67k1.17197.20836.0.25162.7.7.0.0.0.0.129.740.3j4.7.0....0...1.1.64.psy-ab..0.7.736....0.ZF8WiLiUC3E)

---

### Post by invisibleshadowghost on 2018-05-19
Thanks, that works!

---

### Post by cruzer001 on 2018-05-19
Welcome

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

