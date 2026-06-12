---
title: "how to add a second ethernet card and get it recognized?"
date: 2006-04-30
forum: Networking &amp; Wireless
---

### Post by gurdy on 2006-04-30
I'm running Breezy on an Athlon-based system and have networking running fine with DHCP on eth0. I added a second (wired not wireless) ethernet card, but when I run network-admin, eth1 doesn't show up and there is no "Add" button in the Connections section. 

If I run this:
sudo mii-tool eth1
I get this:
SIOCGMIIPHY on 'eth1' failed: No such device

How can I get Ubuntu to recognize the second card?

The second card was running fine in another computer. On that computer I had Hoary running with two ethernet cards -- eth0 was using DHCP, and eth1 had a static IP address and was connecting to my home network thanks to Guidedog. On that computer I think eth1 was working fine because the second ethernet card was there when I initially installed Hoary. I'd rather not have to completely reinstall Breezy on the new computer to get eth1 to be recognized.

Is there a way I can use GUI-based tools to get Breezy to recognize the second card? If not, what command-line-based operations do I perform to fix the problem? 

If I need to do a bunch of command-line-based stuff, that's fine, but if GUI tools will work just as well I'd rather do that.

Thanks!

---

### Post by gurdy on 2006-05-02
I got it to work!

I opened up the computer and took out the second NIC to find out what model it was, and noticed that there was a big thick wad of dust covering part of the NIC's connectors. I cleaned it off and put the NIC back in the computer. When I rebooted and ran network-admin, it listed eth1 in the Connections section! I was then able to configure it.

I guess I wasn't paying attention to the extreme nature of the dust situation when I first put the card in. Oops.

---

