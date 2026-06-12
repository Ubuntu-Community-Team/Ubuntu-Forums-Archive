---
title: "Hardy Heron - problem with network manager"
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by nexus_2006 on 2009-04-03
Every 3rd or 4th boot, the net manager that normally loads in the notification area beside the clock is not there.  Its the one that lists available wireless networks when you click on it, and then has the swirling blue dot that changen into 2 green dots and then blue signal strength bars when it connects.  What is the name of this program, so that I can load it up via the terminal when it doesn't load automatically.  When its not there, the network sometimes connects.  But sometimes it connects to the neighbor's slower network, and if I'm out it rarely connects to a usable network, very annoying weth I have to reboot 2 or 3 times, hoping it will come up?  What gives, and how can I work around?

---

### Post by chili555 on 2009-04-03
It's called *nm-applet*.

Is this, by chance, a desktop computer that never leaves home to go to the cybercafe or university to connect?

---

### Post by nexus_2006 on 2009-04-03
No, its a laptop that goes to the coffee shop and university on a weekly, if not daily basis.

nm-applet, I will def keep that in mind.  Any ideas why it randomly doesn't load sometimes?

---

### Post by leandromartinez98 on 2009-04-03
If you can, update to Intrepid. The newest network manager version that comes with it is much improved. I had several problems like those in Hardy and all worked fine and out of the box with Intrepid.

---

### Post by nexus_2006 on 2009-04-03
I don't think I'll make that same mistake twice, my friend.  I tried the live update to Intrepid about a month ago, it didn't work out all that well, had lots of stability issues.  I'll stick with Hardy for the time being, maybe until Jaunty is out for a while.  I might just hang onto Hardy though, I went straight from Dapper Drake to Hardy, never had any complaints with it for that long.

---

### Post by leandromartinez98 on 2009-04-03
Then I suggest trying Wicd as a network manager. You can install it using synaptic, and it will remove the current network manager you have. This has also solved a lot of problems of a lot of people were having. If it doesn't solve your problem, just reinstall the gnome network manager again (this will remove Wicd).

---

### Post by nexus_2006 on 2009-04-04
Hmmm, wicd doesn't seem to be in my repositories for some reason.

---

### Post by leandromartinez98 on 2009-04-04
> **nexus_2006 said:**
> Hmmm, wicd doesn't seem to be in my repositories for some reason.

You need to add the repository to your database. Here the
instructions are provided:

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by nexus_2006 on 2009-04-04
Ah, well, that would explain it, huh?  I thought the other post meant that it was in the repos by default.

---

