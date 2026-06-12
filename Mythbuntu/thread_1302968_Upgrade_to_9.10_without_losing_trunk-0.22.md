---
title: "Upgrade to 9.10 without losing trunk-0.22?"
date: 2009-10-27
forum: Mythbuntu
---

### Post by mbobak on 2009-10-27
So, I'm currently running trunk-0.22 from US repositories on 9.04.

I was going to try the 9.10 upgrade.  So, I ran 'sudo update-manager -c -d', and it said it disabled all third party repos (which presumably includes mythbuntu-repos), which I expected.

But then it listed mythtv and mysql-server under packages that would be removed.

How can I cleanly upgrade from 9.04 -> 9.10, and still remain with my current myth install running trunk-0.22?  When 0.22 is finally released, (any day now), my desire is to stay with 0.22 when it goes prod, and not move to 0.23-trunk.

So, what do I do now, to make that upgrade clean, without losing my current mythtv config?  (I don't want to re-install mythtv after 9.10 upgrade.)

Second, how do I stay on 0.22 when it goes from trunk to release?  (Again, I'd prefer not to have to wipe and re-install.)

Thanks,

-Mark

---

### Post by jyavenard on 2009-10-27
0.22-rc1 and current trunk are compatible (by compatible I mean same database structure and same backend protocol).

so you can upgrade to 9.10 , then install trunk packages on top of it

---

### Post by mrand on 2009-10-28
> **mbobak said:**
> So, I'm currently running trunk-0.22 from US repositories on 9.04.

I was going to try the 9.10 upgrade.  So, I ran 'sudo update-manager -c -d', and it said it disabled all third party repos (which presumably includes mythbuntu-repos), which I expected.

But then it listed mythtv and mysql-server under packages that would be removed.I tried twice to reproduce this last night and was unable to.  Do you remember the exact order of how (and maybe even when) you installed Myth on your 9.04 system?

Something like:

1. Installed standard (gnome) Ubuntu 9.04
2. Added Mythbuntu-control-centre (MCC) package
3. Installed 0.21 frontend and backend in Sept 2009
4. Added US repo "auto-build" Mythbuntu and selected 0.22 (again, Sept 2009)

Or maybe you didn't install 0.21 or MCC at all, and you did:

1. Installed standard (gnome) Ubuntu 9.04
2. Added US repo "auto-build" Mythbuntu and selected 0.22 (Sept 2009)
3. Installed mythtv-backend-master and mythtv-frontend directly

There are quite a few possibilities, hence my question.

Having said all that, in reality if you go through with the upgrade to 9.10 and it removes those items, your configuration files should be untouched and you simply re-enable/re-install the applications after the upgrade is complete (via MCC/synaptic/apt-get/aptitude).

> How can I cleanly upgrade from 9.04 -> 9.10, and still remain with my current myth install running trunk-0.22?  When 0.22 is finally released, (any day now), my desire is to stay with 0.22 when it goes prod, and not move to 0.23-trunk.

So, what do I do now, to make that upgrade clean, without losing my current mythtv config?  (I don't want to re-install mythtv after 9.10 upgrade.)

Second, how do I stay on 0.22 when it goes from trunk to release?  (Again, I'd prefer not to have to wipe and re-install.)

Thanks,

-MarkThe naming choice that you've seen is unfortunate.  You will remain on 0.22 unless you specifically move over to 0.23.

   Marc

---

