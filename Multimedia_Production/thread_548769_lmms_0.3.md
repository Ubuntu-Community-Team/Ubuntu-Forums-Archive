---
title: "lmms 0.3"
date: 2007-09-11
forum: Multimedia Production
---

### Post by joegiampaoli on 2007-09-11
Trying to build the new lmms 0.3 with absolutely no success under edgy, anyone has any news on the deb packages for lmms version 0.3? Or anyone know how to compile it under edgy from sources?:confused:

---

### Post by Stochastic on 2007-09-17
how far do you get when you try to build it from source?  what's the error that it spits out at you?  chances are that you have unmet dependencies and you may just find that even if the edgy repos have the desired libraries/programs they'll probably be older versions than what lmms is looking for so you may have to then build the newer versions of said dependencies from source.  You may have stepped into what's commonly referred to as dependency hell.

---

### Post by joegiampaoli on 2007-09-17
almost to the end of the configure, don't remember now but yes, it's some dependency hell, just as if I was building something under another linux distro, but thanks anyway I'll wait patiently till someone builds the propper deb package and then may it be placed in the repo.

---

### Post by gmoore on 2007-09-17
Sounds like I've had similar issues with compilation under feisty. configure seemed to go ok, but make failed.Something about Error 2 and missing initializer for the audio file processor librariies, it looked like it couldn't find the ladspa directory, even thought its clearly there in the extracted zip file.

I tried the debian package but got no jack support.

Does anyone know the release schedule for the Ubuntu package?

Thanks

---

