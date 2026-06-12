---
title: "DVD to .avi on feisty..."
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by mc-rpg on 2007-04-28
Hi. I'm trying to rip some dvds under feisty but the "estimated time" that it gives me is bigger from what it was back in Ubuntu dapper. I don't know why. I've tried acidrip, dvdrip and thoggen and the results are the same. In dapper i rip dvds with the original resolution and was faster (2-3 hrs.) now in feisty loosing quality is 5-6 hrs. when the results gonna be even worse... Someone know whats happening?

---

### Post by disturbed1 on 2007-04-28
This won't apply to Thoggen, but if you're using Xvid see this bug [https://bugs.launchpad.net/ubuntu/+source/xvidcore/+bug/84705](https://bugs.launchpad.net/ubuntu/+source/xvidcore/+bug/84705)

For me, Thoggen jumped x3 in speed, due to using the newest libtheora which actually has mmx compiled correctly this time.

Check top in the command line to make sure the app isn't splitting it's cpu resources with another app. VLC, mencoder, mplayer, tcmux/demux, and transcode all have known memory leaks, that keep the program chewing on resources from time to time, even after you've closed them.

---

### Post by mc-rpg on 2007-04-28
Men thanks, that link in LP solve the problem. Its that something is wrong with the libxvid in Feisty. I just download and installed [this package]("http://librarian.launchpad.net/7419321/libxvidcore4_1.1.2-0.1ubuntu2%7Eproposed1_i386.deb") and everything goes just fine :D

PS: Downgrade to the Edgy's libxvid should work too.

---

