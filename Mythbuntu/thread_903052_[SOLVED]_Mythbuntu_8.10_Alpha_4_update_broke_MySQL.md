---
title: "[SOLVED] Mythbuntu 8.10 Alpha 4 update broke MySQL"
date: 2008-08-27
forum: Mythbuntu
---

### Post by Calmor on 2008-08-27
I've been running Mythbuntu Intrepid Alpha 4, since it actually works with my ATI cards as opposed to 8.04.1.  

This evening, I performed an upgrade of 74 or so programs.  After the upgrade and required reboot, MySQL fails to start.  dmesg doesn't seem to provide much help, and the mysql logs are blank.

Has anyone experienced this issue?  Is there any way to get MySQL to restart?  I've tried /etc/init.d/mysql restart, but it fails.

---

### Post by napsilan on 2008-08-27
I hate to sidetrack a bit, but how did you get your ATI card working in 8.10?  I thought that it had xorg 7.4 which the ATI drivers (as of catalyst 8.8 ) don't work with.  Did you downgrade xorg to 7.3?

On topic, are you able to start mysql using /etc/init.d/mysql start, instead of restart?  Does it give any feedback?

---

### Post by Calmor on 2008-08-28
> **napsilan said:**
> I hate to sidetrack a bit, but how did you get your ATI card working in 8.10?  I thought that it had xorg 7.4 which the ATI drivers (as of catalyst 8.8 ) don't work with.  Did you downgrade xorg to 7.3?

During the install, I just chose to use the proprietary drivers, and it worked the first time.  Oddly, the restricted drivers manager doesn't even show an option to enable any, and my xorg.conf just shows "configured device" for the card.  The ATI card in question is an onboard device, but I forget the model right now and am not near the machine.

In 8.04, I tried both the onboard and a 2600XT PCI-E card, neither of which worked with any driver I tried.  Video was too choppy with the vesa driver, and any of the fglrx drivers (from Ubuntu's to Envy's to the cutting-edge driver downloaded from ATI's site) caused severe display problems within MythTV only.  In 8.10 A4, I have occasional momentary tearing of the video, but it's quite watchable.

> On topic, are you able to start mysql using /etc/init.d/mysql start, instead of restart?  Does it give any feedback?

I'll have to give that a try this evening.  Is there a verbose method to start mysql?  

More details:

I set the system up last week and left for about 5 days.  When I returned, it was still up and running just fine.  I went to set up the Firefly remote (which now works!), but saw there were several upgrades available, some to MythTV and some to mysql.  I'd ran a few of these upgrades before and wasn't too worried.  However, now it has apparently held some of the mysql upgrades back (I can't check them in upgrade manager) and mysql doesn't start.  Backend configuration doesn't work because it can't connect to the mysql server.  

The /var/log/mysql/ directory is empty, /var/log/mysql.log and mysql.err are empty.  After I tried to restart, dmesg showed some mysql issue about not being able to read a file (debian.cnf I believe), so I changed the permissions to read access to others (it had been locked down to everyone except root).  Now it just shows that it doesn't start, but doesn't lead to any reason why.

I'd like to avoid reinstalling since I've spent quite a while getting the backend set up the way I wanted it.  I realize that it's an alpha version, though, and it's quite possible I'll have to reinstall several times until 8.10 comes out as a release version.

---

### Post by napsilan on 2008-08-28
I'm shooting in the dark here, but you could try doing "aptitude full-upgrade" and seeing if that will update the remaining packages.

---

### Post by Calmor on 2008-08-28
I might try that when I get home as well.  I did try a dist-upgrade and it wanted to remove mythbuntu-desktop and a slew of other mythbuntu-related packages, for some reason.

Needless to say, I aborted that one...

---

### Post by superm1 on 2008-08-28
There is a bit of a messy liblame transition going on.  Give it a day or so to sort out, and hopefully should be sane again.

---

### Post by Calmor on 2008-09-01
Mario - thanks for the help here and on Launchpad!

---

