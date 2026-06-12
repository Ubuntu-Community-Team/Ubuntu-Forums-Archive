---
title: "What hath NetworkManager wroght?"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by tomhorsley on 2009-11-10
I've got a KVM virtual ubuntu 9.10 machine. I bring it up and wait till it responds to ssh, and I start running my testbed on it. About two minutes later, I see log entries that say NetworkManager has come along and done a brand new DHCPDISCOVER on the same network interface that is clearly already functioning because I'm ssh'ed into the virtual machine. This new discover trashes the old connection, and winds up forcing a new IP address. What the heck is it doing? Why is it doing it? How do I get it to leave my perfectly functional network alone?

---

### Post by iponeverything on 2009-11-10
If you add the interface to /etc/network/interfaces it will no longer be managed by network manager.

---

### Post by tomhorsley on 2009-11-10
When I installed previous versions of ubuntu, I didn't have to fiddle with anything, the network just worked. Has Karmic made the same idiotic mistake fedora made of thinking that NetworkManager is a viable replacement for the old network code?

Anyway, I found the line already in the interfaces file, but commented out. I uncommented it and thought things were working, but then NetworkManager crushed my connection again.

Somewhere in there, while investigating the problem, I changed the network device definition on the KVM host, so apparently I had the "device" now named eth1, but the "interface" named eth0. After removing /etc/udev/rules.d/70-persistent-network and rebooting, I finally got the device and the interface named eth0 and NetworkManager finally left me alone.

This doesn't seem to be an improvement from previous releases :-).

---

### Post by Iowan on 2009-11-10
Somewhere around here is a thread that tells how to disable Network Manager without removing it. Seems like there was more to it than just unchecking a box on the startup sessions.

---

### Post by dmizer on 2009-11-10
> **Iowan said:**
> Somewhere around here is a thread that tells how to disable Network Manager without removing it. Seems like there was more to it than just unchecking a box on the startup sessions.

It's perfectly safe to remove network-manager-gnome. It doesn't even take any meta-packages with it.

---

