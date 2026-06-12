---
title: "the mystery of transcode"
date: 2007-11-07
forum: Mythbuntu
---

### Post by b4t3m4n on 2007-11-07
I have been messing with Myth since its conception.  Basically, I show up, realize how much of a pain it is to get to work right, cry that i don't have a Hauppauge, then realize transcode isn't working at all even though its supposed to be uber.

Well I broke down and finally bought a 150, and was really happy with mythbuntu.  Myth has come a long way and mythbuntu makes it a no brainer.  

Tonight I recorded my first show.  2.2 gig for 1 hour.  Everything rolled off perfectly, so I decided to just hit X and see what the defaults for transcode return.  Mythweb said the transcode job failed with status code "247".  :(

This is where things for me always make me want to give up on myth.  I have managed to get it too record in the past with my crappy tuner card, but could never get transcode to produce what I want.  I am not a dumb guy.  I would like to think I have figured out things far more complex than this, but as soon I as I start looking at the profiles for record/transcoding, I can't figure out which does what.  (why in the world are record and transcoding profiles kept in the same place :( )

I want my box to record my shows, flag (edit out if possible) the commercials, and transcode the television show down to a reasonable size, preferably using MPEG 4.  I am using the defaults on everything, its a fresh install, what do I need to do?

My tuner is a Hauppauge 150.

---

### Post by yabbadabbadont on 2007-11-07
Have you seen the following yet?

[http://ubuntuforums.org/showthread.php?t=346778](http://ubuntuforums.org/showthread.php?t=346778)

---

### Post by b4t3m4n on 2007-11-07
thanks, I will have to read through all of this :-k

I would think it would be a little simplier than this.

---

### Post by kyfehr on 2007-11-07
I had the smae problem.. what you need to do is go into the settings for your transcoders found under 

Utilities/Setup -> Setup -> TV Settings -> Recording Profiles

then select the Transcoders option and make sure that all the options listed you change the codec to MPEG4 (if you have only installed from the Mythbunut disc and not created your own codecs) 

then the transcoder worked fine for me and getting great results..

---

### Post by Weidbrewer on 2008-03-06
> **kyfehr said:**
> I had the smae problem.. what you need to do is go into the settings for your transcoders found under 

Utilities/Setup -> Setup -> TV Settings -> Recording Profiles

then select the Transcoders option and make sure that all the options listed you change the codec to MPEG4 (if you have only installed from the Mythbunut disc and not created your own codecs) 

then the transcoder worked fine for me and getting great results..

...And then what?   I've played around with the default settings, created my own profiles, etc...yet when I try to record, it doesn't give me the option of switching to anything but the default settings (Default, TV, high, low) and is still recording those HUGE .nuv files.


I'm trying to rip some VHS tapes to my hard drive, so I'm using manual record.

Suggestions?

---

### Post by volkswagner on 2008-03-06
AFAIK you will need to record MPEG2.  That is the limit of the tuner (card).  The transcode will happen after the recording and delete the original larger file.

There are cards that will record .avi but that is a whole ball of wax in itself.

---

### Post by Weidbrewer on 2008-03-06
So, you're saying that it only works with hardware encoding?

---

### Post by volkswagner on 2008-03-06
I am just saying it is a post recording task.  Weather your card has hardware encoder onboard or uses the cpu, it will be mpeg2.  You need to check the specs on the card, most will capture using mpeg2, either onboard or software.

---

