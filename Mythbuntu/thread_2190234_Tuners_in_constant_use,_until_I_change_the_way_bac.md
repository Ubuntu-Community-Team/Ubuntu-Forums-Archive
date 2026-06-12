---
title: "Tuners in constant use, until I change the way backend starts"
date: 2013-11-26
forum: Mythbuntu
---

### Post by drifting on 2013-11-26
I have just installed two TBS cards a 6982 DVB-S & 6280 DVB-T into what was my perfect running Mythbuntu .27, well the satellite side was fine, but had to ditch the terrible Nova-TD USB.

Problem I had was constant tuners are in use, yet with scan then play via mplayer they work fine? Now by accident I stopped the backend and thought about starting it verbose, but instead of doing a sudo service mythbackend stop & atart I just ran mytbackend on it's own. Tuners now work in Myth? , did try starting as a service again and the tuners are all busy again? Is this some sort of permissions issue with the tuners? Not quite sure where to look? any hints ?

Paul.

---

### Post by bullwinkle2 on 2013-11-26
> **drifting said:**
> I have just installed two TBS cards a 6982 DVB-S & 6280 DVB-T into what was my perfect running Mythbuntu .27, well the satellite side was fine, but had to ditch the terrible Nova-TD USB.

Problem I had was constant tuners are in use, yet with scan then play via mplayer they work fine? Now by accident I stopped the backend and thought about starting it verbose, but instead of doing a sudo service mythbackend stop & atart I just ran mytbackend on it's own. Tuners now work in Myth? , did try starting as a service again and the tuners are all busy again? Is this some sort of permissions issue with the tuners? Not quite sure where to look? any hints ?

Paul.

How are you getting your scheduling information?  I don't know how it works in your area, but where I live, if you tell MythTV that you want the scheduling information that's embedded in the transmitted signals, then apparently the Myth backend constantly scans those channels when a tuner is not otherwise in use.  If, on the other hand, you use something like [mc2xml]("http://mc2xml.dyndns.org") to get schedule information, then it doesn't do that.  I found this out when I originally set up MythTV with a HDHomeRun Dual and the tuner lights were constantly on.

---

### Post by drifting on 2013-11-27
Hi thanks
Yes, it is using EIT data, and has been for a long while, this has only happened since I have installed the new DVB-T card. Strangely enough I have not even installed a new driver, as being the same company (TBS) it uses exactly the same one.

---

### Post by bullwinkle2 on 2013-11-27
That's it, EIT.  I could not think of the term.  Anyway, I have no idea  why it didn't do that before you installed the new tuner, but I was told  that's normal behavior when you use EIT data.  Which seemed weird and  rather undesirable to me - IMHO it should only recheck at specific  preset intervals, like maybe every hour or two.  But, apparently, that's  not how it works, or at least that's what i was told.

---

