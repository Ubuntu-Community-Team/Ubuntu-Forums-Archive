---
title: "Mythbuntu (XFCE) startup delay"
date: 2011-06-03
forum: Mythbuntu
---

### Post by davidstoll on 2011-06-03
I save my session because there are two things that I like to have running when my machine starts (file manager and command prompt).  However, just recently Thunar starts and then about 30 seconds later the command prompt opens up (then the normal Mythtv program immediately starts).

I was hoping to find out what is causing the delay.  There is very little (if any) HDD activity and low CPU usage during this delay.  Also, the machine is very responsive, so it's not frozen or sluggish during this time.

Can anyone tell me where this "session" is saved?  Maybe there is an entry in there that is causing my problem.  I also checked ~/.config/autostart/ and there isn't anything in there except the mythtv call and an XFCE helper script of some sort that gets auto generated even if you remove it (I tried).

Maybe there is something else I should look at?

---

### Post by David Grigor on 2011-06-03
I don't have filemanager in my autostart but I have noticed lately that file manager takes a while to fire up. I just assumed it was becuase of some sshfs directory shares I have setup to I can rip dvds straight to my backend directories from a frontend. Running 64bit mythbuntu 11.04 frontend only.

---

