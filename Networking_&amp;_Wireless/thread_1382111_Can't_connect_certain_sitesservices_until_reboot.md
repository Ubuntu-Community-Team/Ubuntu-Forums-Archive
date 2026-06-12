---
title: "Can't connect certain sites/services until reboot"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by mikeize on 2010-01-15
This happens regularly if not always.  I leave my computer on overnight (torrents ;) ).  My computer never goes to sleep or hibernates.  The next day, I find that some things work and some don't!  Specifically, Gmail is totally unable to connect.  Nexuiz is totally unable to connect (no servers shown).  Chatzilla is totally unable to connect (quakenet or freenode).  Those are the big 3 that I notice.  Other things work, such as ubuntuforums.org, google.com, and stumbleupon extension works fine.  Oh, weave extension does not connect, but ubuntu-one is fine.

The only way I can fix this issue is to reboot the computer.  Restarting X does not do the trick.  What the heck is going on, and how can I fix it without rebooting?  Thanks!  :KS

-mike

---

### Post by mikeize on 2010-01-15
someone suggested I check for cron jobs related to firewall stuff.  I have one to update ipblock, but I ran that program manually, and had none of the problems I described above.

---

### Post by mikeize on 2010-02-25
Bumping this thread, since I still experience this issue.  The only fix is a reboot.  Restarting networking does not do it.  Surely someone wants to help me solve this mystery? :popcorn:

---

### Post by mikeize on 2010-05-10
Ok, I've made some headway, but still confused.  Just today, I had the same problem, but a reboot did not it.  Messing around, I found that STARTING ipblock, actually fixed all the issues.  If I turned it off again, some services kept working (ie, google), while others did not (ie, weave).  Though the obvious solution is to keep ipblock running all the time, I would still LOVE for someone to help me understand this problem, and why NOT having ipblock running, should cause these problems.

---

