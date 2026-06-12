---
title: "Fresh 10.04, mythbackend requires restart on boot"
date: 2010-07-07
forum: Mythbuntu
---

### Post by SnafuFlux on 2010-07-07
I've been using mythbuntu for 3 years now.  the last version I had running was great.  however I'm one of those suckers who see a new version and want to upgrade.  so I did.

Every time I boot, when the front end loads, one of two things happen:
1) can't find the backend, providing me with the error saying "can't find back end, do you have the right ip?  is it running?"
2) Front end will not prompt error, but cannot play livetv (doesn't have any listings).  

so far, I've found that I can sudo restart myth-backend.  this will clear up all problems - that I can tell so far.

but I don't want to have to do this.  it should be running perfect, right away.

edit: it's almost like the front end loads to fast.  The backend doesn't get to do all it needs to, thus mucking something up....

can anyone please help me out?!

edit 2:  I just noticed that I get the error "Error MythTv is using all inputs, but there are no active recordings?"

if I check info centre it says both tuners have errors.  these tuners are the hauppauge 150's (2 in total)

---

### Post by tgm4883 on 2010-07-07
what is the full build number of mythtv you are using?

---

### Post by SnafuFlux on 2010-07-07
tbh, I'm not 100% sure.  whatever comes preloaded in mythbuntu's most current 32bit ISO.  MythTV 0.23 build 24104, according to the site?  Anyway for me to check?  

I should note, I'm a linux nub!

---

### Post by SnafuFlux on 2010-07-07
my apologizes.   it appears you have already addressed/fixed this issue.
[http://ubuntuforums.org/showthread.php?t=1511342](http://ubuntuforums.org/showthread.php?t=1511342)

I will do a bit more reading.  I'm not 100% sure how to apply auto-builds.

---

### Post by SnafuFlux on 2010-07-07
fyi, I'm currently using 0.23.0+fixes 24

---

### Post by SnafuFlux on 2010-07-07
problem solved.  Applying mythtv updates fixed problems.

thank you.

---

### Post by tgm4883 on 2010-07-07
> **SnafuFlux said:**
> problem solved.  Applying mythtv updates fixed problems.

thank you.

Yep, thought it would. Please mark the thread as solved

---

