---
title: "Partial Lock - Live TV - HDHomerun"
date: 2012-04-03
forum: Mythbuntu
---

### Post by Car_Ramrod on 2012-04-03
I've tried everything I can think of at this point so I'm looking for some advice.

I have the following setup:

HDHomerun Prime with Cablecard
Mythbackend  (Unbuntu 11.10)
Mythfrontend  (Mythbuntu)
Multiple Windows 7 Machines

If I try to watch TV from WMC7 then it works fine.
From any of the Ubuntu machines, I get partial channel locks and no live TV works.  Using the hdhomerun config gui, all the machines are the same in regards to signal.

Initially, I thought it was a network problem so I uninstalled ufw from the ubuntu machines and did a tcpdump.  Everything looks fine.  I have a Check Point firewall so I hopped on that thinking maybe a multicast problem, but no issue there.  Everything is on the same subnet.

I'm just out of ideas on what else to check.  Any ideas?

---

### Post by uncle hammy on 2012-04-04
You don't indicate what version of MythTV, but did you follow the actual setup instructions for Prime / Mythtv?

[http://www.mythtv.org/wiki/Configuring_MythTV_for_the_HDHomeRun_Prime](http://www.mythtv.org/wiki/Configuring_MythTV_for_the_HDHomeRun_Prime)

---

### Post by keithc50 on 2012-04-06
I too am having the same issue. I did notice that if I have wmc locked on one of the tuners MythTV was then able to record on the other 2 tuners. I am using MythTV 0.24.2. This just started about 2 days ago.

---

### Post by keithc50 on 2012-04-07
Fixed my problem, upgraded firmware of HD Homerun to version 20120405.

---

