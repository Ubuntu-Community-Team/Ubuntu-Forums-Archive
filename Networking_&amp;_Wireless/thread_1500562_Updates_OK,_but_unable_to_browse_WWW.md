---
title: "Updates OK, but unable to browse WWW"
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by six on 2010-06-03
I put the latest Ubuntu Netbook Remix 10.04 on my LG X110 yesterday. I then made sure it updated all the packages.

But when it had finished, I found that Firefox wouldn't display any pages. I tried searching the forums for something similar, but couldn't find anything that worked. It sounded like a DNS problem, although there was nothing wrong in the setup of my wired ADSL router. (The previous installation of XP had worked OK).

I thought I'd have another look at it today, and I've managed to resolve it. For anyone else having the same problem, here's what I did:

o. Right-click on the network icon in the top bar.
o. Select [Edit Connections]
o. Select the [Wired] tab on the Network Connections box
o. Left-click on [Auto eth0] then on the [Edit] button
o. Select 'IPv4 Settings' tab on the Editing Auto eth0 box
o. Change the Method to 'Automatic (DHCP) addresses only'
o. Left-click in the 'DNS Servers:' input box
o. Enter your two Domain Name Server addresses (that you should have got from your ISP), separated by a comma.
o. Click the [Apply] button, then close all windows.
o. It might lock up at this point (mine did), so reboot.

Firefox should now be able to use the WWW.

---

