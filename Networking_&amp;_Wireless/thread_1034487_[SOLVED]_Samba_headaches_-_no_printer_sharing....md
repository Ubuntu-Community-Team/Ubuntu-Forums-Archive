---
title: "[SOLVED] Samba headaches - no printer sharing..."
date: 2009-01-08
forum: Networking &amp; Wireless
---

### Post by akelsall on 2009-01-08
Been trying various things with no luck. I have a Linux host and a virtualized XP box running in VirtualBox (I'm doing this to figure things out, then I'll roll it out to my wife's XP box).

I'm getting closer. Now, when I log into my XP box and go into "My network places" then "view workgropu computers", I see my Linux box there, but I can't access it. When I click on it, an error message pops up that says "\\eno is not accessible. You might not have permissions to use this network resource." I'm guessing that until I can get this issue resolved, there's not much sense even trying to map a network printer from the XP box.

Any ideas? Attached is my smb.conf file.


Thanks,

Andy

---

### Post by dmizer on 2009-01-08
I've never been successful in getting samba to share a printer over the network. Fortunately, CUPS works just fine.

Have a look here: [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu) the directions are for 7.10, but they should work for any distribution (nothing has changed that I am aware of).

---

### Post by akelsall on 2009-01-09
thanks for the info dmizer, but unfortunately, the same problem exists. Since I don't have a need for file sharing right now, I'm closing this thread and opening a new one related to CUPS.

Andy

---

