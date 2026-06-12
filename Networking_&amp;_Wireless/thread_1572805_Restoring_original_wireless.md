---
title: "Restoring original wireless"
date: 2010-09-11
forum: Networking &amp; Wireless
---

### Post by rektruax on 2010-09-11
Here's one I've yet to run across...

In an attempt to better my wireless signal, I decided to abandon the "out of the box" wireless set-up in favor of ndiswrapper and the windows drivers that came with my wmp54g card. Lo and behold, my signal didn't get better, but dropped another 15-20 percent. I'm lucky to see a connection of 55 now, compared to the 70-77 percent I got with the Ubuntu drivers. I thought... No problem. I'll just un-install the Windows driver. Upon doing so though there's no wireless option at all. Where did the old set-up go? Is there a way to get it back?

Any help would be appreciated.

---

### Post by MaindotC on 2010-09-11
What do you mean when you say "there's no wireless option anymore"?  Do you mean NetworkManager doesn't allow you to select a wireless network?  Please consult the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).  You should be able to remove ndiswrapper with Synaptic selecting "complete removal" and then use the commands listed in the guide to insert the right driver for your wireless card.

---

