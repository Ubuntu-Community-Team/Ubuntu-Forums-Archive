---
title: "Backend timed out on local install? help"
date: 2008-07-08
forum: Mythbuntu
---

### Post by jpdrawneek on 2008-07-08
Got a new install but using old db

db on one box

backend and frontend on another

> 
Could not connect to the master backend server -- is it running?
Is the IP address set for it in the setup program correct?


No clue why :confused:

Also network seems to be messed up.
The widget thingy does not work - so I tried to do it manually, but that seems to not work either.  I have to set it with ifconfig each time it boots.

Getting to the point of finding the old mythbuntu CDs out :(

---

### Post by pauna on 2008-07-09
That's interesting. I upgraded my Mythbuntu from 7.10 to 8.04 yesterday and had exactly the same behaviour: started the upgrade process, left for other tasks, found some time later MythTV up and querying for display language. Entered the language, MythTV entered the DB setup, which would fail with the above "could not connect" error. I thought I had done something to bork the install, but maybe this is a more common phenomenon.

After some careful investigation, I found that the upgrade was sort of half-way finished. Some packages were installed, some not. And this caused major problems. Including the fact that eth0 did not come up at boot time and it would not come up using /etc/init.d/network start.

My fixes:
- Manually brought the network up with ifconfig and route add default gw
- Made sure all packages were in fact downloaded.
- dpkg --configure -a

This did it and my Mythbuntu works fine now, although I had to tweak the new TV playback options to get jitter free playback.

---

### Post by jpdrawneek on 2008-07-11
Just about got it sorted.

I think the alternate iso image is broke - could not get it to work with that one.

Finally got it working with the desktop iso 

Need to drop the capture cards and channels to get it to work again.

Now to fix the sound...

---

