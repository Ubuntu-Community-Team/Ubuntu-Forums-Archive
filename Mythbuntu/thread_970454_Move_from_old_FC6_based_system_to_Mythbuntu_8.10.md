---
title: "Move from old FC6 based system to Mythbuntu 8.10"
date: 2008-11-04
forum: Mythbuntu
---

### Post by theltne on 2008-11-04
Hello all,

I have a setup with separate BE/FE which is based on FC6. The system has been running 99.9% stable since it was installed but still - I feel it is time to switch to a more up-to-date system.

Since the system was first installed I have increased the storage several times. The system itself is installed on an IDE drive. The recordings are stored on a 1TB (2x500GB SATA) lvm. I also have a 2TB (2x1TB SATA) lvm which stores my other media files.
Further, there is a single PVR-350 handling the cable tv signal.

I am pretty sure I can figure out the installation on both the BE and the FE and even how to replace the PVR-350 with a PVR-500 which has been on the shelf for too long...

However, I am a bit uncertain about moving the two lvms and in particular the recordings database. AFAIK, the database layout has changed (correct me if I'm wrong) and I guess that will cause some problems. :confused:

All and any input appreciated!

---

### Post by mrand on 2008-11-04
> **theltne said:**
> Hello all,

I have a setup with separate BE/FE which is based on FC6. The system has been running 99.9% stable since it was installed but still - I feel it is time to switch to a more up-to-date system.

Since the system was first installed I have increased the storage several times. The system itself is installed on an IDE drive. The recordings are stored on a 1TB (2x500GB SATA) lvm. I also have a 2TB (2x1TB SATA) lvm which stores my other media files.
Further, there is a single PVR-350 handling the cable tv signal.

I am pretty sure I can figure out the installation on both the BE and the FE and even how to replace the PVR-350 with a PVR-500 which has been on the shelf for too long...

However, I am a bit uncertain about moving the two lvms and in particular the recordings database. AFAIK, the database layout has changed (correct me if I'm wrong) and I guess that will cause some problems. :confused:

All and any input appreciated!
Can you be more specific - what do you mean when you say "database layout has changed"?  If you aren't running 0.21 (you didn't say what version you are running), then yes, the database has changed from previous versions, but that doesn't matter much because MythTv auto-upgrades databases (mythtv-setup is what actually does it, if my memory serves correctly) .

My biggest concern would be that paths for various directories and device names are going to be different between FC and Ubuntu, but I believe others have made this transition, so it must be possible - I just don't know what is involve in it.

Good luck,

[INDENT]Marc[/INDENT]

---

### Post by theltne on 2008-11-05
> **mrand said:**
> Can you be more specific - what do you mean when you say "database layout has changed"?  If you aren't running 0.21 (you didn't say what version you are running), then yes, the database has changed from previous versions, but that doesn't matter much because MythTv auto-upgrades databases (mythtv-setup is what actually does it, if my memory serves correctly) .

My biggest concern would be that paths for various directories and device names are going to be different between FC and Ubuntu, but I believe others have made this transition, so it must be possible - I just don't know what is involve in it.

Good luck,

[INDENT]Marc[/INDENT]

Ah - yes - I did not specify that I am running 0.20. Sorry about that.

I believe i read it somewhere a while back that due to changes in the database there are some careful tinkering involved when upgrading from a 0.20 system to a 0.21 system. That's all I know.
Do you have some more info (url?) on that auto-upgrade you mention? 

[INDENT]Torbjørn[/INDENT]

---

### Post by mrand on 2008-11-05
> **theltne said:**
> Ah - yes - I did not specify that I am running 0.20. Sorry about that.

I believe i read it somewhere a while back that due to changes in the database there are some careful tinkering involved when upgrading from a 0.20 system to a 0.21 system. That's all I know.
Do you have some more info (url?) on that auto-upgrade you mention? 

[INDENT]Torbjørn[/INDENT]
[http://www.mythtv.org/docs/mythtv-HOWTO-1.html#ss1.3](http://www.mythtv.org/docs/mythtv-HOWTO-1.html#ss1.3) explicitly states it.  If you search any of the mailing lists or forums, it is referred to frequently.  I believe mythbackend may do it as well, but most people seem to launch mythsetup.

[INDENT]   Marc[/INDENT]

---

