---
title: "basic internet connection w/ router"
date: 2009-12-19
forum: Networking &amp; Wireless
---

### Post by tremblayster on 2009-12-19
Hi,

I am also a newbie with the exact same problem as [this old thread]("http://ubuntuforums.org/showthread.php?p=8207311&highlight=connect#post8207311"), but I see this post has had no replies/resolutions. I hope someone has some time and patience to walk me through a solution.

To summarize : 

+ Running Ubuntu 9.10
+ Used to be connected directly to a modem -- successfully connected using the pon command
+ I now have a new wired/wireless router and wish to connect my computer _with wire_ to the router

At this point, the computer cannot even ping the router's default address (192.168.0.1). Even though the router is on and working properly as wifi router for my other computer (which I am now using to type this)

Any help would be greatly appreciated!

Thank you!

---

### Post by Iowan on 2009-12-20
Wise decision to start your own thread - tacking it on the end of someone else's thread is one way to get no replies.

What is in */etc/network/interfaces*? If there is more than just the two lines defining "lo", you might try commenting out the extra lines.  Details on getting that done available on request...
(Don't forget to restart/reboot after making the changes)

---

