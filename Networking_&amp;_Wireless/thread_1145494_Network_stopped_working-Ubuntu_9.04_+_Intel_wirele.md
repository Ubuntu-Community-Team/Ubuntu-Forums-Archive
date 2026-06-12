---
title: "Network stopped working-Ubuntu 9.04 + Intel wireless 3945."
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by phiabell on 2009-05-01
Hey, my boyfriend recently installed Ubuntu 9.04 on an external hard drive. Everything worked fine first time including wireless but then after a few days of joy, the network spontaneously disconnected while using firefox.
Tried to re-connect, it gets to two green dots and then does not go any further.
Things we know so far - rebooting does not help - re-entering network info doesn't work - not a hardware issue as 8.04 on another partition works fine - he hasn't knocked the wireless switch to off on his computer cos he doesn't have one.

Has anyone had a similar problem? It's particularly confusing as it was working fine and the problem seemed to come from nowhere.

His computer is Gateway 8716b and the wireless is Intel PRO/Wireless 3945


Also, we are both new to Linux! Have been getting on ok so far, but have a lot to learn so forgive me if I don't understand anything straight away...

---

### Post by pi3832 on 2009-05-01
Will it connect to an unsecured network?

If so, it sounds like [my problem]("http://ubuntuforums.org/showthread.php?t=1144561").

---

### Post by phiabell on 2009-05-01
Well we couldn't but after another reboot or two it's randomly working again.. :s

---

### Post by gnusci on 2009-05-01
Well, I had some weird behaviour like you mentioned after I did upgrade to 9.04 but then I upgraded the BIOS and now everything is working very well again... Just check what kind of messages give you the command:

**$ dmesg**

---

### Post by mwolfe on 2009-05-03
I just installed ubuntu 9.04 on my laptop (gateway M6824 which has an intel 3945 wireless card in it). Its only about a 1 1/2 years old. Anyways, I also just got a new trendnet wireless n router (we just moved).  It will connect just fine but then it disconnects shortly afterwards. Its not even enough time to download 50mb on a 12Mb/s line.   It will start a download and then about a minute later or less its as though the connection drops and my downloads stop, although my wireless meter reads 4 bars and says its still connected. The router on the otherhand does not need to be reset. I've checked by restarting my laptop and it will reconnect and work again for a few minutes. I've also had moderate success with just restarting my neworking in linux. 
I now have windows vista running on it and i just completed 160mb of updates for windows and a few more for my antivirus (its been a really long time since I used windows).  I've also been downloading other stuff at the same time and it seems fine.
 I'm typing this from my other laptop (work laptop - dell with high end intel 5300 wireless card, and its running in windows xp without a hitch)
It seems like this is definitely an issue with the driver for the 3945. Hopefully this gets worked out. I am glad that its not my routers fault. I'm just curious now if I would have problems with my older router.. It isn't here so I can't test it though. Curious to see if others are getting this problem or similar and hopefully an update will be released

---

