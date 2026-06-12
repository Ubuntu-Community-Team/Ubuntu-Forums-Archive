---
title: "Wireless was working, then I got a new router"
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by deleyd on 2009-01-25
I'm good with computers but a novice at Linux.

HP Pavilion Laptop dv9410us. Some months ago I got the wireless working by blindly following some steps I found somewhere (possibly here, or a link from here).

Tried it again recently and it's not working. Only thing different I can think of is I replaced the wireless router. But new router has same password, and if I boot windows Vista the wireless works fine.

Tried following the steps I found here:

Broadcom Wireless Setup for Hardy (Step by step)
[http://ubuntuforums.org/showthread.php?t=766560&highlight=setup+wireless](http://ubuntuforums.org/showthread.php?t=766560&highlight=setup+wireless)   

didn't work. Hmm... what do I look at next?

---

### Post by Sam Lars on 2009-01-25
Are you using security on the router?  If so, did it change from WEP to WPA or something?

---

### Post by deleyd on 2009-02-06
I found a nice troubleshooting guide here:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Ubuntu Documentation > Community Documentation > WifiDocsWirelessTroubleShootingGuide 

which found the problem rather quickly.

[For me, there was no ip assignment. Ran "sudo dhclient wlan0" and it's all happy again.]

---

