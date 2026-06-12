---
title: "Dual-Monitor Problem in 12.04 w/ AMD Firepro m4000 Mobility"
date: 2013-02-18
forum: Multimedia Software
---

### Post by aeb105 on 2013-02-18
Hi all.   I am currently running Ubuntu 12.04.   The video card is a AMD Firepro Mobility.   Monitors are new Dells.   The laptop is a Dell Precision M-4700 which I have hooked to a docking station connected to both monitors.    It sees both monitors in Displays.  I am wondering how to get it to use both monitors as one.   The only option I got now is to Mirror which defeats the purpose of having 2 monitors.   Everytime I try and choose to use them both I get this error"

[B]"The Selected Configuration for Displays Could not be applied. 

Required virtual size does not fit requested virtual size requested.  "[/B] 

Basically any size I choose I get this message when I highlight and apply the other monitor.  .


Anybody???

---

### Post by aeb105 on 2013-02-20
Nobody has anything to try???

---

### Post by keenimage on 2013-02-22
I have the same system, but am running Ubuntu 12.10. I had similar issues when I first started setting it up. I tried the Catalyst drivers, but that created it's own set of issues (the FirePro M4000 isn't officially supported with those drivers).

When I reverted back to the stock drivers, the dual monitor stuff magically worked. I don't know why. I'm not sure what I did.

I don't have any 3D support currently, which makes my CPU run under heavy load in Unity, but I've pretty much resigned to hoping AMD releases some updated FirePro drivers at some point that will support this card.

---

