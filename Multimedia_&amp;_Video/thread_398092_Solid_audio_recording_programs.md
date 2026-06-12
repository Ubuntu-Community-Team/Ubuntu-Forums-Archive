---
title: "Solid audio recording programs?"
date: 2007-03-31
forum: Multimedia &amp; Video
---

### Post by ronocdh on 2007-03-31
Hey guys, I've been looking for some decent audio recording programs for a while now. I can remember finding a couple that appeared rather utile, but I never got around to trying them out.

I bring it up now because a friend was trying to record a CD this week, and on a fresh install of XP, he couldn't get his software (SONAR and Acid) working; all tracks he laid were several milliseconds off! In a fit of frustration, he allowed a well-meaning friend to install Debian in an attempt to record in a Linux environment. (Why they used Debian for multimedia, I'll never know.) Problem was, his soundcard, the Creative X-Fi, has zero support! So scratch that.

Right now he's selecting a new soundcard with open driver support, and I wanted to be able to wow him with a great audio recording suite, to lure him away from Windows for good. What do you guys recommend? I currently have found [http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/) and right now that's looking like the top of the heap.

Thoughts??

---

### Post by garybrlow on 2007-03-31
Try Audacity, it works for both windows/linux with no jack . You may want to try Ubuntu Studio [http://ubuntustudio.org/](http://ubuntustudio.org/) but it still has to be released along with feisty but their data packages are already on the repos. Linux has a different method in using sound for recording and midi creation as compared to windows. Linux uses jack and windows doesn't. Jack has latency issues on a normal kernel but patches have been made to accommodate Ubuntu Studio - a dedicated distribution for sound and multimedia production. Hopefully Ubuntu Studio will set on to improve sound production in Linux.

You  can use rosegarden right now but it also uses jack and you will experience the latency issues on edgy's/feisty's normal kernel. You have to install or switch to the patched low-latency kernel catered for Ubuntu Studio which is already on the repos. Search for lowlatency and you will find the kernel image there. Am not really sure how effective the patched kernel is since I haven't tried using it but the people behind Ubuntu Studio hang in the Multimedia and Video section of the forums so for more advice and information post something there. :)


Cheers!!!

GaryBrlow :biggrin:

---

### Post by ronocdh on 2007-04-01
Gary,

awesome reply, thanks a lot! I was definitely looking for something with a bit more functionality than Audacity, which I should have mentioned in the OP, but Audacity is certainly reliable. Thanks most for the mention of low-latency kernel, that's news to me. I'll also have to read up on jack, to get that straight.

Anyone else have any recommendations for advanced recording programs?

---

### Post by christhemonkey on 2007-04-01
When feisty is out, you should be able to pull a low latency kernel from the repos, so that shouldnt be a problem.


IMHO The best audio solution is definately Jack+Ardour.

Both having been designed from the ground up for proffesional low latency audio work.

---

