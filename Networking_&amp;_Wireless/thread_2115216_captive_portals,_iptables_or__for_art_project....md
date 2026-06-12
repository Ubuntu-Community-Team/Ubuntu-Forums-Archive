---
title: "captive portals, iptables or ??? for art project..."
date: 2013-02-12
forum: Networking &amp; Wireless
---

### Post by kristofferorum on 2013-02-12
Hello,

I'm an artist looking to develop a new way of distributing text, internet, video and interactive based art, outside of the internet. Through a network of cheap used routers and computer I am intending to build a number of wireless networks, not connected to the internet, that would that only one particular php/mysql page (preceded by a splash page) to anyone who connects to the network. The intent is to build a hardware/sotware solution that would enable more people to make their own nodes, eventually creating a low cost network of publicly accessibly art works linking specific physical spaces with particular electronic works of art.  

I've been looking into various ways of doing this, such captive portals and iptables. But I remain unsure of where to start, so before I delve further into a specific technology (of which I have very little knowledge), I was wondering if anyone had any ideas for the cheapest and easiest way redirecting everyone who connects to the network to a page? 
What would be the minimal hardware set-up for something like this? Would one low powered (atom) computer and an old router do the trick?
Is there a linux distro that would be an especially good starting point?
ANY help or suggestions would be greatly appreciated.
Kristoffer Ørum

---

### Post by Bucky Ball on 2013-02-12
Welcome to the forums. Even though this is about creating a LAN (local area network), or more than one, I'm tempted to move it to the ***Art & Design*** section. ;)

As for the Linux distro, there are many and some that would suit what you are doing, or be massaged into doing it. Hardware-wise, you might want to research the Raspberry Pi. It, or perhaps a variation on it, could be just what you're after. See here.

[http://www.raspberrypi.org/quick-start-guide](http://www.raspberrypi.org/quick-start-guide)

That runs lightweight distros, among other things, and can be used for wireless via a USB adapter. There are a few threads on the Raspberry Pi here, also.

A lot will depend on how much RAM as to what distro you use (more to the point what desktop environment and resource hungry apps simultaneously). Sounds like you might only need a couple or several apps and a very lightweight desktop environment if you are creating the physical nodes.

You may want to create something custom; easy enough depending on how much time you have to research what you are trying to realise. You could go for a minimal install of Ubuntu and add only the packages you want/need, for instance. A lightweight desktop environment (xfce, lxde, but there's plenty lighter) and not much else.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Hope that helps. Sounds interesting, even though I'm not exactly sure what you are attempting. (Where are the nodes? At home? In a certain space for the network to connect to? Do you mean when they go to your website? Good luck.

PS: You might consider posting what you need the machine/device to do first (wifi, AV), then it will be easier to figure out what would suit hardware/software wise.

---

### Post by kristofferorum on 2013-02-14
Hi Bucky,
thanks a lot attempting to answer my vague questions I've friends to draw a simply diagram of what I'm trying to achieve.
[IMG]http://s3.postimage.org/js2y3xnk3/model.jpg[/IMG]



I wasn't going for a rasPi solution hardware-wise as I've already got a bunch of asrock 330 (with Intel® Dual Core Atom™ 330 processors) and some other atom powered devices lying around - these a I have  in mind, mostly because the netbook fad seems over and I figure there a lot of these lying around unused..

Sorry about the misused terminology the nodes are other similar set-ups located several places - other closed systems serving single php/mysql pages in other specific locations.. 

i Hope this helps clear up things a little bit,
best,
Kristoffer

---

