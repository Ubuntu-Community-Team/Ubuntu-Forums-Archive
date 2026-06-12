---
title: "network-manager can't find my wireless network"
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by Eenvoud on 2009-12-26
Driver (= broadcom) works fine, recognizes other wireless networks. But not mine...the router (which I can't control, it's a shared connection) has WPA security. Tried reinstalling wpa-supplicant, tried using wicd, no dice.

The strange thing is that all of a sudden it used to work for a while...but then it didn't anymore. Unfortunately I never found out why. Maybe after an update or so - (un)installing some good/bad package?

I was using Jaunty, upgraded to Karmic yesterday but nothing changed.

Any help would be greatly appreciated...my wire is a bit short and I don't like going back to Windows...thx!

Johan

---

### Post by bender1234 on 2009-12-26
Hi.

This problem most likely occured if you upgraded from jaunty to karmic. Karmic is full of networking bugs. In the case of broadcom I think it is enough to blacklist and remove the old drivers. Go to broadcom's site, there is a driver to download with a short howto for solving the issue there. You will need the build essentials, and compile the driver for your system. Everything is explained in a howto.

Sadly I don't remember the url. I was setting up a dell box with a bcom card, but I had to give it back before I got wifi up and running. However it is really strange that you could see other networks. On this box I didn't get to see any other SSID's at all.

merry x-mas
bender

---

