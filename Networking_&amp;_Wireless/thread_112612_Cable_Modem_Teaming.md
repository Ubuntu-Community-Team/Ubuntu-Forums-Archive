---
title: "Cable Modem Teaming"
date: 2006-01-04
forum: Networking &amp; Wireless
---

### Post by jaykup on 2006-01-04
Is it possible to team two cable modems to one PC to get double the bandwidth in Ubuntu?

---

### Post by amblin on 2006-01-04
They would have to be two different lines for one thing, and the bandwidth is capped at whatever the service provider sets it too(mine is comcast its 4mps).  Unless anyone knows better than me Im going to say no you can't double your bandwidth with dual cable modems.

---

### Post by mips on 2006-01-05
Should be possible, something like ppp multilink maybe...

---

### Post by cwaldbieser on 2006-01-05
[QUOTE=mips]Should be possible, something like ppp multilink maybe...[/QUOTE]
I found this article-- I am not absolutely sure, but it seems like it would do the trick.
[http://lartc.org/howto/lartc.rpdb.multiple-links.html]("http://lartc.org/howto/lartc.rpdb.multiple-links.html")

---

### Post by jaykup on 2006-01-06
[QUOTE=cwaldbieser]I found this article-- I am not absolutely sure, but it seems like it would do the trick. [http://lartc.org/howto/lartc.rpdb.multiple-links.html]("http://lartc.org/howto/lartc.rpdb.multiple-links.html")[/QUOTE] This looks promising, I will give it a shot and let you know.

[QUOTE=amblin]They would have to be two different lines for one thing, and the bandwidth is capped at whatever the service provider sets it too(mine is comcast its 4mps). Unless anyone knows better than me Im going to say no you can't double your bandwidth with dual cable modems.[/QUOTE]

Back in my windows days I tried some software by midpoint and it would let you team the modems for downloading files only, and I was able to get some pretty nice speeds.  The physical limit of a cable line is 10mb/s or 8mb/s depending on who you talk to (the old BNC networks were 10) and capped speeds are configured inside your modem through configuration files your modem downloads from the ISP's TFTP server.  So if you were able to get 2 modems the speed should be limited at 10mb (depending on the cable line quality and if you've got at least 5mb per modem).

---

