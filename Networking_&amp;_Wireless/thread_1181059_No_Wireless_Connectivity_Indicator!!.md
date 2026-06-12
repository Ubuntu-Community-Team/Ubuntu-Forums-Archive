---
title: "No Wireless Connectivity Indicator!!"
date: 2009-06-07
forum: Networking &amp; Wireless
---

### Post by yosef on 2009-06-07
Suddenly network manager is no longer showing me wireless networks with the applet in the corner! I don't know what could have caused this.  I can still connect to a wireless network (this is how I am now posting this request for help) but it does not show that I am connected nor is there any indication that the applet recognizes my wireless card.  As I said, I can connect but I would like to be able to see it.  Any suggestions?

---

### Post by cariboo on 2009-06-07
Open an Applications-->Accessories-->Terminal and type:

```
nm-applet
```

To see if that changes anything.

---

### Post by yosef on 2009-06-07
It doesn't.  I do still have the applet up in the corner, it just doesn't recognize wireless networks.  I have wireless connection checked in network settings and I am in fact connected to a wireless network, but the applet doesn't understand.

---

### Post by blairbo on 2009-06-08
me too.  nm-applet brings it back up, but only as long as I'm running it in the shell.  It must have been updated and not added back to the startup services.. 

I'm running:
Jaunty Netbook Remix 9.04
Acer Aspire One 110 ZG5

---

### Post by yosef on 2009-06-09
Ok!  Fixed it! This helped me a lot, hope it helps others as well.
[http://forum.lowpowertech.com/viewtopic.php?f=6&t=9&sid=5114ff743a9d246f470bc77275bf919c](http://forum.lowpowertech.com/viewtopic.php?f=6&t=9&sid=5114ff743a9d246f470bc77275bf919c)

---

