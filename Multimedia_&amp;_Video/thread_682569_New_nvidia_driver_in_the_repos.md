---
title: "New nvidia driver in the repos?"
date: 2008-01-30
forum: Multimedia &amp; Video
---

### Post by MightyMe on 2008-01-30
I have the restricted nvidia driver enabled and now I see that there are a new driver out 169.09 (21 Jan 2008). My questions are:

1. Why arent the new driver(s) in the repos for an  easy upgrade?
2. To upgrade, I see poeple have been using Envy. Is this recommended or should I wait for a new driver in the repos?

---

### Post by AndyCooll on 2008-01-30
The way that Ubuntu works (and indeed most Linux distros) is that once a release is out of the door the repos will effectively be frozen ...apart from security updates and occasionally "significant" apps released through backports. In effect all software will stay at the same release number.

This is for a number of reasons. Amongst them is the fact that the product they have just released should be stable, and to introduce changes now may have a detrimental effect. Updated apps may well require updated libraries, so it would mean not just the app itself that would need updating. This would in turn mean developers time being taken up.
Instead developers concentrate on integrating updated apps in the next release rather than having to spend time testing whether an updated app will work on old releases. Since a new release of Ubuntu is every six months, it usually isn't long before the updated app reaches the masses. 

So, unless the new nvidia driver release was to fix a significant fault or security problem it is unlikely to be updated in the repos. It will probably be included as part of the next Ubuntu release (Hardy Heron) instead.

:cool:

---

### Post by njparton on 2008-01-30
Envy is great - go for it!

My GPU fan no longer sounds like it's going to self destruct anymore, ahhhh...

169.09 fixes quite a few irritating bugs.

---

### Post by eye208 on 2008-01-30
> **AndyCooll said:**
> So, unless the new nvidia driver release was to fix a significant fault or security problem it is unlikely to be updated in the repos.
The XVideo capability of Gutsy's Nvidia driver is partially broken. Threads related to this problem come up at least once per day.

I do understand that Ubuntu cannot update every package in a timely fashion. But a display driver is mission-critical. You cannot call a release "stable" as long as its display driver is broken.

Why there is no update in the gutsy-backports repository is beyond me.

---

### Post by MightyMe on 2008-01-30
Ok, I think I'm going to give  Envy a go. Thanks for all the information guys.

---

