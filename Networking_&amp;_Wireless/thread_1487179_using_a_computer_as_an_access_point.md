---
title: "using a computer as an access point"
date: 2010-05-18
forum: Networking &amp; Wireless
---

### Post by pearlzilla on 2010-05-18
Ok, I don't really know what I am doing here, but this is the situation.

I get free wireless internet from my apartment building.  Only my laptop has a wireless card.  A friend gave me a pci wireless adapter, so I can connect one of my desktops to the network.  I would like to set this box up as some kind of subnet router (its hardware is pretty outdated), and then set up another desktop as a seedbox.  I would then like to have a file server so I dont have to use a pen drive or ubuntu one to transfer files between the computers.  I have another old desktop I would like to use for this fileserver.  I have a 3rd desktop (way too many, I know) that has a video card I can hook up to my TV, and I would like to be able to watch videos from the file server on my tv with this one.

I was thinking maybe I should try and set the network enabled desktop up as some kind of router/access point, and then plug it into a switch to connect the rest of the machines.  It sucks that I have 2+ TBs of data storage lying around, because I can only put 2 drives in a desktop at a time.

I would really like to spend little or no money on this.  Anyone know of a way to accomplish these things?

---

### Post by BoneKracker on 2010-05-19
What I think you want is a firewall/router which happens to be connected on its external interface to a wireless network.  There are lots of tutorials on how to build your own router.

Typically, it's a dedicated low-end machine, but you can use your own desktop to do this (although it's generally not recommended, because you want your firewall/router to be the most secure machine on your network).  It just needs to have multiple network interfaces.  If your machine has a wireless adapter and a separate wired adapter, then you're all set as far as hardware goes.

Then, you just alter some sysctl settings (things like turning on IP forwarding, and some other settings that are different on routers), install and configure iptables (I'd recommend using something like shorewall to help you with that unless you're going to use a firewall/router-oriented distro like untangle or something), and you're in business.  Don't forget to set up DNAT rules to forward traffic to any nodes providing services to clients outside your little subnet.  Really, you should compile your own kernel with a configuration appropriate for a router (thinks like CONFIG_IP_ADVANCED_ROUTER).

Off the wired interface on your machine, you'd probably want to connect a switch, then you can plug your other network nodes into that.  If you want your other machines in your apartment to have wireless access on your own little subnet, then you could either replace that switch with a wireless router (and configure it as a switch -- i.e., don't use the wired uplink port and configure the wireless part to function as an "access point"), or you could keep the switch but plug an additional wireless card into the machine you're using as a firewall/router (which you would either use as an interface to a discrete dmz-like subnet or which you would bridge to your primary (lan) subnet).

If that all sounds like a confusing nightmare to you, then you probably ought to do one of the following:

a) just connect each of your boxes independently to the apartment community's wireless.

b) get your own wired connection and put a wired/wireless router on it to create your own subnet(s) (I would recommend a NetGear 3500L, which you can use open firmware on and satisfy your need to tinker).

Also, I'm not sure what you mean by a "seed box", but if you're talking about heavy seeding of torrents or the like, that would be a really dickish thing to do to the other people sharing the apartment community's wireless connection.  Don't do that.  If you're going to participate heavily in p2p sharing, have a little class and get your own connection.

---

