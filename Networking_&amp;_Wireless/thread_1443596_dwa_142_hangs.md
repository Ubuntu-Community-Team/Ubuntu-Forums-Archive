---
title: "dwa 142 hangs?"
date: 2010-03-31
forum: Networking &amp; Wireless
---

### Post by audience of one on 2010-03-31
so I found the right drivers, its one of the marvel netmw245 ones.
got them copied over,
the system sees the wireless puck, although it doesn't see it every reboot (any thoughts on that?)
```
ndiswrapper -l shows the device
netmw245 : driver installed
       device(07D1:3B10) Present 
```
When I run sudo modprobe ndiswrapper, it sees the wireless card in the gui, I put in my wep code, it says it is configuring, and then it hangs.  If I try to do anything in the cli it just sits there and does nothing.

What else can I provide that will help someone help me?

---

### Post by audience of one on 2010-03-31
Decided to drag a wire from router to the desktop on second floor.  Running an update now.  Will give a status update when this is done.

---

### Post by audience of one on 2010-04-01
I applied all patches, and get the same thing, it says connecting and never goes further.  Anyone have any thoughts on what I can try?

---

