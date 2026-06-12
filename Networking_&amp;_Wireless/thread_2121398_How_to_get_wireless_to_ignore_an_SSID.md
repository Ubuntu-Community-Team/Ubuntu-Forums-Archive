---
title: "How to get wireless to ignore an SSID?"
date: 2013-03-01
forum: Networking &amp; Wireless
---

### Post by Rocket J Squirrel on 2013-03-01
We have two wireless SSIDs here: a "guest" one, and a "private" one. The "guest" SSID has throttled bandwidth, no access to attached network devices, etc., so it's not the one I want to connect to. But Network Manager likes to connect this Lubuntu laptop to the "guest" network whenever I bring it back into the building.

How can I tell NM to "forget" the "guest" SSID?

Thank you for your help.

---

### Post by pierceTN on 2013-03-01
Hey Rocket J Squirrel,

If you open the network maneger it should have the "forget network" button on the selected network.  look at the snapshot attached.



-Pierce

---

### Post by Rocket J Squirrel on 2013-03-01
Thank you, Pierce. The screenshot looks like it was made from Ubuntu. In Lubuntu I can't find a way to bring up "Forget this network."

---

### Post by pierceTN on 2013-03-01
Yes, sorry that is in Ubuntu.

In Lubuntu, you go to the wireless tab in the network manager, then simply delete the one you don't want it to automatically connect too. (I attached the lubuntu network manager pic)

---

### Post by Rocket J Squirrel on 2013-03-01
Thank you, PierceTN, that's very helpful. It works.

Followup question? Suppose I need to connect to that SSID sometime in the future -- how do I get NM in Lubuntu to do that?

---

### Post by pierceTN on 2013-03-01
Your computer will always "see" it when it is in range of your AP, but wont automatically connect. But, If you connect to it once it will store it in there so you don't have to select it every time. 



Cheers,

-Pierce

---

### Post by Rocket J Squirrel on 2013-03-01
Ah -- I see you are right. "Deleting" an SSID doesn't mean that NM doesn't show it and make it available. Thank you.

---

