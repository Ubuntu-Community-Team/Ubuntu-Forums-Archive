---
title: "fixes repository is screwed up"
date: 2008-04-27
forum: Mythbuntu
---

### Post by BBQNinja on 2008-04-27
When 8.04 was released:
-0.21 got pushed to the GUTSY fixes repository (I don't know if it's still there, I've upgraded to 8.04)
-NO hardy repsitory for "fixes" was created despite the updated doco on the web site


The .21 push to 7.10 was obviously accidental as it contravenes what was discussed on the myth-dev list.  However, if anyone has auto-updated they may not be able to go back now.

I'm guessing the whole thing is an automated build machine/script not being updated to create and push to a "hardy" directory.

---

### Post by laga on 2008-04-27
Huh?

> 
-0.21 got pushed to the GUTSY fixes repository (I don't know if it's still there, I've upgraded to 8.04)


> 
The .21 push to 7.10 was obviously accidental as it contravenes what was discussed on the myth-dev list. However, if anyone has auto-updated they may not be able to go back now.

No. It was intentional. I don't remember any discussion on the mythtv-dev list. Here's my announcement to mythtv-users: [http://www.gossamer-threads.com/lists/mythtv/users/330303?search_string=weekly;#330303](http://www.gossamer-threads.com/lists/mythtv/users/330303?search_string=weekly;#330303)

> 
-NO hardy repsitory for "fixes" was created despite the updated doco on the web site


The hardy builds are on the PPA, the mirrors are just outdated.

---

### Post by BBQNinja on 2008-04-27
> **laga said:**
> Huh?
No. It was intentional. I don't remember any discussion on the mythtv-dev list. Here's my announcement to mythtv-users: [http://www.gossamer-threads.com/lists/mythtv/users/330303?search_string=weekly;#330303](http://www.gossamer-threads.com/lists/mythtv/users/330303?search_string=weekly;#330303)
The hardy builds are on the PPA, the mirrors are just outdated.

To quote Mario on the dev list from March 9 2008
> 
As expected this is going to be a source of confusion.

There has to be a balance chosen.  Yes 0.21-fixes is a fixes branch, but 0.20.2
shipped with 7.10.  It's either force everyone using that branch to switch to
0.21, or let them stay on a "stable" 0.20.2.

There have been no updates to the "fixes" branch because nothing has been
committed to 0.20.2.  It seemed silly to keep pushing updates when the focus was
only on 0.21 for the last few weeks.

So here is the entire plan for 0.21+:

1) Get it in hardy (done)
2) Get it on the mythbuntu-trunk branch so that people on 0.20.2 who were using
the -fixes branch don't need to switch
3) Get an official backport into gutsy backports
4) Once this backport is active, the mythbuntu-trunk branch will start to track
trunk again
5) No more -fixes for the rest of gutsy.
6) -fixes will resume for hardy with release-0-21-fixes.

That sound sane?


and on Mar 13:
> 
The "last" build that was on gutsy will be available.  No more new ones though.



I missed the users thread due to the spammy nature of users (I only follow -dev closely).  When/how was this decided, and why did it not take into account the long discussion mario had with people on -dev ?  

Also, It'd be cool if you'd update the mythbuntu site if there's any major changes like a version upgrade out-of-release cycle. I simply assumed it was an error due to the discussion on -dev and the lack of anything on the site.


Also, not trying to be mr negative.  I appreciate all the work that has gone in, mythbuntu on 8.04 is great.

---

### Post by laga on 2008-04-27
> **BBQNinja said:**
> When/how was this decided, and why did it not take into account the long discussion mario had with people on -dev ?


It was decided a few weeks ago (after that discussion). There were a few reasons:

* The 0.21 package in gutsy-backports had some big problems (eg with Xvmc)
* I didn't want to force people to upgrade to Hardy
* It didn't take any major changes to get the packages to build on Gutsy (I still maintain MythTV builds for feisty here)

> 
Also, It'd be cool if you'd update the mythbuntu site if there's any major changes like a version upgrade out-of-release cycle.


True, I should have updated the website as well. I assumed it wasn't a problem because

* People who're using third-party repos should take a closer look if these packages are getting updated
* Many people were already using 0.21 on Gutsy, thanks to an oversight on our part which left the gutsy-backports repository enabled in /etc/apt/sources.list

> 
Also, not trying to be mr negative.  I appreciate all the work that has gone in, mythbuntu on 8.04 is great.

I'm glad you like it.

The best solution for this problem would be having separate PPAs for each major MythTV release (along with separate branches for each release for the packaging scripts). We haven't done that yet because it's a lot of work, but for the next release, it'll have to happen.

Thanks for making me do stuff properly! ;)

Regards,
laga

---

