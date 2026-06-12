---
title: "Why is the rt3562sta driver so unstable?"
date: 2011-12-14
forum: Networking &amp; Wireless
---

### Post by bobman321123 on 2011-12-14
I'm running Ubuntu on my computer (I can give you system specs if desired), and my wireless card required the ralink driver "rt3562sta" to work. Why is that driver so unstable? I can barely use linux because of how frequently the network will go unresponsive or cut out completely. This is driving me crazy!

---

### Post by ratcheer on 2011-12-14
That driver is working perfectly for me.

What version are you using? Mine is v 4.1.1 dated 17-Dec-10. I have seen others trying to use much older versions.

Also, did you setup the makefile for the wpa_supplicant options?

Tim

---

### Post by bobman321123 on 2011-12-15
I did indeed change the WPA supplicant options in the make file. 
I think the version I have is 5.1.something. (I think, I'm checking now)
Ok wait, the version I have is V2.4.1.1
I know it's not JUST the card's fault because I run windows on the same system and windows works fine about 90% of the time, whereas linux works reliably about 50% of the time. 

p.s. even as I write this, my wireless rate is hoving at about 2kb per second, then jumping up to 70-ish for about 2 seconds, and going back down to 2 again for another 3 minutes before giving me another burst of activity. -.-

---

