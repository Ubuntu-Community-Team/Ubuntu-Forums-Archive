---
title: "wired network connection profile suddenly disappers"
date: 2010-07-28
forum: Networking &amp; Wireless
---

### Post by xihad76 on 2010-07-28
hi, i m using ubuntu jaunty jackalope.
today morning i installed team viewer linux version from deb package. after installing this one, every time i click on the software, it didn't start. so i thought that restarting the pc would solve the problem. after restart i suddenly noticed that my wired connection profile eth1 has been disappeared from network connection panel located at the upper right corner of the bar. then i made a new wired connection profile and tried again to connect to net. but it fails this time, though i used exactly the same settings that was working for me since before the last time i restarted my pc. so i again restarts my pc and this time the newly created wired connection profile is also gone from the network menu. 

just wondering what could be the issue. can anyone plz advice me what to do now to resolve my problem?

thnx in advance..

---

### Post by Iowan on 2010-07-28
Check */etc/network/interfaces* to see if the missing interfaces appear there. Bu default, interfaces defined there are not controlled by Network Manager (although that can be changed...).

---

