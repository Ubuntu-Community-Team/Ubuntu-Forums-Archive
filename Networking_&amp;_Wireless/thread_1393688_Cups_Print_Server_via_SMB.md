---
title: "Cups Print Server via SMB"
date: 2010-01-29
forum: Networking &amp; Wireless
---

### Post by HoboSteaux on 2010-01-29
I am trying to set up a shared network printer using cups-pdf and encountering many problems. I have gone through about 6 guides now, the latest being [this one]("http://www.faqs.org/docs/Linux-mini/Debian-and-Windows-Shared-Printing.html"), taken with a grain of salt. I can print locally, but I can not print to if from windows computers over the network. This is the error i get:
```
D [29/Jan/2010:13:17:20 -0800] cupsdReadClient: 12 WAITING Closing on EOF
D [29/Jan/2010:13:17:20 -0800] cupsdCloseClient: 12
D [29/Jan/2010:13:17:21 -0800] cupsdAcceptClient: 12 from localhost (Domain)
D [29/Jan/2010:13:17:21 -0800] cupsdReadClient: 12 WAITING Closing on EOF
D [29/Jan/2010:13:17:21 -0800] cupsdCloseClient: 12
D [29/Jan/2010:13:17:21 -0800] cupsdAcceptClient: 12 from localhost (Domain)
D [29/Jan/2010:13:17:21 -0800] cupsdReadClient: 12 WAITING Closing on EOF
D [29/Jan/2010:13:17:21 -0800] cupsdCloseClient: 12
D [29/Jan/2010:13:17:21 -0800] cupsdAcceptClient: 12 from localhost (Domain)
D [29/Jan/2010:13:17:21 -0800] cupsdReadClient: 12 WAITING Closing on EOF
D [29/Jan/2010:13:17:21 -0800] cupsdCloseClient: 12

```This will continue to loop. Any suggestions?

A note: I do not have internet at home so my replies may be sporadic

---

### Post by HoboSteaux on 2010-02-01
Anyone?  I'm pretty sure it has to to with the network user changing files on my computer, but I'm not sure.

---

