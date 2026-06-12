---
title: "[SOLVED] Garbled dispay on Compaq 1800T with Feisty"
date: 2007-05-03
forum: Multimedia &amp; Video
---

### Post by rrwo on 2007-05-03
I have an old Compaq Presario 1800T that I decided to install Feisty on.

The X server only recognizes 800x600 resolution, even though the video card supports higher resolutio. (It used to run Dapper, which had no problem recognising the video card and supporting higher resolutions, like 1024x800 and 1280x1024).

Worse, there's a thin verticle line just to the right of the middle of the screen that extends from top-to-bottom.  It looks like there's a problem with video memory, because sometimes when the mouse pointer is in a idfferent part of the screen, a bit of it can be seen in this thin garbled line.

How do I fix this?

---

### Post by jrmink on 2007-09-19
I have the same exact problem but no one wants to seem to hep us 18000T users.

---

### Post by Certify on 2008-02-19
I have the same laptop.  I believe it's an overheating issue- I think the fan stopped working and the video card is the first to go when the laptop overheats.  I believe the video card chips are located underneath the motherboard.

Try this- apply some pressure near the center of the laptop on the bottom (close to the RAM upgrade panel screw).  You'll see some further distortion in the image displayed onscreen.  You should also find the hottest part of the laptop near this area.

My laptop's very finicky; it seems to display text mode fine, but full graphics modes rarely work without glitches.

---

### Post by rrwo on 2008-03-08
Why would the laptop suddenly overheat when upgrading Debian or Ubuntu?

---

### Post by rrwo on 2008-03-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/16842](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/16842) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I tried Hardy and found the same problem.  But a quick search in the bug database found a solution:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/16842](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/16842)

---

