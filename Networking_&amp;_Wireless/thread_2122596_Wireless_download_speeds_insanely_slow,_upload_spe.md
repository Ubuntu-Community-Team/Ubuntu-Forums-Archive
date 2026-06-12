---
title: "Wireless download speeds insanely slow, upload speeds twice as fast"
date: 2013-03-05
forum: Networking &amp; Wireless
---

### Post by HolyMythos on 2013-03-05
OS: Ubuntu 12.10
Wireless Card: ASUS PCE-N10 Wireless-N ([https://www.asus.com/Networking/PCEN10/](https://www.asus.com/Networking/PCEN10/))
Router: Belkin f5d7234-4 v4
Provider: WOW! (2Mbps d/u)

Hey guys. I'm having a problem with download speeds on my computer. I got my wireless card about nine months ago and the highest it's run at was 150kbs. I've seen it hit 200kbs for split seconds but that's about it. It hasn't really been a problem since I just assumed it was my crappy cheap internet. However recently I've noticed it getting so slow that certain websites won't load if Facebook is open just because Facebook constantly eats internet. I knew my connection was bad but not that bad. Connected to the Wifi on my phone (Droid RAZR Maxx HD) I tried the Speedtest.net App and I got a download and upload speed of about 2.0mbs respectively. Trying it again on my computer I got 0.53mbs for my download and 1.07mbs for my upload (however, whenever downloaing something that isn't this test it's merely fractions of that).

Could the problem be my wireless card? I've had plenty of phones, other computers and gaming systems connected to the network without a problem, just this computer. The computer is rooms away from the router/modem so I can't do a wired connection. I can honestly say I'm not Linux savvy at all so I have no idea if there are drivers needed to be updated or not. It came with a CD however I cannot get it to work with my computer. If all else fails I was going to get the PCE-N15 to see if maybe perhaps it was just my wireless card and not it's relation to Linux.

Any help is greatly appreciated!

---

### Post by praseodym on 2013-03-05
Please show the outputs of:
```

lspci -nnk | grep -iA2 net
lsmod
iwconfig
sudo iwlist scan
```

---

### Post by HolyMythos on 2013-03-08
On a hunch I tried opening the disk through wine and installing the drivers that way. Thought it wouldn't do a thing but for some reason it did help. I'm not working at 2mbs download and 1mbs upload, which is what I'm provided with. So, I think problem solved?

---

