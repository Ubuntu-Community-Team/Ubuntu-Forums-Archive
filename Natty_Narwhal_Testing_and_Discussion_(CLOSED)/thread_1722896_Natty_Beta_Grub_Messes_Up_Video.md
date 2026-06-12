---
title: "Natty Beta Grub Messes Up Video"
date: 2011-04-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by LaneLester on 2011-04-06
This problem did not occur with the Natty Alpha. With Beta1, after the BIOS gets through and grub runs, my monitor goes blank with a "bad resolution" message floating on it. If I press [Enter] it's obvious that the first grub selection is executed, and Natty starts normally. As soon as X starts, I again have an image.

However, I run more than one Linux install on my machine, so I need to see the grub menu.

I installed the Natty Beta1 on another machine, and this problem did not occur. I guess it's something about my machine/monitor, but I don't know how to fix it. My machine's motherboard has a fairly new nVidia chipset, and the monitor is a Samsung SyncMaster 910T.

Lane

---

### Post by uRock on 2011-04-06
Your Natty questions will get answers faster when you ask in the Natty sub-forum.

Moved to NNT&D

---

### Post by VanR on 2011-04-06
Did you install the proprietary Nvidia drivers?

---

### Post by mdhollis on 2011-04-06
I had the same problem.  I uncommented #GRUB_GFXMODE=640x480 in /etc/default/grub and it resolved my issue.

---

### Post by LaneLester on 2011-04-07
Thanks for the replies, guys!

I scanned the list of forums at the top of the page and didn't see a Natty one. I guess it's not there because it's two layers deep. But thanks for the move.

Yes, I have the nVidia drivers installed, but I think the problem develops before that.

I'll try the mod you suggest, and hopefully, I'll be back to report.

Lane

---

### Post by LaneLester on 2011-04-07
> **mdhollis said:**
> I had the same problem.  I uncommented #GRUB_GFXMODE=640x480 in /etc/default/grub and it resolved my issue.
That was it!

To be honest, the first time I failed to notice the need to run update-grub, so of course, it had no effect.

The second time I went ahead and changed the line to my monitor's native rez, 1280x1024, and it worked just fine.

Lane

---

### Post by mdhollis on 2011-04-07
Glad to help:D

---

