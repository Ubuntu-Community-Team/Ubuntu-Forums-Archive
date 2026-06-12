---
title: "Ethernet just stopped working suddenly"
date: 2010-08-12
forum: Networking &amp; Wireless
---

### Post by Bre Ntt on 2010-08-12
Version: Ubuntu 10.04
Relavant hardware: P5QL Pro built-in ethernet, cable modem with linksys wireless-G router (although problem is with ethernet connection, not wireless)

One minute my ethernet was working, and the next it stopped working. The only thing that I did between it working and not working was install electricsheep from Synaptic and then I shut down the computer. When I restarted a bit later, no ethernet connection shows up. 

I checked the cables, made sure they are in tight. 

My laptop connects using the same ethernet cable fine. So its not the cable or the router.

I reset the router and the computer at the same time. Still doesn't work. 


I don't know where to even start with troubleshooting this sort of problem. Everything to the extent of my computer knowledge seems to be working fine. Can anyone point me in the right direction?

Thanks for the help in advance.

---

### Post by Iowan on 2010-08-12
Is Network Manager icon visible?
Right-click it and verify networking is enabled.

Some other threads which might help:
[http://ubuntuforums.org/showthread.php?t=1505217]("http://ubuntuforums.org/showthread.php?t=1505217")
[http://ubuntuforums.org/showthread.php?t=1484913]("http://ubuntuforums.org/showthread.php?t=1484913")

---

### Post by Bre Ntt on 2010-08-13
Yea that was the problem, I noticed before that it said "network not enabled" but I was interpreting that as "not available" and didn't think it may have been disabled (I'm pretty sure I never disabled it). Everything is working good now. Thanks for the help.

---

### Post by Iowan on 2010-08-13
Some updates have reportedly disabled NM, and sleep/hibernate can (sometimes) cause problems. Glad you got it.(If you're sure it's fixed, use Thread Tools to mark the thread [SOLVED]. :)

---

