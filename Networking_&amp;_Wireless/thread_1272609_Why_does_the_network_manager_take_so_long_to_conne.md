---
title: "Why does the network manager take so long to connect after coming back from suspend?"
date: 2009-09-22
forum: Networking &amp; Wireless
---

### Post by Felliph3 on 2009-09-22
I have noticed that the Network manager in GNOME is very slow at getting a connection. It seems to connect fairly quickly once it starts trying but it takes about 30 seconds for it to start connecting. 

When you turn on the computer wifi is the last thing to connect, when you come back from a resume, it takes a minute to be connected. Where as on a mac or windows its less than 10 seconds, very fast.

I feel the problem is that the network manager doesn't know that it needs to connect for a long time.

 I was using the WICD network manager and it connects as fast as the gnome network manager but it doesnt wait to connect, it tries to connect as soon you boot, etc. It was a bit buggy so I let it go.


Is there a fix to get the Gnome network manager to connect faster? I know Im not the only one that is bugged by this!

---

### Post by Felliph3 on 2009-09-25
Bump!!

---

### Post by Felliph3 on 2009-09-25
Found a fix to have it scan after suspend, helps a lot but it could be better. Wait from 60s is now down to 30s?

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274405/comments/37](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274405/comments/37)

---

### Post by TVAbuntu on 2009-10-05
That bug has been open over a year! I'm hoping this is fixed in Karmic, though it may from upstream. 
WICD isn't much better for me.

---

### Post by Felliph3 on 2011-01-03
Yeah still not fixed in Maverick =/

---

### Post by kostkon on 2011-01-03
In my case, NM works just fine in maverick; it takes NM less than 10 secs to start trying to reconnect after suspend.

---

### Post by 3602 on 2011-01-03
Same here. Although NM flash-connects upon boot/reboot, it just about can't connect after a Suspend.

---

