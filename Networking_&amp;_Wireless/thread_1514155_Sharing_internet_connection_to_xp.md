---
title: "Sharing internet connection to xp"
date: 2010-06-20
forum: Networking &amp; Wireless
---

### Post by pg1192 on 2010-06-20
Allrighty.  I have a acer aspire one netbook, dualbooting windows 7 starter and ubuntu 10.04 UNE.  Since windows doesn't seem to support network sharing, I realized that ubuntu probably has a solution.  Right next to this one is a hp pavilion zd7000 running windows xp, very old and malfunctioning often.  Its wireless card does not work.  However, its ethernet is fine.  I'm currently using my phone as a wifi hotspot, just like a router.  Basically, I'd like to use ubuntu to allow the hp pavilion to connect to the internet by connecting to my netbook ethernet port, the netbook connected to the phone via wifi.  I'm not very experienced when it comes to connection sharing, so any help is appreciated.

thanks!

---

### Post by Joe of loath on 2010-06-20
On the netbook, right click network manager, select 'edit connections', click 'auto eth0', click edit, then click 'ipv4 settings'. You'll see a drop down box, and in there select 'shared to other computers'. It should now work.

---

### Post by Iowan on 2010-06-21
Depending on your ethernet card(s), you *might* need a crossover cable between the machines (or a hub/switch/router) to make things work properly.

[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is an article that might be helpful.

---

