---
title: "Broadcom 4306 ndis vs built-in"
date: 2006-07-07
forum: Networking &amp; Wireless
---

### Post by goneskiing on 2006-07-07
sudo islist eth1 scan
"device does not support scanning"

sudo iwconfig eth1 essid <....>
shows the BCM 4306 card but no connection

I'm seeing really mixed messages here - I used ndis under Breezy, worked fine.  Now it doesn't connect under Dapper using above commands.  If I want to use native driver do I have to do all that fw cutter stuff ?  Sounds real messy - should I just install ndiswrapper and use as before ?

---

