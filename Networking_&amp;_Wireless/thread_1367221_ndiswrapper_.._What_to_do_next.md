---
title: "ndiswrapper .. What to do next?"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by timZZ on 2009-12-29
Hi Everyone,

I have tired looking into this issue myself but I have hit a stopping point.

Can anyone help me at least make some progress.

I am using Ubuntu 9.10 on a desktop. (I have decided to make this wireless)

I have an unsupported USB wireless stick.

Using nDiswrapper.  I have this working. (To a point)

The device _**can**_ 1. see local wireless networks 2. connect to any wireless network in which there isn't any security.

The device **_cannot_** connect to my local network using WEP.

I have narrowed this down to the ndiswrapper module.

I am just looking to know what is the next step.

I used the following ndiswrapper module.

[http://packages.ubuntu.com/karmic/misc/ndiswrapper-common](http://packages.ubuntu.com/karmic/misc/ndiswrapper-common)
[http://packages.ubuntu.com/karmic/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/karmic/misc/ndiswrapper-utils-1.9)
[http://packages.ubuntu.com/karmic/net/ndisgtk](http://packages.ubuntu.com/karmic/net/ndisgtk)

---

### Post by timZZ on 2009-12-29
**Additional information.

I can connect to my WEP secured router using a laptop hardy heron and Cisco Air350 credit card size wireless card.

---

### Post by Tholley on 2009-12-29
i'm still waiting on help on a wireless problem too, but I think I can help you... maybe...
 
change from WEP to WPA and you might be ok.
 
Allot of newer wireless adapters will only work with WPA now.

---

### Post by bkratz on 2009-12-29
> **timZZ said:**
> **Additional information.

I can connect to my WEP secured router using a laptop hardy heron and Cisco Air350 credit card size wireless card.



Since you are using ndiswrapper--- a lot of us ( including me!) can not connect with any encrypted wireless, there seems to be some issues involved with 9.10 and ndiswrapper, this may or may not affect you, it does me.  Non-encrypted works fine.

[https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/459716](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/459716)

---

