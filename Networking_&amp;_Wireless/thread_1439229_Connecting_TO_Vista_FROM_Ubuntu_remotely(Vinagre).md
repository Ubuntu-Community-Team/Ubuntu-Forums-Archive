---
title: "Connecting TO Vista FROM Ubuntu remotely(Vinagre)"
date: 2010-03-25
forum: Networking &amp; Wireless
---

### Post by n2o-Gr55 on 2010-03-25
Hi, i have been struggling with setting up a VNC connection between my Ubuntu laptop and my Vista desktop. I am trying to remotely access the Vista desktop using my Ubuntu laptop. I have forwarded port 5900 to my Vista desktop, and attempted connecting to (VistaLocalAddress):5900 using Vinagre. Sadly enough, it instantly returns "Connection Closed."

I have tried setting up some sort of remote access in a similar manner about 3 times in the past, finally i just made a forum account and created this thread in a plea for help. Any help with my problem would be greatly appreciated.

PS: I forgot to mention that the Vista desktop has allow remote connections ENABLED.

Thanks,
n2o-Gr55

---

### Post by spyrule on 2010-03-25
I use TightVNC to connect between my Windows and Linux computers. All you have to do is install TightVNC desktop on your Ubuntu machine, and TightVNC server on you Windows machine and you should be able to connect without a problem.

You can get TightVNC (for free) from:

[http://www.tightvnc.com/download.php](http://www.tightvnc.com/download.php)

---

### Post by spyrule on 2010-03-25
You can, though, just install TightVNC Server onto the Windows machine and make sure the port to connect through is 5900... It works fine too. I just tried it.

---

### Post by n2o-Gr55 on 2010-03-26
Connecting to Vista successful after installation of TightVNC. Thank you greatly.

n2o-Althalus

---

