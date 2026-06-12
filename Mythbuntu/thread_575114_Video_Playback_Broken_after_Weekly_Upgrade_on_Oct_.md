---
title: "Video Playback Broken after Weekly Upgrade on Oct 12th '07"
date: 2007-10-13
forum: Mythbuntu
---

### Post by DLLarson on 2007-10-13
Help! :confused:

My MythTv setup was just updated using the weekly feisty update and now no form of MythTV playback works. By "no forms" I mean live tv, recorded shows, or DVD ISO's.

I can play recorded files with Totem just fine. How can I roll back this update?

Thanks,
Dale

---

### Post by superm1 on 2007-10-13
I've heard opengl vsync broke in the 0.20-fixes branch recently.  New uploads will be queued soon, hopefully it's been fixed upstream.  Otherwise, you can roll back to the version in feisty-updates still.

---

### Post by DLLarson on 2007-10-14
I managed to locate an older feisty weekly mythtv build on the UK server (The US server didn't allow me to "poke around"). I installed it and the problem is gone. 

I saw the short discussion about the opengl sync problem on the mythtv-dev mailing list.

Thanks for the quick reply! It's what makes Ubuntu the distro of choice.

Dale

---

### Post by laga on 2007-10-14
It was fixed upstream and should be reflected in our next builds.

---

### Post by superm1 on 2007-10-15
Should be fixed now in weekly fixes builds on mythbuntu.org

---

