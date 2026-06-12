---
title: "How to see the *number* of packets sent through the wireless connection?"
date: 2009-10-07
forum: Networking &amp; Wireless
---

### Post by orngjce223 on 2009-10-07
Hi,

I'm a recent Ubuntu switcher (cue cries of "Welcome Aboard!") with a modicum of technical knowledge.  I'm not exactly a power user of either Ubuntu or Windows, but I do know just enough to know what's happening and where, so I can Google for a fix, and report the trouble if it's not known enough :D

But to the topic: is there a way to see the number of packets that the wireless is sending out?  I already have a System Monitor sitting in my (GNOME) upper bar that shows me network use (and it's invaluable for seeing if Firefox has leaked too much memory again xD), but sometimes I just need to see whether the router's working *at all* or not.  On Windows I accomplished this by opening up the network connection properties dialog box, which showed you how many packets that the network sent to you and that you sent to the network.  As a number (the system monitor just doesn't have enough vertical resolution).  Where would I find this?

Thanks!

---

### Post by sedawk on 2009-10-07
```

netstat -i

```

This should to the trick (I'm not sure currently if 
you have to add "sudo" in front to have the access
rights to read the counters - so you might have to
try "sudo netstat -i".).

I think you can also use "conky".

---

### Post by orngjce223 on 2009-10-07
Cool, I'll try that.

---

