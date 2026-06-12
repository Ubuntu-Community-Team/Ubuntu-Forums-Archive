---
title: "wireless working in Windows but not in Ubuntu"
date: 2010-11-01
forum: Networking &amp; Wireless
---

### Post by saurabhgeo on 2010-11-01
Hello 

I am not able to connect to wireless in Ubuntu but its working fine in Windows .
Could some one suggest any solutions?

Also if some one knows a good link for troubleshooting that would be appreciated very much 

Cheers

---

### Post by dsa42 on 2010-11-01
try running "sudo rfkill list" in a terminal window (applications->accessories->terminal) to see if you see "hard blocked: yes"   If so, it's the same problem the rest of us are having (see [http://ubuntuforums.org/showthread.php?t=1610928](http://ubuntuforums.org/showthread.php?t=1610928))

---

