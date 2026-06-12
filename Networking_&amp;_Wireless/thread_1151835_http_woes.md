---
title: "http woes"
date: 2009-05-07
forum: Networking &amp; Wireless
---

### Post by ryw on 2009-05-07
Hi -- I'm having a problem with http download working from my ubuntu virtual server (a slice from slicehost.com) -- it works from my mac, then fails in production.

Ubuntu 8.04.2
Linux kernel: 2.6.24-19-xen #1 SMP Sat Jul 12 00:15:59 UTC 2008 x86_64 GNU/Linux

This is the first time in a long time that the internet didn't just "work" :)

wget [http://www.qsisw.com/centacs/rf/Reports/WB5P4.0_Powers_Austin_20090506223208.pdf](http://www.qsisw.com/centacs/rf/Reports/WB5P4.0_Powers_Austin_20090506223208.pdf) consistently hangs at 4% 15,928 of 395,442 bytes downloaded.

wget [http://www.adobe.com/devnet/livecycle/articles/lc_pdf_overview_format.pdf](http://www.adobe.com/devnet/livecycle/articles/lc_pdf_overview_format.pdf) (a 361,018 byte PDF) works fine.
  
I'm thinking there must be something unusual about [qsisw.com]("http://qsisw.com/")'s networking environment, since I can get it to fail on a number of linux machines. It must be something unusual about their .NET environment, as this doesn't seem to be a common or widespread issue.

I am pulling my hair out on this one now. AAAAARRRRGGGGHHHHH!!!! :(

Additional tests:

Distribution              Kernel version            status
----------------------------
Ubuntu 8.10 (intrepid)    2.6.27-11-generic          fail
Debian 4.0 (etch)         2.6.24.4-grsec                  fail
Debian 4.0 (etch)         2.6.21.3-grsec                     fail
Debian 4.0 (etch)         2.6.18-5-686                        fail
Debian 4.0 (etch)         2.6.18-6-xen-686 (domU)     PASS
Debian 4.0 (etch)         2.4.35.3                           PASS
OpenWRT 7.09 (kamikaze)   2.4.34                      PASS



-Ryan

---

### Post by jerrrys on 2009-05-07
i went to Qualitech Solutions to see whats up...couldnt even get the site to load on 804...

---

