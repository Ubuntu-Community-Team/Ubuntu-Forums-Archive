---
title: "What is best plan for Mythbuntu migration?"
date: 2008-05-08
forum: Mythbuntu
---

### Post by CornMaster on 2008-05-08
I'm currently running MythTV on 6.06 I think or maybe 7.04.  I'm planning an upgrade to 8.04.  I mainly use this computer for PVR, but I'm planning to integrate my webserver there too.  Also, I plan to use the computer for casual web browsing when I get myself a decent TV.

So, should I install ubuntu and then install the mythbuntu package on top of this (I've tested this with a virtual machine, and it seemed to run ok) or should I install mythbuntu and then install the ubuntu desktop package?  Or should I just install Mythtv separately on Ubuntu?

To understand the timing, I plan to reinstall my PVR in a week or two, and migrate the web server over in a month or two.  Most of the sites I'm actually moving to a shared hosting package that I'll manage, but some stuff I fool with I'll be moving to the PVR.

As for my myth setup, I have a separate partition for /, /home and for my recordings.  I've tested database backups, so I shouldn't lose any data when I export the database and reimport it.  I plan to mount the partition in the same location, so that should work fine too.

Any recommendations given the setup I have and the plans I've made?  I'm hoping to take advantage of the better/easier frontend/backend configs so that I can watch on my main PC, and my eeePC.  And to gain the new features of the newest Ubuntu and Mythtv.  I think where I am now is as far as I can come on the distribution without having to compile from source.  And I'm lazy and like packages that just work. ;)

Anywho....Thanks in advance for any advice.

---

### Post by superm1 on 2008-05-08
> **CornMaster said:**
> I'm currently running MythTV on 6.06 I think or maybe 7.04.  I'm planning an upgrade to 8.04.  I mainly use this computer for PVR, but I'm planning to integrate my webserver there too.  Also, I plan to use the computer for casual web browsing when I get myself a decent TV.

So, should I install ubuntu and then install the mythbuntu package on top of this (I've tested this with a virtual machine, and it seemed to run ok) or should I install mythbuntu and then install the ubuntu desktop package?  Or should I just install Mythtv separately on Ubuntu?

To understand the timing, I plan to reinstall my PVR in a week or two, and migrate the web server over in a month or two.  Most of the sites I'm actually moving to a shared hosting package that I'll manage, but some stuff I fool with I'll be moving to the PVR.

As for my myth setup, I have a separate partition for /, /home and for my recordings.  I've tested database backups, so I shouldn't lose any data when I export the database and reimport it.  I plan to mount the partition in the same location, so that should work fine too.

Any recommendations given the setup I have and the plans I've made?  I'm hoping to take advantage of the better/easier frontend/backend configs so that I can watch on my main PC, and my eeePC.  And to gain the new features of the newest Ubuntu and Mythtv.  I think where I am now is as far as I can come on the distribution without having to compile from source.  And I'm lazy and like packages that just work. ;)

Anywho....Thanks in advance for any advice.
If you're on 6.06, dist-upgrade.  If you are on 7.04, I'd say re-install.

If you are wandering down the path of reinstall and trying to figure out add mythbuntu to ubuntu or ubuntu to mythbuntu, either way gets you the same end result.

The time necessary to do one or the other will be about the same, but you will have less configuration mythwise to do if you if you add ubuntu to mythbuntu.

---

