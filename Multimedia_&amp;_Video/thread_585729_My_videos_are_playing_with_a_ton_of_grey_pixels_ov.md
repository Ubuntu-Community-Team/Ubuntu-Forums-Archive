---
title: "My videos are playing with a ton of grey pixels over them"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by Marty McFly on 2007-10-21
I'm using ubuntu more than XP and started watching downloaded tv shows in the Totem player and they are coming out with all these grey dots on them....it's like I'm watching the video through a screen door =\

I thought it may be the player, so I downloaded VLC and it's doing the same thing.  It's just a normal AVI file that I'm playing....any ideas?

---

### Post by Light- on 2007-10-21
whats your graphics card make+model?

are you using open-source drivers or restricted drivers?

do you have Compiz running?

---

### Post by Marty McFly on 2007-10-21
1. Onboard video:

VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

2. I don't know (I'm new to this)

3. Yes

---

### Post by Marty McFly on 2007-10-22
Bump

---

### Post by Marty McFly on 2007-10-23
anyone?

---

### Post by Marty McFly on 2007-10-24
.................

---

### Post by Marty McFly on 2007-11-06
:(

---

### Post by williammanda on 2007-11-06
Review this post and see if you have the same problem:
[http://ubuntuforums.org/showthread.php?p=3680576#post3680576](http://ubuntuforums.org/showthread.php?p=3680576#post3680576)
Thanks

---

### Post by ski309 on 2007-11-08
I recently had this problem after upgrading to 7.10.  I tried turning Compiz off completely and it fixed the problem.  I want my Compiz back tho!

---

### Post by rafar on 2007-11-08
I think you should check which overlay your player is using. Just go to player preferences->video section and select openGL instead of whatever you're using now. Thats how i got mine to render properly.

---

### Post by ski309 on 2007-11-08
Thanks rafar, that fixed it.

---

### Post by jonno on 2007-11-28
Aha! I have the same video chipset and the same exact problem. [Here]("http://ubuntuforums.org/showpost.php?p=2896078&postcount=2") is some more detail how to configure various players.
However I'm now having the same issue with Skype video which won't allow you to select a different video overlay (it uses Xv only apparently).
So there appears to be a conflict with this chipset and the Xv overlay. [Here]("http://ubuntuforums.org/showthread.php?t=625168") is a thread I started on the subject.

---

