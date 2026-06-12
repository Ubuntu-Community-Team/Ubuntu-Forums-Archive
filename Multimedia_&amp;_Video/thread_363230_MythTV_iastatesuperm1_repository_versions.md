---
title: "MythTV iastate/superm1 repository versions"
date: 2007-02-16
forum: Multimedia &amp; Video
---

### Post by pelago on 2007-02-16
This is a question for superm1 personally really, but I thought it might be best asked and answered in the open for the benefit of the forum archive.

I use superm1's [http://home.eng.iastate.edu/~superm1/](http://home.eng.iastate.edu/~superm1/) repository for MythTV on dapper. Every once in a while the version there gets updated. Is there anywhere that describes what is new in each version? I haven't seen any posts on here or on [http://www.gossamer-threads.com/lists/mythtv/users/](http://www.gossamer-threads.com/lists/mythtv/users/) about it.

The specific reason I ask is that although the latest version is labelled svn20070122, it doesn't seem to have the 'storage groups' functionality that I thought had been added to SVN a couple of months ago.

---

### Post by superm1 on 2007-02-16
> **pelago said:**
> This is a question for superm1 personally really, but I thought it might be best asked and answered in the open for the benefit of the forum archive.

I use superm1's [http://home.eng.iastate.edu/~superm1/]("http://home.eng.iastate.edu/%7Esuperm1/") repository for MythTV on dapper. Every once in a while the version there gets updated. Is there anywhere that describes what is new in each version? I haven't seen any posts on here or on [http://www.gossamer-threads.com/lists/mythtv/users/](http://www.gossamer-threads.com/lists/mythtv/users/) about it.

The specific reason I ask is that although the latest version is labelled svn20070122, it doesn't seem to have the 'storage groups' functionality that I thought had been added to SVN a couple of months ago.
Pelago, I just updated this recently.
Its svn "fixes" that is the date of the fixes snapshot.  That's hopefully the same version that will be going into feisty.

---

### Post by superm1 on 2007-02-16
> **superm1 said:**
> Pelago, I just updated this recently.
Its svn "fixes" that is the date of the fixes snapshot.  That's hopefully the same version that will be going into feisty.
Also,
I haven't been able to keep up with gossamer threads with how busy I am with school now.  If there is any question about it, could you answer for me?

---

### Post by pelago on 2007-02-16
Thanks superm1. Any ideas about the missing 'Storage Groups' functionality? It doesn't seem to be in your latest version but I thought it was in SVN now. Or is Storage Groups not in the 'fixes' branch? I'm afraid I'm not really up on all the jargon.

I don't actually post to the mythtv-users mailing list, I just lurk there.

---

### Post by superm1 on 2007-02-16
> **pelago said:**
> Thanks superm1. Any ideas about the missing 'Storage Groups' functionality? It doesn't seem to be in your latest version but I thought it was in SVN now. Or is Storage Groups not in the 'fixes' branch? I'm afraid I'm not really up on all the jargon.

I don't actually post to the mythtv-users mailing list, I just lurk there.
Well there are two different SVN branches.  The SVN "trunk" branch includes all the new functionality.  The SVN "fixes" branch is for guaranteeing a stable release with extra fixes from the "tagged" release.

So its a balance between choosing a stable release or a feature packed release.  Its a safer bet for packaged releases to be made from the stable releases.

---

### Post by pelago on 2007-02-16
Ah I see, that explains it, thanks.

Do you know of a source of regularly updated packages from the "trunk" branch? Or alternatively, how easy would it be for me to make my own packages from SVN - do you have a 'recipe' or script I could tweak, just changing to get from "trunk" instead of "fixes"?

---

### Post by superm1 on 2007-02-17
> **pelago said:**
> Ah I see, that explains it, thanks.

Do you know of a source of regularly updated packages from the "trunk" branch? Or alternatively, how easy would it be for me to make my own packages from SVN - do you have a 'recipe' or script I could tweak, just changing to get from "trunk" instead of "fixes"?
I wouldnt call it exactly a "straightforward route" to go to trunk.  If you've never built a package, there is a bit of learning curve.  If you look for posts by me, I posted one post explaining exactly whats required to roll your own packages.  Most people are just better off waiting for when 0.21 becomes stable and a package is made for that given the amount of work and building required for building a svn trunk package.

---

### Post by pelago on 2007-02-17
A bit of searching finds this thread [http://ubuntuforums.org/showthread.php?t=314442](http://ubuntuforums.org/showthread.php?t=314442) which I assume is the one you're referring to. I'll have a go compiling it when I'm feeling brave! Thanks.

---

### Post by superm1 on 2007-02-17
Yup, thats it.  Good luck!

---

