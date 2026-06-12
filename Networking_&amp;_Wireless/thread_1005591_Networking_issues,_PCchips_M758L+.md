---
title: "Networking issues, PCchips M758L+"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by lerrow on 2008-12-08
I've a quite old computer. Mother is a PcChips M758L+, and the Processor it's a Via C3 600MHz, with 512 MB RAM (64MB shared with video)
 This mother comes with an on-board sis 900 ethernet board, and at least in my case, it comes with no physical adress (well, the assigned it's 00:00:00:00:00:00).
 So my problem it's basically that the mother doesn't know where the ethernet is located. I'd the same problem on windows.
 To solve this issue, it's really simple, you just need to open temrinal and type this:

```

 sudo ifconfig eth0 down 
 // This is only in case eth0 it's up
 sudo ifconfig eth0 hw ether 00:00:00:00:00:01
 sudo ifocnfig eth0 up

```
 
 this is how I sovled the issue running the Ubuntu 8.10 Live CD, and it worked perfectly. 
 Hope this is usefull for others running my same problem.

Regards

LeRRoW

---

