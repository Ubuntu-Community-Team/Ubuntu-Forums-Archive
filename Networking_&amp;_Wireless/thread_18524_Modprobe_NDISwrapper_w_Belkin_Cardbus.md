---
title: "Modprobe NDISwrapper /w Belkin Cardbus"
date: 2005-03-07
forum: Networking &amp; Wireless
---

### Post by spd106 on 2005-03-07
Hi all, 

I've managed to get the network card for my laptop to work through trawling forums and help pages, the only trouble comes in start up, i don't know how to get the card to automatically configure. Although i can do it manually, i am rather lazy and hope there is a quicker way.

details follow:

Network Card - F5D7010uk Belkin 54g Cardbus with the Broadcom 93406 rev3 chipset

Ubuntu 4.10 'Warty' from Linux Format Magazine DVD.

NDISwrapper 0.12 from sourceforge.net

I tried the supplied Belkin driver bcmwl5.inf but it didn't work, eventually I tracked down a newer driver for dell laptop which was also called bcmwl5.inf. This one does work. 

As everyone says i did the "ndiswrapper -m" command.

Now when i boot up, the network card light comes on and the 'configure network' message causes a short pause then it says 'ok' and moves on. The only message that fails is dhcp name resolution

I log in, and can't access the network.
iwconfig wlan0 shows no information
iwlist wlan0 scan doesn't show the ap

I found that if i

1) unload modprobe, 

2) set the card's details via iwconfig, (i should mention that i use wep in open     mode).

3) reload modprobe, 

i can now find the ap and access the network.

i've written a script to do this, but i don't know where to put it, and it still seems like a less than elegant way to do it.

I tried using the Gnome network configuration tool, but it doesn't work and if i try it after manual set up it seems to stop the card working. 

Thanks for any help, i'd be glad for someone to tell me more about what to do or point me in the right direction.

I'm glad to be away from the clutches of "Sir" Gates at last!!!

---

### Post by burlap on 2005-03-07
This is just a vague hint (I use d-link - acx 111 - with ndiswrapper):

I had once problems to reconfigure my card and it turned out that setting anything with gnome-network while the module was loaded did not work. But I am not too sure. 

So you can try to:
[list]unload module, set and activate the card with gnome-network[/list]
[list]manually edit /etc/network/interfaces[/list]

---

