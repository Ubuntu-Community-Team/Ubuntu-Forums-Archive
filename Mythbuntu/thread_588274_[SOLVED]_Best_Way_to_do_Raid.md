---
title: "[SOLVED] Best Way to do Raid?"
date: 2007-10-23
forum: Mythbuntu
---

### Post by uopjohnson on 2007-10-23
I'm really excited about migrating to mythbuntu, but I'm not sure what the best way is to set up raid for my recording drives. 
My current setup is 7.04 using the alternate install CD which lets me do raid easily.  Is there an alternate install CD for mythbuntu?  Should I just do a regular 7.10 setup and convert to mythbuntu?  I don't want to end up with a mixed system which is a paid to update correctly.
Is the best way to just do a standard mythbuntu install onto the non-raid system drive and then to set up the array once I get running?
Any info will help, thanks in advance,

---

### Post by tgm4883 on 2007-10-23
> **uopjohnson said:**
> I'm really excited about migrating to mythbuntu, but I'm not sure what the best way is to set up raid for my recording drives. 
My current setup is 7.04 using the alternate install CD which lets me do raid easily.  Is there an alternate install CD for mythbuntu?  Should I just do a regular 7.10 setup and convert to mythbuntu?  I don't want to end up with a mixed system which is a paid to update correctly.
Is the best way to just do a standard mythbuntu install onto the non-raid system drive and then to set up the array once I get running?
Any info will help, thanks in advance,

AFAIK, the best way to setup a RAID system is to use the Ubuntu Alternate CD and install a command line system.  Setup the RAID, then do 
apt-get install mythbuntu-desktop

That should get you where you want to be.

---

