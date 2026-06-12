---
title: "Internet Issue in Dualboot"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by mr_skipper on 2009-02-07
I'm using XP SP2 dualboot with Intrepid Ibex. I can go online w/ my ubuntu but not on XP. Before I upgrade to Intrepid I had Hardy installed boot OS can go online. Is there any settings on my Intrepid that is blocking my XP not to access the internet? Please help.

---

### Post by ForMar on 2009-02-08
There is not way that ubuntu could actively be effecting your internet connection while it is not running. Thus there are two possible problems. 
1. you have done something to windows at some point by accident that has nothing to do with ubuntu
2. you some how corrupted some files while updating ubuntu on your windows partition.

Either way you need to reinstall the drivers in windows and if that does not work then possible reinstall windows.

I would also (for good measure) copy all the network info (such as ip, gateway, ect.) from linux and make it exactly the same on windows. 
             You can get this info by typing "ifconfig" in terminal

---

### Post by mr_skipper on 2009-02-08
Everthing is fresh installed. I installed XP 1st after that I install Interpid. I've already tried setting static IP on my windows but still the computer did not recognized the connection. Its a weird case but I'll try to reload hardy and see what happens. :)

---

