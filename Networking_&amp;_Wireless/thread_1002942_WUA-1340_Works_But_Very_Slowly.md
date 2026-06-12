---
title: "WUA-1340 Works But Very Slowly"
date: 2008-12-05
forum: Networking &amp; Wireless
---

### Post by hiptahop on 2008-12-05
I recently completed a fresh Ubuntu install (8.04) on a desktop machine and am using this D-Link WUA-1340 USB wireless device to connect to the net.  I installed using NDISWrapper and the Windows driver and it works--I can connect, send/receive data, etc.

However, when data is actually being transferred--that is, whenever I'm loading web pages or transferring files or a background task is look for updates--my machine appears to overload.  The mouse skips, windows are unresponsive, etc.  This is true even whether several programs are running simultaneously, or just one.

A potentially related issue is that, immediately after rebooting, I can transfer files from another computer to this one at about 800KB per sec over wireless.  But that rate drops to about 80KB/sec and stays there a minute or two after rebooting and logging in to Ubuntu.

On a hunch the explanation is that my machine is just working REALLY hard on routing packets back and forth through NDISWrapper, I'll mention that this box is running a 2 point something Ghz Celeron, I have 2GB of memory, and I have a 512MB AGP video card (which is also running on a proprietary driver...).

Any ideas what the problem is?

---

### Post by hiptahop on 2008-12-07
Perhaps somebody could suggest what additional info I need to post to clarify my issue--to begin troubleshooting this problem...?

---

### Post by hiptahop on 2008-12-09
Wherefore art thou Wisdom of Crowds?

---

### Post by hiptahop on 2008-12-12
Has anybody else -- or anybody you know -- ever experienced a problem similar to mine?

It seems unusual to me, but I know only so much about troubleshooting hardware issues.  If it is the result of some odd quirk unique to my set up, then oh well.  There are many tolls on the road to Linux.

But, if there is a simple explanation and solution, damnit... I want to know!

---

### Post by hiptahop on 2008-12-15
Forget it.  I bought a new Linksys PCI wireless adapter.  Worked out of the box.

---

