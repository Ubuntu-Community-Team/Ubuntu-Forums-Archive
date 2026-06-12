---
title: "mythtv has suddenly stopped skipping forward/backwards"
date: 2009-11-07
forum: Multimedia Software
---

### Post by kcox5342 on 2009-11-07
Backend: 2X3.0Ghz AMD64 running Ubuntu 8.04 and Mythtv 0.21

Frontends:  Same as above plus a Mac PPC 1.8Ghz running 0.21-fixes


   Prior to today, this all worked fine, and there hasn't been any updates from update manager in the past day or two.

   Normally, in mythtv, skipping forwards and backwards with the arrow keys while watching video worked fine.  Tonight, it doesn't, at ALL - it makes the video stop and the frontend often needs to be force-quit (IE escape rarely works at this point).  And the weirdest thing?  It does this with 480i and 720p native MPG video, but not with video that has been transcoded to .nuv format.  That, I can still skip around in just fine.

   I did some Googling before I came here and the best Google came up with was fixing my mysql database (post #5 here: [http://ubuntuforums.org/showthread.php?t=357927&highlight=MYTHTV](http://ubuntuforums.org/showthread.php?t=357927&highlight=MYTHTV) ) but that doesn't seem to have worked.  Also, any instructions about fiddling about with mysql should be written with the novice in mind - I have phpmyadmin installed and was able to follow the directions above but it's new territory to me.

   Help!  This has instantly taken mythtv from useful to pretty useless, and it's extremely frustrating.

   Additional experimentation shows that when I play video and hit the menu button it says "No Seektable".  This at least gives me something short&sweet to Google... but I found another fix at [http://www.deprecated.net/node/29](http://www.deprecated.net/node/29) which also didn't work for me - I rebuilt a seektable for a recording but that same recording gave me a "no seektable" immediately thereafter.

   [http://regx.dgswa.com/html/node/42](http://regx.dgswa.com/html/node/42) - after running the mysql fix earlier I tried mythcommflag --rebuild -f [filename] which worked for one file.  I really hope whatever broke just caused the seektables of current recordings to go funny - I have a lot of stuff on here from prior to this flaw occurring, and I hope I don't have to run that command with *.mpg as its argument... hmm, nope, the old Star Trek's I haven't deleted seem to have their seek tables just fine.  Weird.  So, I guess what happened is sometime recently the seek table database in mysql got an error, which prevented it from storing the seektables for the new recordings but didn't mess up anything prior to the error.  Weird.  Oh well.

   By the way, I do this a lot on the forums - post a bit, fiddle a bit, update the post, fiddle some more... I want to give you all the info I have, but it does make some confusing reading sometimes, and for that I apologize.

   I have looked over the mythtv log via mythweb, and I see something which could spell the beginnings of my troubles - after the nightly news tonight, when it goes to delete the old one, mythbackend logs "Delete Recording: Error deleting recordedseek for chanid 1171 at Thu Nov 5 17:30:00 2009."  I rebuilt the seektables for three shows - the nightly news, Good Morning America, and the Breeder's Cup this afternoon.  The news works flawlessly.  GMA works fine until about 35 minutes in and then it skips to the end if I hit any forward button - but I can skip back to the 35 minute mark with a quick press of either the left or up arrows.  The horse race is all screwy - in addition to, or perhaps because of, reception troubles this afternoon.  It's a 2 hr recording which lists as being 12h59m long, and seems to work a lot like the GMA recording does - you can skip around in it up to a certain point, but that point it'll skip no further forward, although it continues to play.  Weird.  I hope any new recordings it makes tonight or tomorrow turn out with none of these issues, and I'll certainly be making a Tomboy note with the steps I took to resolve these issues thus far.  (Every mythtv server should have Tomboy installed for all those notes you need to make, your passwords, the fixes, locations of stuff, all the things you'd want to remember but know you won't.)

---

