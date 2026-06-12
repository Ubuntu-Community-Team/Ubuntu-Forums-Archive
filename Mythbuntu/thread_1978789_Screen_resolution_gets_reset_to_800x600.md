---
title: "Screen resolution gets reset to 800x600"
date: 2012-05-12
forum: Mythbuntu
---

### Post by bjw1 on 2012-05-12
After trying a newer version of Ubuntu (12.04) then reverting back to 10.10, I to got stuck with 800x600 resolution on my GeForce GT 545.  Updated Nvidia drivers, purged and re-install both nvidia and X11 to no avail.  The xorg.conf file had the desired mode of 1920x1080
Adding another user and logging in as them I got the desired 1920x1080 which is the clue that there is something else in the users home drive causing this.

 In .config I located a file ,monitors.xml, which contained setting for, well, monitors.  In here the width was set to 800 and the depth to 600.  Changing these to 1920 and 1080. logging out and back on resolved my problem.

I Suspect the monitors.xml file could be deleted as the new user does not have it.  I further suspect that it was added as part of Unity.

:)

---

### Post by thatguruguy on 2012-05-12
> **bjw1 said:**
> 

I Suspect the monitors.xml file could be deleted as the new user does not have it.  I further suspect that it was added as part of Unity.

:)

1. Why are you responding to a thread that is nearly two and a half years old?
2. How could Unity have anything to do with a problem which existed in 9.10, when Unity wasn't introduced until 11.04?

---

### Post by overdrank on 2012-05-12
Hi and welcome, I have moved your post to it's own thread. :)

---

