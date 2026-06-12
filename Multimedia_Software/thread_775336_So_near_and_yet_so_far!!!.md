---
title: "So near and yet so far!!!"
date: 2008-04-30
forum: Multimedia Software
---

### Post by tarmitag99 on 2008-04-30
With great anticipation I loaded up Hardy Heron and was ecstatic to see it picked up my 1440x900 laptop panel (No more messing around with 915resolution) and it picked up the wireless card and openoffice translated my ppt's without any problems - my life was sorted.  

I take the laptop into work attach my second monitor and it detected it and offered me the screen resolution app to set the resolution of each device - and thats when things went horribly wrong.  I cant get an extended desktop at two different resolutions (it always shows the single desktop and cant do the two resolutions correctly).  I find hundreds of web sites saying use this, change that run xrandr, edit xorg.conf are you using xzy etc etc.  Why should I have to do all that - Windows does this perfectly - why, after so many years cant this be done in Linux/Ubuntu.  

I have a Dell Latitude D620 with the Intel 945 graphics - has anyone managed to get dual monitor working properly (with extended rather than cloned desktop) with the 1440x900 panel and a 1280x1024 digital/analog lcd monitor. If so can you explain in easy terms how you did this.

Surely dual monitor support shouldn't be this hard (after all my XP laptop does it without a hitch)

Any help appreciated

Mr Disappointed

---

### Post by chewearn on 2008-04-30
See if this will help you out:
[http://ubuntuforums.org/showpost.php?p=4828822&postcount=4](http://ubuntuforums.org/showpost.php?p=4828822&postcount=4)

Btw, the link at the end of the post will explain it's a bug, why you get clone mode only.

---

### Post by tarmitag99 on 2008-04-30
AstalaVista

Thanks for that - I had already been through this but as the article you reference points out at the bottom there is a bug that means in the Intel 945 you can't set virtual to better then 2048 x 2048 without losing DRI.  1280x1024 monitor and 1440x900 laptop panel means I need more than I can get.  If I lose DRi then things like Google Earth die a horrible death!!!

I'm not a fan of Windows - I'd love to ditch it!!  BUT as pointed out this works without a hitch in XP.

Thanks

Mr Disappointed

---

### Post by chewearn on 2008-04-30
Ok, sorry about that.  I misunderstood your question.  You are not asking for a solution.  You already search extensively and didn't find it.

What you will like to know is why Windows works better in this than Linux.  To this question, my guess will be Windows has significantly larger market share, Intel automatically fix their driver first in Windows, and put less effort for Linux.

Mind, this just my guess.  I don't think this answer helps you in anyway, but you did ask, so it's free of charge. :lol:

---

### Post by tarmitag99 on 2008-04-30
OK so now I've figured that if I have an above/below config for my screens then I can do this as it stays in the 2048x2048 virtual screen limit (needed to keep DRI).  Not my preferred option but I'll have to see if I can get used to it.

Mr Less Disappointed

---

