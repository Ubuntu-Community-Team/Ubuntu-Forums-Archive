---
title: "Choppy playback after a few minutes"
date: 2009-10-11
forum: Mythbuntu
---

### Post by jgull8502 on 2009-10-11
My mythtv backend is running on arch linux but my frontend is on Ubuntu 8.04. (I run mythfrontend with --upgrade-schema... this seemingly allows an older version frontend to run with a newer backend)

After a few minutes of playing a recording, the playback gets choppy somewhat randomly. It freezes every second or so. If I pause playback, it runs fine for another few minutes. 

I'm wondering if this could be related to the ubuntu dimming the screen after inactivity, but I'm not sure what controls this. 

Has anyone else had this problem?

---

### Post by Crash87ss on 2009-10-12
I'd check the frontend logs first and see what that is doing. should be in var/lib/mythtv. 
Take a look at the times when playback was giving you issues.

---

