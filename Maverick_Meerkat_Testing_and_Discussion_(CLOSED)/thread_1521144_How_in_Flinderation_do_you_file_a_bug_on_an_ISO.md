---
title: "How in Flinderation do you file a bug on an ISO?"
date: 2010-06-30
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ranch hand on 2010-06-30
I can't get a download of maverick-desktop-amd6.iso that has a md5sum that is even close to the one listed.

I can report this as a failure in the test page but a bug would be good to file.  I can not figure out how to do it at all on the launchpad bugs page.

EDIT
Can't report on the test page with out a bug number.  This is not good.

---

### Post by psyke83 on 2010-06-30
I'm not sure if they do things differently in West Virginia :P.... but this page may help: [https://wiki.ubuntu.com/Testing/ISO/Procedures](https://wiki.ubuntu.com/Testing/ISO/Procedures)

Take a look at the end of the document. If the MD5SUM doesn't match, perhaps the image wasn't uploaded to the mirror(s) correctly, and filing a bug through the tracker may be a waste of time.

Have you tried repairing the image with zsync?

---

### Post by ranch hand on 2010-06-30
I did live in West by God Virginia for some time.  Now I am in Montana.

We are testing the ISO as folks will down load it so I am not trying to fix it.  I just want a bug number.

I actually had that page but nothing really fits well.  I did, with your encouragement (I can blame it on you now), file a bug.

Now I can submit the failure report.  Thanks.

---

### Post by fedexnman on 2010-06-30
git-r-done ranch hand , nice to see some humor today thx

---

### Post by ranch hand on 2010-06-30
Must be some problems.  They are rebuilding the ISO right now.

This is why we test.  That and we are probably not quite all there.

---

### Post by VMC on 2010-06-30
> **ranch hand said:**
> I can't get a download of maverick-desktop-amd6.iso that has a md5sum that is even close to the one listed.

I can report this as a failure in the test page but a bug would be good to file.  I can not figure out how to do it at all on the launchpad bugs page.

EDIT
Can't report on the test page with out a bug number.  This is not good.

Odd, but early today I zsync'ed the latest live current, and it totally screwed up. In the mean time I had other issues. When I got around to reexamine the situation, I noticed the zsyn value changed. I re zsync'ed with the later current and it installed perfectly.

---

### Post by ranch hand on 2010-06-30
> **VMC said:**
> Odd, but early today I zsync'ed the latest live current, and it totally screwed up. In the mean time I had other issues. When I got around to reexamine the situation, I noticed the zsyn value changed. I re zsync'ed with the later current and it installed perfectly.
Interesting.

Been off line for a while, really neat electrical storm.  Shut down our provider.   City set off the tornado/severe hail siren and everything.

I am now downloading a new ISO.  I bet it works.

---

