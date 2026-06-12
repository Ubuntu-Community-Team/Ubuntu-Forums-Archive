---
title: "Backend collapsing after database import 0.24 to 0.25"
date: 2013-03-02
forum: Mythbuntu
---

### Post by ceejay on 2013-03-02
This is a bit odd, and I'm a bit lost, and some pointers would be appreciated...

I have been running Mythtv for some time on Ubuntu 11.04 + 0.24-fixes, separate front end & backend machines. As 11.04 is no longer supported, I thought I'd go to 12.04 LTS and generally upgrade stuff... I've been at this for weeks and it's driving me nuts! I've fixed most of the issues but...

I've set up separate partitions on both front and backend machines for the "new" build, so that I can take my time to get it right and revert to "old" in the evening when we actually want to record and watch stuff. The front end I did as a fresh install - 12.04 + 0.25-fixes, the backend as an upgrade to a copy of the old partition.

As a fresh install, it all works well. I have set up the cards and channels, and i can use everything more or less as I expect, stressing the system by doing lots of recordings, starting and stopping, everything I can think of - all is fine.

However, I naturally want to import all of my old recordings into the new world - the file storage system is set up in both "new" and "old" root partitions so it appears as the same path in each. So I do a database export with mythconverg_export.pl in the old system: reboot into the new one and then do mythconverg_restore.pl --drop_database --create_database.

This appears to work fine: when i start the backend, it asks if I want to upgrade the database, I say yes, it does, and for a while everyhting appears to work. I can see all of my old recordings, and I can set new ones, watch Live TV, everything. For a while...

Then things start to go wrong. First, an attempt to watch live TV fails (error opening jump file?). Then, an attempt to access mythweb from another box (working fine a little while ago) results in interminable waits for anything, even though the backend box is not very busy at all. I go into the backendsetup utility, it asks me if I want to shutdown the backend, I say yes ... but the backend fails to die. So when I exit and start up again, I have two backend processes running on the same box, which can't be good. The only way I can stop these processes is with a "sudo kill -9 ..."

Can anyone give me some clues as to where I should be looking?

I was hoping not to have to move on to 0.26 as the change to UTC internally means that I would have to rework some batch jobs and I'd rather not, though if someone can convince me that this is really necessary then I suppose I could.

It just seems really odd that it should work for a while before falling apart...

TIA.

---

### Post by newlinux on 2013-03-04
I'm on 12.04 with mythtv .25, and it is using db data that is upgraded from .24. FWIW, I experienced the same slow problem with mythweb and some other problems and they were all caused by the backend not properly dying, and having two going. When I experience this problems however, killing the backend via the kill command and then starting it with the service command usually fixes all my problems. Not sure why .25 doesn't properly die or stop when issue a service stop command, but that has been the culprite of a few problems for me.  It only happens once in  blue moon for me now as the backend process is stable, but when it crashed it would never stop cleanly and I have an extra process running...

Not much help, I know. I might be able to give more help with your frontend and backend logs around the times of the error opening jump file.

---

