---
title: "Weekly Build GPG Error"
date: 2009-01-03
forum: Mythbuntu
---

### Post by endemoniada on 2009-01-03
I`ve just tried to add the weekly builds of the mythbuntu repos to my freshly installed intrepid installation, following the instructions at [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds), but on doing a "sudo apt-get update" I get the following message 
W: GPG error: [http://uk.weeklybuilds.mythbuntu.org](http://uk.weeklybuilds.mythbuntu.org) intrepid Release: The following signatures were invalid: BADSIG C1A77650EEED06D0 Mythbuntu Automated Package Builder <packages@mythbuntu.org>
W: You may want to run apt-get update to correct these problems

This is only occuring on one of my computers set up as a frontend, i get no gpg errors on my backend machine

Any Ideas on how to solve this will be greatly appreciated

---

### Post by algae105 on 2009-01-05
FWIW, I also get a GPG BADSIG error but only when updating from the uk.weeklybuilds.mythbuntu.org mirror.

As far as I know, I've changed nothing on my server that could explain this (and it used to work for me) so I assume there's a problem with the signing key used on the weekly build...

---

### Post by db260179 on 2009-01-05
> **endemoniada said:**
> I`ve just tried to add the weekly builds of the mythbuntu repos to my freshly installed intrepid installation, following the instructions at [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds), but on doing a "sudo apt-get update" I get the following message 
W: GPG error: [http://uk.weeklybuilds.mythbuntu.org](http://uk.weeklybuilds.mythbuntu.org) intrepid Release: The following signatures were invalid: BADSIG C1A77650EEED06D0 Mythbuntu Automated Package Builder <packages@mythbuntu.org>
W: You may want to run apt-get update to correct these problems

This is only occuring on one of my computers set up as a frontend, i get no gpg errors on my backend machine

Any Ideas on how to solve this will be greatly appreciated

Try my temp mirror for the time being, until this issues gets resolved.

[http://archive.mulberry.towerhamlets.sch.uk/mythbuntu/](http://archive.mulberry.towerhamlets.sch.uk/mythbuntu/) intrepid main

---

### Post by tgm4883 on 2009-01-06
Weekly MythTV builds (for -fixes) are now fixed for both the US and UK mirrors.  If these are already in your sources.list then you have nothing else to add and it should work straight away.  The GPG key error for the UK mirror has also been fixed.  -fixes will contain MythTV updates for Hardy and Intrepid, and in the future Jaunty.

Trunk/0.22 - If you wish to run trunk please note that the trunk repo address has been changed to reflect 0.22 now.  If you have been previously running trunk or have added the repo before today, you have the wrong repo and will not get trunk updates.  Please go to [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds) and add the new repo if desired.  Trunk repo will contain MythTV 0.22 updates for Hardy, Intrepid, and Jaunty.

---

