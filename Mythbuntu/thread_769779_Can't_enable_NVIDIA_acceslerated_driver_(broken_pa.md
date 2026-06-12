---
title: "Can't enable NVIDIA acceslerated driver (broken packages?)"
date: 2008-04-26
forum: Mythbuntu
---

### Post by sublimnl on 2008-04-26
Hi, I installed Mythbuntu yesterday and had working video initially after the install.  Something happened while I was trying to set the proper resolution for my TV (LG 37L2CD) and now it refuses to load the NVIDIA driver through the Restricted Drivers Manager.  

When I attempt to enable the driver I get an error saying "Could not apply changes: Fix broken packages first."

I saw some people saying to do an apt-get update and apt-get upgrade to fix broken packages but that got me nowhere.  The update command goes by very quickly at 5-7 seconds.  Not sure if that seems right or not...isn't it supposed to be downloading info or checksums or something from the repository at that point?  Seems fast to me, but I'm not very experienced with Linux.  After that the upgrade command goes OK and then says 

"0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

I also tried a dist-upgrade and get the same line back.

Any ideas on how I can get the restricted driver enabled again?  MythTV is useless without it!

---

### Post by sublimnl on 2008-04-26
Forgot to mention this is on Mythbuntu 8.04

---

### Post by sublimnl on 2008-04-27
Nevermind, I figured it out.  I downloaded some scripts to get my FusionHDTV tuner cards working and they changed the sources.list for apt-get to some Australian mirrors for an old distro.  Restored the previous sources.list and everything was good after that!

---

