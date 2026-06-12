---
title: "Some Natty problems with graphics ... and other problems"
date: 2011-02-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by An Sanct on 2011-02-24
Ok, I use Maverick and Natty (dual boot)

So I can run Natty just okay, but the proprietary drivers are not working. If anyone can help me here ...

The error is:
> SystemError: E:Unable to correct problems, you have held broken packages.And if I go to Synaptic, do Edit > Fix broken packages, it says "Successfully fixed dependency problems".
Also under "Custom Filters" > "Broken", I have en empty list...

The update manager says either all updates are done or "*partial upgrade*" and then something like "*all updates are fine, no updates available*" ***** (not a direct quotation, from memory)

PS. ... And this is not so important, since it is Alpha2: The cursor disappears slightly randomly, I thought it was a Virtual Box issue, but I found it also on a "real" install, the funny thing is it often happens if the cursor is not "normal", normal meaning a normal arrow pointer (IE. it is a *over text* shape or it is a *hand* or a *hourglass*) and even then, only if it moves over text in the contra-reading direction pixel by pixel (I haven't tried Arabic or so, but so it seems).

***** edit:
The error is 
> Your system is up-to-date
There are no upgrades available for your system. The upgrade will now be canceled.

---

### Post by cariboo on 2011-02-24
If you've been using Natty for the last couple of weeks, and checking this sub-forum, you should know that the restricted drivers don't work yet, depending on you graphics hardware the open source drivers should work well for you. I'd suggest giving the hardware manufacturers a couple of weeks to release a driver that works with the latest version of Xorg-xserver.

---

### Post by An Sanct on 2011-02-26
I thought so, but graphics don't work okay for me, I'm Always "falling back" to classic desktop, just like as if unity wouldn't work. It displays okay in a virtual machine (host Maverick, guest Natty)

Any thoughts about that cursor thing I mentioned?

---

