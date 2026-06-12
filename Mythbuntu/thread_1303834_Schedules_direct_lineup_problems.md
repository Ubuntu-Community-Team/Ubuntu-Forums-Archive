---
title: "Schedules direct lineup problems"
date: 2009-10-28
forum: Mythbuntu
---

### Post by resolost on 2009-10-28
The problem started when I was running Mythbuntu 9.04 with a HVR-1600. Previously everything was working fine and I had lineups for both the digital and analog tuners. Randomly the mythfilldatabase command was failing, so I decided to look into it. I have been able to narrow down my problem. When I go into mythtvsetup and add the lineups, it does not retrieve any lineups from schedules direct. I tried deleting both lineups then adding them back, but I got the same result. What I was able to discover was that when I only added one "LocalBroadcast" lineup, everything worked fine. I was able to get my digital listing with no trouble. When I try to use only the cable lineup, it brakes again and I cannot even see the lineup in mythtvsetup. I have already tried completely removing my mythconverg database and rebuilding it, but that also did not work. 

I have also recently did a clean install of Mythbuntu 9.10 RC and I still cannot get listing for both of my sources.

I believe this is a mythtv/mythbuntu problem because I am able to get the listings using tv_grab_na_dd.

Does anyone have any ideas on how to fix this problem?

---

### Post by resolost on 2009-10-30
bump

---

