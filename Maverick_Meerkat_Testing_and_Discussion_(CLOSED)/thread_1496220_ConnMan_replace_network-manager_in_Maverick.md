---
title: "ConnMan replace network-manager in Maverick?"
date: 2010-05-29
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by cristianfere on 2010-05-29
ConnMan replace network-manager in Maverick? Or is only a more option?

[https://wiki.ubuntu.com/NetworkSettings](https://wiki.ubuntu.com/NetworkSettings)
[http://www.omgubuntu.co.uk/2010/05/help-test-ubuntu-1010s-proposed-network.html](http://www.omgubuntu.co.uk/2010/05/help-test-ubuntu-1010s-proposed-network.html)

---

### Post by 23meg on 2010-05-29
It's currently targeting UNE only, but should be usable on the desktop as well.

---

### Post by MacUntu on 2010-05-29
Connects fine (after entering the password in an unmasked field #-o). I hope the lack of features is related to the applet rather than ConnMan?

---

### Post by screaminj3sus on 2010-05-29
Network manager works great, no need to replace it.

---

### Post by cariboo on 2010-05-29
I just installed it on my netbook, I have to say so far aside from the lack of features, I'm impressed, when coming out of hibernate, it is connected before the desktop finishes loading.

---

### Post by anders_c_ on 2010-05-29
Installed on Lucid, works great, but the "Open network settings" is greyed out...

---

### Post by MacUntu on 2010-05-29
> **screaminj3sus said:**
> Network manager works great, no need to replace it.

I too am missing the motivation behind this change. It's not in the blueprint and not in the UDS log: [https://wiki.ubuntu.com/DesktopExperienceTeam/MaverickUDSLog#dx-m-indicator-network](https://wiki.ubuntu.com/DesktopExperienceTeam/MaverickUDSLog#dx-m-indicator-network)

One reason might be that ConnMan is optimized for lower spec'd systems (keep in mind - it's only planned to replace NM in the UNE):

> The ConnMan project provides a daemon for managing internet connections within embedded devices running the Linux operating system. The Connection Manager is designed to be slim and to use as few resources as possible, so it can be easily integrated. It is a fully modular system that can be extended, through plug-ins, to support all kinds of wired or wireless technologies. Also, configuration methods, like DHCP and domain name resolving, are implemented using plug-ins. The plug-in approach allows for easy adaption and modification for various use cases.

[http://connman.net/](http://connman.net/)

---

### Post by cristianfere on 2010-05-29
> **MacUntu said:**
> ...

One reason might be that ConnMan is optimized for lower spec'd systems (keep in mind - it's only planned to replace NM in the UNE):



My question is because I don't see any news about integration off Network-manager in indicator applet.

And replace the network-manager now that is stable, looks like a regression.

---

### Post by cariboo on 2010-05-29
The focus for Maverick is going to be the UNE, there are quite a few changes coming down the pipe in the next couple of weeks. 

We already have Unity working, the Unified Application Menu is ready for apps, now conman. Watch out for Windicators coming soon.

I run the UNE on an atom n270 powered netbook, anything that makes things run faster is fine with me. :)

---

### Post by MacUntu on 2010-05-30
> **cariboo907 said:**
> anything that makes things run faster is fine with me. :)
Get yourself a real notebook. :twisted:

---

### Post by gnomeuser on 2010-05-30
> **MacUntu said:**
> I too am missing the motivation behind this change. It's not in the blueprint and not in the UDS log: [https://wiki.ubuntu.com/DesktopExperienceTeam/MaverickUDSLog#dx-m-indicator-network](https://wiki.ubuntu.com/DesktopExperienceTeam/MaverickUDSLog#dx-m-indicator-network)

One reason might be that ConnMan is optimized for lower spec'd systems (keep in mind - it's only planned to replace NM in the UNE):



[http://connman.net/](http://connman.net/)

Largely to me it sounds like ConnMan is somewhat pointless duplication of effort.

[http://blogs.gnome.org/dcbw/2009/06/25/networkmanager-and-connman/](http://blogs.gnome.org/dcbw/2009/06/25/networkmanager-and-connman/)

I am not inclined to agree with Dan that reimplementing standard cli tools as libraries which can be easily and correctly used in application (which appears to be the aim, making things lightweight is a beneficial sideeffect here).

That being said, regardless it makes little sense long term to have 2 different frameworks to do the same job, it's 2 different things to go wrong and to require support. I think we will see one win out, perhaps not in the Maverick timeframe though but I am convinced that it will happen.

---

