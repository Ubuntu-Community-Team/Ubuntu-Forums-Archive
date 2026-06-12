---
title: "Schedules Direct guide up issues"
date: 2009-08-08
forum: Mythbuntu
---

### Post by usmcstitch on 2009-08-08
Hello.  I've got a new problem.  I am missing alot of guide data while using schedules direct.  A few channels have it, most don't.

I spent 7 hours filling in all the xmltv id data by watching TV, going through each channel and cross-referencing between Zap2it and Schedules Direct lineups that i subscribed to in my account.  I say 7 hours, because the 1st time I did it, i forgot to save it, and all my changes were lost!!!

Like i said, i used SD's XMLid's and Call Signs in filling out the channels.  I did this by using MythWeb.  
I checked 4 times to make sure my Schedule Direct username and password were correct. -> It did log in and find my particular lineup
i've run the Mythfill database, multiple times.  Here, i keep seeing an 401 unauthorized error when doing the channels.  
One thing i did do different, was change the default QAM256 channel numbers to match their analogue or digital counterparts locally.  For instance, 62-6 became 49.
The weird thing is, i have some odd ball channels that are receiving guide data correctly.  Their default QAM channels to local Digital counterpart as well.
I also have ALOT of channels, including the Music Choice channels, that pulled incorrect listings (they're all Disney HD or Nickelodeon)
I was also able to find Icons for most of the channels, and most of those are correct (some are off).  Unfortuantly, while my tuner grabbed the music channels, i can't view them.  MythTV says there's an error and goes back to main menu.  What happened here?
I've posted in the SD fourms, but there are more people here that may be able to help, plus i haven't been "approved by a moderator" yet there.

Recap: 
No/Incomplete SD Data
Music Channels are recognized, but cant tune to them w/o erroring out.

Hardware:
Mythbuntu 9.04
HDHomerun, 1 tuner (0), and latest firmware
Core2Quad 6600
4 GB RAM
1x 80GB HDD (3GB /boot, 15GB /, 52 /home) 
2x 500 GB Drives for data storage (not yet fstab'd)
ATI 2400XT HDVC

I'm not sure how to go about getting you logs, so if someone can help me, i'd be very grateful.

Thx
Stitch

---

### Post by usmcstitch on 2009-08-08
Oh joy.  Just as an added bonus, i reset my input sources.  I didn't know that that kills the database.  So this will be the 3rd time i have to fill in all the info.

good times.

oh.  and no one has any ideas for me yet? :(

---

### Post by usmcstitch on 2009-08-09
**UPDATE**

I just performed a raw XML pull as described in this link: [http://forums.schedulesdirect.org/viewtopic.php?f=6&t=295]("http://forums.schedulesdirect.org/viewtopic.php?f=6&t=295").  I looked at serveral channels and i had program data.  According to that link, my SD is fine, Its something in the application.  Still need some help!

---

### Post by usmcstitch on 2009-08-09
Nevermind.  I fixed it.  Nuke it from orbit.  I just reinstalled the whole thing.
Close the thread.

---

### Post by klc5555 on 2009-08-09
> **usmcstitch said:**
> Nevermind.  I fixed it.  Nuke it from orbit.  I just reinstalled the whole thing.
Close the thread.

Just for reference: the very first time mythfilldatabase is run on a new database, it fills in all schedules data starting "now" for whatever channels it is set up for at the time.

Subsequent runs of the default "mythfilldatabase" fill in data in any added new channels beginning "tomorrow" and also the 14th day from "today". Just the way it's set up by default, to save time and bandwidth. You likely had data in your channel guide for the various added channels beginning around midnight for the day after the mythfilldatabase run, if you had scrolled ahead in the guide to look. 

When channels have been added since the very first mythfilldatabase run, to make guide data get added for "today" you have to run "mythfilldatabase  --refresh-today". To get everything over the entire two-week span of your database when new channels have been added, the command is: "mythfilldatabase --refresh-today  --refresh-all"  (Has to be both --refresh-all won't do "today" by itself).

---

