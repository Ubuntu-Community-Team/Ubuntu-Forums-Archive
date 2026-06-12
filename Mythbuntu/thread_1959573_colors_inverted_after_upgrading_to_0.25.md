---
title: "colors inverted after upgrading to 0.25"
date: 2012-04-16
forum: Mythbuntu
---

### Post by sfp-a7x on 2012-04-16
I just upgraded my MythTV installation from 0.24 to 0.25 (using the Mythbuntu repos).  Now my colors are inverted (blues are red, reds are blue).  If I change the hue to 0, then it looks normal but the colors should look normal at 50.  Any ideas?

Thanks!

---

### Post by dheianevans on 2012-04-16
see this post on the mailing list [http://www.gossamer-threads.com/lists/mythtv/users/513602?do=post_view_threaded#513602](http://www.gossamer-threads.com/lists/mythtv/users/513602?do=post_view_threaded#513602)

---

### Post by sfp-a7x on 2012-04-16
Nice, that's good news.  Thanks for the link!

---

### Post by sfp-a7x on 2012-04-16
For reference, this appears to be the commit that was referenced in the mailing list:  [https://github.com/MythTV/mythtv/commit/b2657a1a3f8aa7210885a9699b620634e4043363](https://github.com/MythTV/mythtv/commit/b2657a1a3f8aa7210885a9699b620634e4043363)

---

### Post by mebu99 on 2012-05-15
I am having the same issue.  Where do I go to adjust the hue?

---

### Post by nickrout on 2012-05-15
> **mebu99 said:**
> I am having the same issue.  Where do I go to adjust the hue?

You don't, you upgrade to a version with the fix!

---

### Post by mebu99 on 2012-05-15
I thought 0.25 was the newest version.  If I'm wrong please link the newest version so I may download it.

Currently I am using  12.04 Ubuntu and 0.25 mythtv from the mythbuntu web-site.

---

### Post by nickrout on 2012-05-15
[http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos)

---

### Post by tgm4883 on 2012-05-15
It's worth noting that builds were disabled for the last few days while we waited for load on LaunchPad to die down. I've reenabled it today and you should see new builds in the next few hours.

---

