---
title: "Wireless connection to Mac Mini is unstable"
date: 2010-11-05
forum: Networking &amp; Wireless
---

### Post by martymcc on 2010-11-05
I have an eMachines e520 with Maverick Meerkat (upgraded from Lucid Lynx). I recently bought a new Mac Mini. Both were added to a wireless home network with four Windows machines and a network attached storage.

Ubuntu can't see anything on the Windows for Workgroups laptop if there's a dot in the name, and the Mac can't connect to it at all, but that doesn't seriously bother me. Other than that, everything works except the connection between Ubuntu and the Mac.

My main issue is that Ubuntu and the Mac sometimes can see each other and sometimes they can't. I set them up to ping each other every 30 seconds, and there are intervals of many minutes when nothing comes back to the Mac from Ubuntu, and there are different intervals when nothing comes back to Ubuntu from the Mac. The problem existed in Lucid Lynx and is still there in Maverick Meerkat.

I posted this issue on a forum on apple.com as a Mac issue, but it's also an Ubuntu issue. The reason it's an Ubuntu issue is that the eMachines laptop also has an earlier installation of 64-bit Fedora, and the connection between the Mac and Fedora is stable.

Ubuntu, Fedora and the Mac have three different local IP addresses. They all point to the wireless Internet router on my home network as the gateway.

The wireless interface is identified as Atheros AR5001 in Ubuntu, and as Atheros AR242x in Fedora, but they both use the built-in ath5k driver. Do we know that ath5k is the same code in both systems?

Since both Linux systems are using the same hardware, nominally the same drivers, and the same user configuration, the difference could be in the kernel.

Kernel versions, as identified by uname -r:
Fedora: 2.6.32.11-99.fc12.x86_64
Ubuntu: 2.6.35-22-generic

If I upgrade Fedora, or change to a 32-bit version, would wireless connectivity become as unstable as it is in Ubuntu? Would I get a stable connection if I change Ubuntu to a 64-bit system, or if I downgrade to an older Ubuntu version than Lucid Lynx?

---

