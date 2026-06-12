---
title: "Downloading cuts off my browser"
date: 2010-10-04
forum: Networking &amp; Wireless
---

### Post by LinuxNovice54 on 2010-10-04
As the title suggests, when I start to download large files and try to use firefox the "Server Not Found" error appears. I'm seriously new to Linux so I don't want to be discouraged on being a fan of Ubuntu Linux. Thank you for any help given.

---

### Post by Sergius14 on 2010-10-04
Could be many things.

What kind of downloads?

HTTP/FTP downloads (from a Website for ex.) or P2P downloads?

This issue can be expected with P2P, specially with unlimited upload speed.

If it is a P2P download, limiting the uploading should be a solution.


Regards,

---

### Post by LinuxNovice54 on 2010-10-05
Wait, when I download from the browser up to different computer. Normally it would slowdown the internet since its wireless with 256kb/s or it would say that the server timedout but instead of that it only says Server Not Found and its only on downloads from 30mbs or above and it doesn't necessarily has to be from my computer, like I've said before. 

p.s its from http, p2p, etc...

---

### Post by Sergius14 on 2010-10-05
Under a stress situation is expected to have high latency and packet loss.

Specially if your Internet is a Wireless, technology that usually is too much overbooked.

While you have the issue, try to ping [www.google.com](www.google.com) and see what happens.

Check if it being resolved to an address and if it yes, see the time (ms) that takes longs.

Server not found should be related to DNS stuff issue.

---

### Post by LinuxNovice54 on 2010-10-05
Actually it takes about ten minutes to tell me the server not found error message and in the status bar it only says Lookin [www.google.com](www.google.com)

When I tried to ping to my wireless router and modem it would do it with 64kb/s but ill see if i can ping google

---

### Post by LinuxNovice54 on 2010-10-06
Ok I have tried pinging google when it is downloading and it tells me 

ping: unknown host [www.google.com]("http://www.google.com")

---

### Post by Sergius14 on 2010-10-07
Have you tried with Windows?

I'm staring to believe that is something related with your broadband (low bandwidth, bad quality, overbooked, etc.) Very specially with Wireless.

---

### Post by LinuxNovice54 on 2010-10-08
Yep and it works perfectly in windows xp, vista and 7; no problems like with Ubuntu

If it helps I'm using Ubuntu 10.0.4

---

