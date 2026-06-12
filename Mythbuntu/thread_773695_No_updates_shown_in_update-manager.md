---
title: "No updates shown in update-manager"
date: 2008-04-29
forum: Mythbuntu
---

### Post by ppww on 2008-04-29
I started with a fresh install of Mythbunty 8.04RC, and ran update-manager on a regular basis to keep in sync with the rapid development cycles.  Suddenly, the availability of any updates ceased about a week ago, and update-manager now reports "current dist not found in meta-release file".

My /var/lib/update-manager directory is empty; there is no meta-release file, which is what I believe to be the problem.  Running "update-manager -c" causes a meta-release-lts file to be created, but it contains only information about 6.06LTS Dapper Drake; nothing about 8.04 Hardy Heron.

Synaptic shows my last successful batch of upgrades occurred on 4/22/2008, and included apt, apt-utils, update-manager, and update-manager-core, among others.

Any clue what the meta-release file should contain, if indeed that is the problem?

---

### Post by justanotherhack on 2008-04-29
What's in your /etc/apt/sources.list ?
I know from Debian that this usually involves a ```
apt-get dist-upgrade
``` Than again I remember that the GUI tool in Ubuntu provides a button for that.

---

### Post by superm1 on 2008-04-29
If you installed from the RC, it's just standard update/upgrade.  No need to invoke the special mode to update manager.

Just launch it like normal, have it reload the sources and hit the upgrade button.

8.04 *did* just get released, so it's normal for a lot of the updates to stop due to the archive freezing.

---

### Post by ppww on 2008-04-30
Thanks, superm1.  I was worried because all the package information files that scrolled by as update-manager checked were reported to be 0 bytes.  I just tried again, and a few of them are now several hundred kbytes, so maybe there's no problem after all.  I was accustomed to seeing many megabytes per day of updates in the last month, and it's good to know that things should be more stable now, post-release.

---

### Post by superm1 on 2008-05-01
You'll see some things trickle in here and there from the -updates repo, but probably not for a few weeks.

however, if you turn on backports, you may see more activity there soon too.

---

