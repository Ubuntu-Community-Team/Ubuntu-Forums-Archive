---
title: "Cannot connect to winSSHD server via port 443"
date: 2011-07-09
forum: Networking &amp; Wireless
---

### Post by boosted on 2011-07-09
I originally setup WinSSHD on my Windows7 desktop with it listening on port 22.  It worked fine when using Ubuntu 11.04 and putty on my laptop from various locations.  However, when I was at my college class and tried to connect it failed.  They block port 22.  So, I figured out that port 443 is open, so I went home and had WinSSHD listen on port 443.  I made sure 443 was forwarded on my DD-WRT router.  When I try to connect using my Ubuntu laptop and putty I just get: Server unexpectedly closed network connection.  This happens even if I try from home and use the local 192.168.1.48 IP for the server address.  I'm not sure what I'm missing here.  If I change the listening port back to 22, it connects just fine.  But I need it to connect on 443.  Any help would be appreciated.

---

### Post by boosted on 2011-07-11
I figured it out.  Hough it may just be a work around.  I port forwarded 443 to 22 and kept WinSSHD listening on 22, so now it works...if anyone cares.

---

