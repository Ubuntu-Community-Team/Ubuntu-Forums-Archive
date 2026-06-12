---
title: "Mythbuntu 0.24 ppa Bulds - problem"
date: 2010-06-03
forum: Mythbuntu
---

### Post by awaterson on 2010-06-03
Hi,

I have been trying to use the mythbuntu 0.24 ppa builds for a while,but there seams to be a problem building these since the 10/05/2010. I have even tried building them myself but to no avail.  Does anyone know what the issue is with the autobuilds and where they may be running again?

Regards

Andy](*,)

---

### Post by superm1 on 2010-06-03
A bunch of patches keep breaking due to upstream changes - you can see the latest build log here:

[http://smithers.mythbuntu.org/~autobuild/weekly_trunk.txt](http://smithers.mythbuntu.org/~autobuild/weekly_trunk.txt)

---

### Post by superm1 on 2010-06-03
> **superm1 said:**
> A bunch of patches keep breaking due to upstream changes - you can see the latest build log here:

[http://smithers.mythbuntu.org/~autobuild/weekly_trunk.txt](http://smithers.mythbuntu.org/~autobuild/weekly_trunk.txt)
So that said, tgm4883 worked on this a little last night - I think he got the perl patch fixed.

---

### Post by awaterson on 2010-06-03
> **superm1 said:**
> So that said, tgm4883 worked on this a little last night - I think he got the perl patch fixed.

Thanks for all your work on this.  I feel if I could do something to help resolve the problem, I could contribute a bit. :cool:

---

### Post by superm1 on 2010-06-03
> **awaterson said:**
> Thanks for all your work on this.  I feel if I could do something to help resolve the problem, I could contribute a bit. :cool:

If you notice it breaking in the future again like this, and have the skills to fix the broken patches, that would be awesome!

If you don't have the skills, but would like to learn, tgm and I would be glad to help teach you.  The more help we have, the more time we have to do other cool things with mythbuntu :)

---

### Post by awaterson on 2010-06-03
> **superm1 said:**
> If you notice it breaking in the future again like this, and have the skills to fix the broken patches, that would be awesome!

If you don't have the skills, but would like to learn, tgm and I would be glad to help teach you.  The more help we have, the more time we have to do other cool things with mythbuntu :)

I have built mythtv using the old script.  Just need to get my head round the new one's.  Although currently I couldn't get access to the source file build log as this is not on the ppa site. I would love to be of any help I can in the future.

:P

---

### Post by superm1 on 2010-06-03
> **awaterson said:**
> I have built mythtv using the old script.  Just need to get my head round the new one's.  Although currently I couldn't get access to the source file build log as this is not on the ppa site. I would love to be of any help I can in the future.

:P

This should help you get started:

[http://www.mythbuntu.org/wiki/developer-cheatsheet](http://www.mythbuntu.org/wiki/developer-cheatsheet)

You can check out the various branches that way and dwelve into how the build actually happens.  If you've got a fix for a build bug, just need to write a patch and propose a merge request and assign it to the mythbuntu team to review.

---

