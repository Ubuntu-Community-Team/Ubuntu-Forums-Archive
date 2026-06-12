---
title: "Annoying internet problem"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by tom56 on 2006-06-03
The internet keeps disconnecting after being inactive for a short time, and after a reboot. I've found I can get it going again by going to System->Administration->Networking, selecting the ethernet card and pressing "Deactivate" then "Activate". I think the problem is that my settings are not being stored. Compare the two screenshots. The first is when it is working, the second is after a reboot. Note the difference under "Default gateway device". Any ideas? Has anyone encountered the same - or similar - problem, and did you manage to fix it?

---

### Post by daveg2 on 2006-06-03
I had a problem with RC 7 that looked the same.  Lsmod showed that both the tulip driver and the dmfe driver were loading.  I was unable to ping the router with both loaded.  I renamed tulip and blacklisted it.

---

### Post by daveg2 on 2006-06-03
Here's a link to another thread that does a good job of explaining how to resolved the problem. [http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

---

### Post by tom56 on 2006-06-03
[QUOTE=daveg2]I had a problem with RC 7 that looked the same.  Lsmod showed that both the tulip driver and the dmfe driver were loading.  I was unable to ping the router with both loaded.  I renamed tulip and blacklisted it.[/QUOTE]

Hmmm... My lsmod doesn't show either of those modules so I don't think that's it :(
Thanks anyway though.

---

### Post by tom56 on 2006-06-04
Found a couple of other people with the same problem in [http://www.ubuntuforums.org/showthread.php?t=187880](http://www.ubuntuforums.org/showthread.php?t=187880)

---

### Post by kieranjones on 2006-06-04
Hi,

I had the same problems as everyone else and did these steps described to disable tulip etc, but it didn't work.

I found out the problem though, it seems that Network Manager was preventing it from working as well. So if you're finding that it's still not working, make sure that you've not accidentally installed Network Manager like I had.

---

### Post by tom56 on 2006-06-04
Nope, don't have Network Manager. Thanks anyway.

---

