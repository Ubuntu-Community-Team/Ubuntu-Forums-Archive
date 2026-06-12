---
title: "Mythbuntu Trunk not at 0.22 level, Frontends can't connect to Backend"
date: 2008-03-19
forum: Mythbuntu
---

### Post by mocha on 2008-03-19
I recently updated my backend to the latest SVN 16557.  Apparently this version is part of the new 0.22 release of MythTV.  The problem is that now my frontend won't work because the trunk version that I get from:

"deb [http://weeklybuilds.mythbuntu.org/mythbuntu-trunk/ubuntu](http://weeklybuilds.mythbuntu.org/mythbuntu-trunk/ubuntu) gutsy multiverse universe restricted main"

isn't updated to the 0.22 version.  So when I run the frontend I get the message:

"The schema version of your existing database is newer than this version of MythTV understands. Please ensure that you have selected the proper database server or upgrade this and all other frontends and backends to the same MythTV version and revision."

I was just curious if the maintainer of the Mythbuntu trunk repository is planning to update it.  Thanks.

---

### Post by Dragonflyoh on 2008-03-19
I think am having the same problem. The error I am getting in my mythfrontend log is:
This version of MythTV requires an updated database schema. Please run mythtv-setup or mythbackend to update your database.

As always, any help is appreciated.

---

### Post by superm1 on 2008-03-19
Hi mocha,

We didn't push the build because it is supposed to be fairly broken at this point on 0.22.  I'll push it, but no guarantees if it fails currently.

---

### Post by mocha on 2008-03-20
> **superm1 said:**
> Hi mocha,

We didn't push the build because it is supposed to be fairly broken at this point on 0.22.  I'll push it, but no guarantees if it fails currently.

Oh, well I can say that it's working fine on my backend/frontend machine.  Been running it since last weekend.  Thanks.

---

### Post by laga on 2008-03-20
[http://www.gossamer-threads.com/lists/mythtv/dev/323423](http://www.gossamer-threads.com/lists/mythtv/dev/323423)

[http://www.gossamer-threads.com/lists/mythtv/dev/324093](http://www.gossamer-threads.com/lists/mythtv/dev/324093)

Stuart Morgan says:

>  If you didn't get the message earlier from Janne's post, things are about to
get unstable in trunk and it's in your interests and ours to hold off
upgrading if you aren't completely comfortable with this. If resolving issues
like compilation problems and submitting patches aren't part of your skill
set then you should wait at least a week.


---

### Post by mocha on 2008-03-21
Thanks for the links.  I didn't read every message but the gist of it seems to be that a minimum of Qt 4.3 will be needed for future 0.22 releases.  Since Qt is at 4.3 in Feisty that shouldn't pose any problems for Ubuntu users.

---

