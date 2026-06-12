---
title: "RTL8110SC running at 100 mb"
date: 2010-05-31
forum: Networking &amp; Wireless
---

### Post by zyberwoof on 2010-05-31
I have a Biostar TP35D2-A7 motherboard with an onboard Realtek 8110SC NIC.  After upgrading to Ubuntu 10.04, I noticed that netperf was reporting that I was only getting ~94 mbps speed over my LAN.  After testing my cables and switches, I narrowed it down to my Ubuntu box itself.

**I solved this by upgrading the driver to the newest one from the Realtek site.**  The driver is version 6.013.00 and was added to the site 2010-05-04.  I grabbed the driver from the site, untared it, and followed the included README file.

It seems like everything is working fine now.  **Can someone tell me, does this need to be reported as a bug anywhere?**  If not, I'll just mark this post as Solved.


Also, the newest driver can be grabbed from [Realtek's site]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true").

---

