---
title: "Network connectivity drops out randomly after upgrading to Jaunty... Help!"
date: 2009-07-25
forum: Networking &amp; Wireless
---

### Post by ShiningMasamune on 2009-07-25
Greetings all,

I have a fileserver running Ubuntu.  I've been rather lazy with keeping it updated; it's been running Gutsy since I installed it.  A week ago I decided finally get off my butt and upgrade to Jaunty.  I did it incrementally, just as the upgrade guide specified.  Everything seemed to go fine.

A day later, the server suddenly dropped off the network.  I hooked up a monitor to the local machine; everything seemed fine.  I rebooted it, and everything went back to normal, and I assumed (hoped) it was a one-time hiccup.  Then today (a week later) it happened again.  This time I did a little more research before rebooting.  I tried pinging google.com from the local terminal; nothing.  I tried running /etc/init.d/networking restart; strangely that made it visible to the rest of the network, but I still couldn't ping google.  Rebooting fixed the problem completely.  Except, this time it went back down about 15 minutes later.  And again 15 minutes after I reset that.

The server was rock solid before I upgraded, and my family really depends on it.  Help?

EDIT: Seems to have stabilized, for the moment at least.  Here's another data point: every time it went down, it was while I was watching a video file streamed from the server.  So maybe it only happens when there is continuous network usage?

---

### Post by ShiningMasamune on 2009-07-26
Sorry to bump, but I'm on the verge of reformatting here.  Are there any log files that can help me figure this problem out before I nuke the whole thing?

---

