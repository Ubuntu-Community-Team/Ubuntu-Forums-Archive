---
title: "Slower internet connection speeds with Ubuntu"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by papachungo13 on 2008-12-14
Hi

Using 8.10 and I have observed much slower browser and download speeds than I do with Windows XP SP3.  Under windows my tested speeds are in the 12000 Kbps region, while under Ubuntu it is 1204 Kbps.  As a matter of fact, my upload speeds are actually measuring faster than that (it is consistently 2000+ under both OS's.

Aside from the OS, all other things remain equal, same PC, just a different partition, using firefox as the browser.  Optimum Online is the ISP.

Under windows there are TCP tweaks that can be performed, is there something similar that can be done with Ubuntu?

Thanks

---

### Post by Tilex on 2008-12-14
How do you connect to the Internet?
Wirelessly?
If it's the case, you might want to check the link quality with your AP by issuing the command "iwconfig" and looking at "link quality".
Hope it somehow helps!

---

### Post by papachungo13 on 2008-12-15
Darn!  I thought I had included the connection type - it is via ethernet cable, sorry.  Would the suggestion be applicable to a wired connection as well?
Thanks.

---

### Post by Tilex on 2008-12-15
No, the link quality in a wire is very good because of the "stabilized environment".
I don't know what could cause this...
You mention that you can tweak TCP in Windows, but in Linux I know that the TCP Windows is made larger and larger if the communication is good, so there's no need to tweak it...

---

