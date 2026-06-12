---
title: "Wired network won't connect"
date: 2010-06-21
forum: Networking &amp; Wireless
---

### Post by mr.scissorkick on 2010-06-21
So, I'm brand new at this Ubuntu thing.  I had trouble for a while with my wireless card, but now my ethernet connection won't hook up.  I'm using the same wire right now on my wife's laptop and it is running like a dream. However, my laptop is way cooler and I am still bragging to everybody about my escape from Vista--I can't go back now.  I have used the wired network before on this computer, with this OS, and I don't think I could have broken anything (famous last words, right?) since I last used it.
So what are some suggested troubleshooting strategies?

I am using Ubuntu Lucid 10.04

---

### Post by garvinrick4 on 2010-06-21
Right click on network applet and make sure it is enabled.

---

### Post by mr.scissorkick on 2010-06-21
The box is checked.
When I go into "Edit Connections," It has Auto eth0 listed as a wired network.
When I plug in, it shows that little swirly animation for about a minute, then tells me I've been disconnected.

---

### Post by mr.scissorkick on 2010-06-21
Bueller... Bueller...

---

### Post by Iowan on 2010-06-21
Check [post #3 ]("http://ubuntuforums.org/showthread.php?t=1505217"). Dunno if you may need **sudo** if front of any of those lines.  If that doesn't work, check results of **sudo dhclient eth0**

---

### Post by mr.scissorkick on 2010-06-23
Thanks Iowan, that was what I needed.  Now on to start another thread :-|
:p

---

