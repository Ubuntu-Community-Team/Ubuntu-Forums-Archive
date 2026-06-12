---
title: "black and white video?"
date: 2007-11-10
forum: Multimedia &amp; Video
---

### Post by oysterpog on 2007-11-10
hey guys

my video files (generally avi or mpeg) are now only playing in black & white, in both totem and VLC. why is this happening? i dont get it.

many thanks in advance

---

### Post by avik on 2007-11-10
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/149791](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/149791) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm guessing the bug I mentioned is it, so check the fix at the bottom of that page.

---

### Post by TylerMcManus on 2007-11-13
> This post could be related to an Ubuntu bug filed at: [https://bugs.launchpad.net/ubuntu/+s...el/+bug/149791](https://bugs.launchpad.net/ubuntu/+s...el/+bug/149791) 

confirmed. i had this same problem, and the solution on the above link worked for me. thanks avik. i'll pay it forward and save someone the trouble of following the link lol. the fix is below:

"rm -r ~/.gconf/apps/totem" and then logout and login again.

---

### Post by philidox on 2007-11-25
Thanx alot that was an easy fix

---

### Post by Langleyo on 2008-01-30
Thanks so much guys, was pulling my hair out on this. Hope this is the appropriate place for this message, if not, apologies.

---

### Post by vamsibethapudy on 2008-01-31
in recent posts in the particular bug forum ,
it is said that changing the saturation level in totem might fix the problem.
i tried it & it seems to work.
i will update again if it does not work.

---

### Post by rare HERO on 2008-02-20
tried the fix in the above post.
still won't work in VLC
works w/ movie player (totem)
guess this will have to do.

---

### Post by vamsibethapudy on 2008-02-24
its works with my VLC, hero.
but i happen to notice that the saturation level seem to readjust to 0, sometimes.
i had to change it again & it works normal again!

---

### Post by lunanueva on 2008-02-24
thanks for the fix, worked great for movie player, haven't tried vlc yet.  cheers to the forum:KS

---

### Post by vamsibethapudy on 2008-02-25
check if its working with vlc or not.
dont forget to thank the person/persons who gave the solution to the problem!

---

### Post by rare HERO on 2008-03-02
Color video now in both Totem & VLC,

Thanks.

---

