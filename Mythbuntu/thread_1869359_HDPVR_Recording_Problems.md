---
title: "HDPVR Recording Problems"
date: 2011-10-25
forum: Mythbuntu
---

### Post by fullmoonguru on 2011-10-25
I have had this unit working on a 10.04 Ubuntu/Myth install for a while.  I recently loaded a new setup, same configuration.  When it came time to compile the v4l driver I noticed that the Wiki instructions were new & updated to support the HDPVR without having to do the previous tweaks - yea!  But it wiped out a bunch of modules, killed LIRC, & made Myth unstable - boo!.  So I tried the old way & that didn't work either.  The old instructions don't kill the modules, but Myth doesn't record.  I can record a test file from the command line, but it's really stop action with about 3 second pauses.  During all of this I still had the old install on another partition working fine.  So I know the unit is good.

So... I decided to take myself & v4l compiling issues out of the mix & loaded Myhbuntu 11.04.  I also loaded the Mythbuntu repo's & updated everything.  The recorder was found without having to compile, but the results are exactly the same as compiling with the old instructions.  Recording in Myth fails & test video is stop action.

This is really driving me insane.  Way too much time spent.  Can anyone shed some light?

---

### Post by nickrout on 2011-10-25
> **fullmoonguru said:**
> I have had this unit working on a 10.04 Ubuntu/Myth install for a while.  I recently loaded a new setup, same configuration.  When it came time to compile the v4l driver I noticed that the Wiki instructions were new & updated to support the HDPVR without having to do the previous tweaks - yea!  But it wiped out a bunch of modules, killed LIRC, & made Myth unstable - boo!.  So I tried the old way & that didn't work either.  The old instructions don't kill the modules, but Myth doesn't record.  I can record a test file from the command line, but it's really stop action with about 3 second pauses.  During all of this I still had the old install on another partition working fine.  So I know the unit is good.

So... I decided to take myself & v4l compiling issues out of the mix & loaded Myhbuntu 11.04.  I also loaded the Mythbuntu repo's & updated everything.  The recorder was found without having to compile, but the results are exactly the same as compiling with the old instructions.  Recording in Myth fails & test video is stop action.

This is really driving me insane.  Way too much time spent.  Can anyone shed some light?

Logs?

---

### Post by fullmoonguru on 2011-10-26
Thank you for eminding me that the logs are my freind.  File permissions were not set on my channel change script.

So the setup works now with the old v4l install.  problem is that it says I shouldn't be using it.  I tried the new install again & it seems to work OK if I update after installing...except it kills LIIRC.  I think I'll try running the lirc prob. down before going back.

---

