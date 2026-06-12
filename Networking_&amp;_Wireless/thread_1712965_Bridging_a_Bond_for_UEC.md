---
title: "Bridging a Bond for UEC"
date: 2011-03-23
forum: Networking &amp; Wireless
---

### Post by keyz182 on 2011-03-23
Hi there, I'm setting up a UEC (attempting to anyway).

As part of the back end network, the plan was to have 4x1GBit connections bonded to appear as a 4GBit connection. I can do this fairly easily, and can communicate over the bonded connections.

The problem I'm having however, is that UEC needs it's connection to be part of a bridge, and Maverick just does not want to add a bond to a bridge.

I used [this page]("https://help.ubuntu.com/community/UbuntuBonding") to set up the bonding, and I've tried all of the suggestions in [this thread]("http://ubuntuforums.org/showthread.php?t=835732&page=2") to get it bridged, but no luck so far.

Any suggestions or ideas?

Thanks

/Kieran

BTW, I didn't include my /etc/network/interfaces because after trying all the various things, it was a non-working mess that didn't represent what I was trying to do at all.

Thhe connections I'm bonding will be eth2,3,4,5, though I'm testing with just eth4,5 the bond is bond0, and the bridge is br0.

---

