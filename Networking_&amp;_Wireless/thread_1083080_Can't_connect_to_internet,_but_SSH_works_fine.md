---
title: "Can't connect to internet, but SSH works fine?"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by miguel64086 on 2009-02-28
Hello all,
I'm very new to ubuntu and this the very first weirdness that I run into.
I can't connect to the internet. I can't connect to any website, can't ping anything, but **I am able to SSH** from other PC into my ubuntu machine?

I received a message about broken packages (but I can't seem to find that message again), so I went to the Synaptic Package Manager, chose Custom Filters > Broken > and then click RELOAD, but it says that it can't resolve the address. Maybe running APT-GET UPDATE would fix it, but I get the same thing.

The PC is connected directly to the router, the network manager is enable but the wired connection grayed out.
All seems to start after I install theu update sun-java6-jre (6-10-0ubuntu2) to 6-10-0ubuntu2

Any help would be appreciated. I'm fairly comfortable with terminal commands and google is my best fried, I don't know what to ask google to give me something meaninful.

oh, I forgot to say that I also disable ufw, but no luck

Thank you
Thanks

---

### Post by miguel64086 on 2009-02-28
I got it.
NetworkManager is the problem.
I found this link:

[http://tristram.squarespace.com/home/2008/11/3/ubuntu-810-network-problem.html](http://tristram.squarespace.com/home/2008/11/3/ubuntu-810-network-problem.html)

---

