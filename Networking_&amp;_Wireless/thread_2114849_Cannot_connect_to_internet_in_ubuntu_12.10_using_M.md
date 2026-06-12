---
title: "Cannot connect to internet in ubuntu 12.10 using MTS"
date: 2013-02-11
forum: Networking &amp; Wireless
---

### Post by abhishek39 on 2013-02-11
I have recently installed Ubuntu 12.10(64 bit).
But was not able connect to internet using my MTS modem.
It detects My modem, but says 'not enabled' even after enabling mobile broadband.
But some times, very rarely (once in a day) the 'not enabled' changed to somthing like 'CDMA home network...evdo' and then i was able to connect.

I googled around and found that this is due to buggy 'modem manager 0.6.0.0' or so i removed it using software center and installed modem manager version 0.5.2.0) from a .deb package i have downloaded, using this code in terminal.

```

sudo dpkg -i modemmanager_0.5.2.0-0ubuntu2_amd64.deb
```

The problem has gone even worse. The bad part remained bad while the good part worsened. 
Now i can't connect to internet even when the 'CDMA home network...evdo' appears in place of 'not enabled'.

People found the solution working, every where around different forums.
What could have gone wrong with mine??

---

