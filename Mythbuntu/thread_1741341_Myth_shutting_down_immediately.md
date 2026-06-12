---
title: "Myth shutting down immediately"
date: 2011-04-28
forum: Mythbuntu
---

### Post by sqeelurgle on 2011-04-28
I have a new problem on a previously running system.  WHen Myth boots up to Mythwelcome, it will shut down instantly.  The bit at the top says it will shut down in 120 seconds, but it goes down immediately.  Frustrating.  I had graphics problems a few days ago and did the dpkg restore thingy from the grub restore boot option.  Since then, a few extra errors cropped up that were due to dpkg "restoring" a few files that had been purposefully changed, but I have no clue on this one.  This problem also started a few days after the other problem seemed to be totally fixed.  Any idea where to start looking?

---

### Post by poodoopealeoaph on 2011-04-28
Honestly... I would just save the hassle of messing with this and that and just reinstall myth. I know it sounds like a not so technical answer but it is really about the only sure fire way to get things to work correctly. In most cases, if one thing messes up and you fix it, more things will mess up, then fixing those will mess up even more things.... gah..

---

### Post by sqeelurgle on 2011-04-28
Problem then is losing all the database info and recordings.  Not too keen on that.:(

---

### Post by alien878 on 2011-04-28
I'm not sure how it messed up, but if a dpkg-restore managed to mess up the backend, as mentioned earlier, there may be other problems.  For future reference, I would strongly recommend putting linux on a small partition separate from data/video files.  Then do a regular clonezilla of the linux partition before doing any upgrades.  I've been burned too often by mythbuntu updates.

But all that probably won't help you at the moment.  If you can get to a shell window (ex. ALT-TAB xterm), then "mythshutdown -l" should (hopefully) stop the shutdown.  Once you get that far, check the log files.  In particular, the mythbackend log file as that is where all the shutdown timeouts happen.

---

### Post by sqeelurgle on 2011-04-28
The main thing (that I can notice) that dpkg restore did is restore the ati closed source driver for my video card, which doesn't actually support my particular card (I need to use the open source driver).  Had to boot with a very dodgy (freezes the whole machine after a few minutes) nvidia card to put that right.  It also restores a file (ICEauthority or something like that) that had previously been deleted to cure a problem as per a number of fixes I found on the web.  Anyway, After many attempts, I have now managed to get the system to stay booted long enough to get into the myth frontend.  I intend to keep it booted now until I can get some resolution. I should be able to go back in the backend log and see what was going on.  I should also be able to hook up my external drive and back up recordings and database and reinstall if needed.  I'll get back if I find anything useful in a log.

Thanks

---

### Post by sqeelurgle on 2011-04-28
OK, there are no glaring error messages in the backend log that I can see, but the date is off.  It looks like when it boots normally, the date is all correct.  When it has booted incorrectly, the date in the log has the correct day and month, but the year is 1980.  ANy ideas?

---

### Post by alien878 on 2011-04-29
If myth shuts down the server, you should see something like the following in the backend log:```
2011-04-28 10:00:29.938 CheckShutdownServer returned - OK to shutdown
2011-04-28 10:00:29.973 Running the command to shutdown this computer :-
                                                /usr/bin/mythshutdown --shutdown
```If you don't see anything like that, you might check syslog around the shutdown time to see if there is anything interesting as the shutdown probably wasn't related to myth.

The 1980 date is interesting.  That means that linux somehow lost the year (linux starts counting time January 1, 1980).  Maybe you need a new CMOS battery?  Still, I can't see how this would trigger a shutdown, but you never know....

---

### Post by sqeelurgle on 2011-04-29
I did wonder about the CMOS battery.  It's an older motherboard.  There hasn't been enough time today so far when it hasn't been in use to power it down and change the battery.  I do actually have a spare right now.  There was nothing about shutting down in the backend log at those times.  I'll check syslog as well, thanks.

---

