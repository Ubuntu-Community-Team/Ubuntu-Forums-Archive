---
title: "Can't print after installin updates"
date: 2011-06-04
forum: Networking &amp; Wireless
---

### Post by schworak on 2011-06-04
A couple days ago the update manager alerted me to a series of updates that were needed so I installed them. I didn't try printing anything until the next morning to find that both of my network printers were GONE!

I went to add them back and they installed just fine but any time I try to print I get "Not Conencted" errors. But if I navigate to the printers directly (they both have web interfaces) they are fully functional and print just fine (self test print samples).

Ubuntu 11.04 can see the printers when I search the network. I have tried CUPS and the Preferences/Printer/Add method and both add the printers just fine and let me do any type of configuration except I can't print. 

I am not sure what was updated that might cause this type of thing. What can I do? Any thoughts would be greatly appreciated.

Printers are both Brother network enabled printers and have worked 100% perfectly until the last update.

---

### Post by schworak on 2011-06-05
Well, I am not sure what the actual problem was, but I removed all of the printer drivers with apt-get and then reconnected the printers again and now they work. It took a full uninstall/reinstall of the printer drivers to get it going. Quite frustrating but fixed.

---

