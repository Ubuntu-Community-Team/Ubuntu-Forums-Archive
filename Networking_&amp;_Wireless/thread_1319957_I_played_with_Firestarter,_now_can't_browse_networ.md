---
title: "I played with Firestarter, now can't browse network"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by dixie460 on 2009-11-08
I searched and didn't come up with much on this...here's what I got. I have a Linksys WRT54GL router running Tomato, and 3 computers. My wife's Windows Vista pc is connected via ethernet to the router, my laptop and the kids pc connect over the wireless link. Earlier this morning, I installed Firestarter (on my laptop only) just to see what it could do. All I did was run the program, didn't change a thing with it. I realize that Firestarter is just a GUI for IPtables which is enabled by default in Ubuntu, and I haven't messed with that either. I put my computer in my router's DMZ and ran an online port scan from Gibson Research to check it out...behind the router all my ports showed stealth...not responding to anything. Behind IP tables they were all closed but still appeared on a port scan. Put my computer back behind my routers NAT firewall and all was well. Then, since I loved Ubuntu so much even though I've only used it for maybe a week, I decided to put it on my kids computer too... nuked Win XP and gave Karmic the entire drive. Now, it used to be (as of this morning) when I went to Places > Network > Windows Network, it would show me my Workgroup icon. I could click on that and access shared directories on either my wife's win vista pc, or my kids win XP pc no problem. After I installed Ubuntu on my kids pc, I needed a file from my laptop so I went into Places > Network and clicked on Windows Network. It comes up with a message that says "Unable to mount location. Failed to retrieve share list from server." Now, 2 questions here...if my kids pc is running Ubuntu, shouldn't it show up alongside the Windows Network...certainly it wouldnt be found under windows network, would it? Also, how come I can't access either one of the computers anymore? Did I screw something up by starting Firestarter? All 3 computers can access the internet just fine.

Thanks!!

---

