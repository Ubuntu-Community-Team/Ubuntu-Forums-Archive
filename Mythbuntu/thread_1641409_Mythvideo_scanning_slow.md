---
title: "Mythvideo scanning slow"
date: 2010-12-09
forum: Mythbuntu
---

### Post by GuiGuy on 2010-12-09
Hi,

I've had to rebuild my backend/ frontend due to a hardware failure. Using Maverick/ 0.23.1 I'm having to run the usual gauntlet of problems (sound not working, video play back corruption etc etc). I am now up to mythvideo:

Most video and music files are stored on a QNAP NAS box.

Mythvideo is taking an unusually long time to present a menu. The delay is something like **20 to 30 minutes** which now renders mythvideo useless. 

My previous install (Lucid), running on the same network, only took a couple of minutes, which I thought was bad enough. 

Anyway, any ideas how I can prevent the autoscan every time Mythvideo is activated or to speed mythvideo up?

NB: Network performance (wired Gigabit) is fine.

Thanks

---

### Post by GuiGuy on 2010-12-09
Update: 
I've worked out that about a third of the time is spend "scanning" the NAS device. However, general access and file transfer to and from the QNAP is relatively good (RAID 5).

The other two thirds it's "Updating (the) Database"

---

### Post by GuiGuy on 2010-12-09
Nevermind; I worked it out. Need to force a rescan, which seems to have fixed the slow database update.

The scanning of the NAS box remains a mystery for now..,

---

