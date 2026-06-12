---
title: "--verion showing &quot;0.27-pre...&quot;?"
date: 2012-10-03
forum: Mythbuntu
---

### Post by uncle hammy on 2012-10-03
With 0.26 being release yesterday, I did an update to my machines (Mythbuntu 12.04) that have been running master (by selecting 0.26 in the Mythbuntu Control Center's Repos panel), hoping to see the "rc2" gone.  Now I see that mythbackend --version is showing
> 
MythTV Version : ***_v0.27-pre-3-g6a7e351_***
MythTV Branch : master
Network Protocol : 75
Library API : 0.26.20120822-1
QT Version : 4.8.1

Is this cause for concern?  I haven't changed anything in my repos selection (in fact, the only options are still 0.25/0.26), so I would expect the version to be 0.26....  and the branch to no longer be master.

---

### Post by tgm4883 on 2012-10-03
> **uncle hammy said:**
> With 0.26 being release yesterday, I did an update to my machines (Mythbuntu 12.04) that have been running master (by selecting 0.26 in the Mythbuntu Control Center's Repos panel), hoping to see the "rc2" gone.  Now I see that mythbackend --version is showing

Is this cause for concern?  I haven't changed anything in my repos selection (in fact, the only options are still 0.25/0.26), so I would expect the version to be 0.26....  and the branch to no longer be master.

No cause for concern. 0.26 got released during a 4 week window where it would cause us an issue. There are no db schema differences between 0.26 and 0.27 right now. We've fixed it in the builds, which will be available in the next few hours.

Since there are no schema differences, you'll just need to update as usual to resolve this issue.

---

### Post by uncle hammy on 2012-10-03
Cool, thanks

---

