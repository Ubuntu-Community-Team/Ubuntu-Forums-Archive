---
title: "dependency issue with mythweb 0.25 on 10.04?"
date: 2012-05-04
forum: Mythbuntu
---

### Post by anonymousdog on 2012-05-04
Hate to even suggest that there's a problem with the mytbuntu repos, but I have a broken mythweb 0.25 package on Mythbuntu 10.04 x64 using the mythbuntu repos.  The current version of mythweb, 2:0.25.0+fixes.20120504.2e2f02e-0ubuntu0mythbuntu1 (lucid), reports dependency on mythtv-common 2:0.25.0+fixes.20120504.2e2f02e-0ubuntu0mythbuntu1.  However, that version of mythtv-common is not available in the repos with a 20120503 version being most recent.  I can successfully force the install of the 20120503 mythweb package, but obviously, that's a work around at best.  Apt-get cleanup and update, dist-upgrade, etc are of no help.

Any thoughts, packaging and repo guru's?  Thanks in advance.

---

### Post by superm1 on 2012-05-04
I think you might have caught some PPA skew that happens from time to time when the amd64 builds lag the i386 builds.  It looks like the amd64 build caught up though now.

If you refresh your sources, you should be able to do the upgrade.

[https://launchpad.net/~mythbuntu/+archive/0.25/+packages](https://launchpad.net/~mythbuntu/+archive/0.25/+packages)

---

### Post by anonymousdog on 2012-05-04
> **superm1 said:**
> I think you might have caught some PPA skew that happens from time to time when the amd64 builds lag the i386 builds.  It looks like the amd64 build caught up though now.

If you refresh your sources, you should be able to do the upgrade.


Thanks, superm1!

I just came back to the terminal to try again after having dug through the PPA on the web (and not finding anything "weird"), and it's all good now!

Part of the symptomology was that about half of the packages managed by the PPA were on 20120503 releases.  Now they are all 20120504.  No amount of cache cleaning and updating would resolve the issue (on any PC).

This did persist for ~12hrs (or more), and I noted the behavior on three separate machines, one on 10.04 and two upgraded 10.04 --> 12.04...all x64.  On the upgrades, all was well until I enabled the repos, then the dependency issue.

Does that 12 hours (or more) sound right for a PPA "skew"?

Thanks again, and I'll mark this [SOLVED].:guitar:

---

### Post by tgm4883 on 2012-05-04
> **anonymousdog said:**
> Thanks, superm1!

I just came back to the terminal to try again after having dug through the PPA on the web (and not finding anything "weird"), and it's all good now!

Part of the symptomology was that about half of the packages managed by the PPA were on 20120503 releases.  Now they are all 20120504.  No amount of cache cleaning and updating would resolve the issue (on any PC).

This did persist for ~12hrs (or more), and I noted the behavior on three separate machines, one on 10.04 and two upgraded 10.04 --> 12.04...all x64.  On the upgrades, all was well until I enabled the repos, then the dependency issue.

Does that 12 hours (or more) sound right for a PPA "skew"?

Thanks again, and I'll mark this [SOLVED].:guitar:

Yea that can happen right after a release. We shouldn't put the builds on hold for a week or so until the servers get switched back over for PPAs

---

