---
title: "Mythbuntu 7.10 and database version error"
date: 2008-04-05
forum: Mythbuntu
---

### Post by kbehel on 2008-04-05
I tried to add mythvideo to my mythbuntu frontend and had a problem with the database version on the frontend being at 40 and the backend at 31. The error I get is that they cannot communicate due to this difference.

I think this problem should be common to any 7.10 Ubuntu installation where they try to install a new feature.

I suspect the problem is that Mythbuntu (or apt/Synaptic) is trying to install the latest bleeding edge version of MythVideo with all the other bleeding edge dependencies, when all I really want is to install a version of mythvideo that is compatible with the install I already have.

Is it even possible to do this? Am I forever doomed to being at the whim of Ubuntu repository changes that will trash a nicely working system when I want to install a new feature? Is it possible to install a version of a package (such as MythVideo) that was released at the same time as the currently installed software????!?!?

Updating my backend server is NOT an option - it works, I've spent too much time getting it working, and I have no desire to rebuild it. I had to do that TOO many times just getting this backend working - good thing I used partimage and figured out how to make a stable backup image otherwise I'd have been in real trouble several times.

Any useful help is appreciated.
not a nob (far far from it) but VERY down on all the Ubuntu instability.

Kevin

---

### Post by tgm4883 on 2008-04-06
Use synaptic,  You should be able to choose which version you want installed

---

### Post by kbehel on 2008-04-06
Ah... perfect. That worked. I did not realized that with Synaptic I could force an older versions without changing the repositories or something. When it comes to Synaptic and Ubuntu I must confess I am a bit of a novice - a lot has changed since I last had linux running. 

For anyone who reads this needing similar help - You can force the version from the package-> force version menu. I highly recommend this if you don't want lots of functional stuff being automatically "improved" for you without warning.

thanks again,

Kevin

---

