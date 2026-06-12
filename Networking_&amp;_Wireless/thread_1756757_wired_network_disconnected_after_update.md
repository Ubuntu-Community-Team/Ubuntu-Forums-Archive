---
title: "wired network disconnected after update"
date: 2011-05-12
forum: Networking &amp; Wireless
---

### Post by belialcouk on 2011-05-12
Hey, this is the first time I have had to post up on this forum; most of the time a quick search reveals someone with the same problem and it works! This time no such luck :(

I have been running 10.10 Meerkat for a while now. But recently an update came through, which I authorised, and ever since I have been unable to access the internet from that machine.

The radial networking icon on the top bar whizzes for the first minute after boot, and then exclaims (!) "Disconnected - You are now offline".

From the command line a quick ```
ifconfig
``` reveals that the eth0 adapter is up and has an ipv6 address, but no ipv4..? Also the RX and TX are moving, with no errors.

Then running ```
dhclient
```, I can see offers and AKs coming back with a valid IP (in fact it's assigned a static IP from the DHCP server, so I know it's talking to it).

Running ```
ifconfig eth0 up
```, does nothing. running ```
ifconfig eth0 down
```, takes it down. Then an ```
ifconfig eth0 up
```, brings it back to the same state as before, but still no LAN or WAN connection is available.

I'm totally at a loss... IMHO it is getting DHCP responses, but the IP being doled out to it is not being registered by the adapter for some reason?! The annoying thing is; this was working... and has been for years now with various versions of Ubuntu. I can only assume that a driver update has bawlked by adapter. Is there anyway to look at recently applied updates, and rollback? 

I do have a spare diddy HD which I could try installing 11.04 on, but I'd rather avoid the hassle right now and get this fixed. (I have software raid on 2 supplementary drives, and I'm concerned a reinstall would lose the raid config... and subsequently the data on them. I should prolly learn to trust raid more than I do...)

Help gratefully received!

---

### Post by belialcouk on 2011-05-13
Ok so my problem was pretty similar to the thread above ([here]("http://ubuntuforums.org/showthread.php?t=1753698")) which has now been answered and solved (!). The solution was given in a post on the BT homehub forum. Seems there was a HH firmware update that has cocked things up for ubuntu users.
What you need to do is change your dhcp config so that you are sending your mac address as an identifier in your dhcp setup. follow the basic instructions given [here]("http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473/page/9") (Thank you "Irony") for a step by step guide.

---

