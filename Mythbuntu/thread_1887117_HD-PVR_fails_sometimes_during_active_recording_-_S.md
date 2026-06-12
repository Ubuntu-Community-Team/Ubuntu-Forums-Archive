---
title: "HD-PVR fails sometimes during active recording - Solved?"
date: 2011-11-26
forum: Mythbuntu
---

### Post by romanyiv on 2011-11-26
I have been getting  anywhere from 3 to 9 failures a day - where a recording is going on and than fails with a "MPEGRec(/dev/video0) Error: StartEncoding failed".   I did a lot of reading but nothing really made any difference (make sure it's on a 2.0 USB bus (alone), replace power supply, etc).   I finally decided to see if it might be heat related - I took the top cover off (easy to do - 4 screws at the base) and left it off overnight.  I had one failure over the next 12 hours.  Not definitve but encouraging - so I cut a 4 inch circle opening in the top cover and mounted a "muffin" fan - drilled about a dozen 3/8 in holes in the sides for exhaust outlets - hooked up the fan to a 12VDC adapter - put everything back together and have had zero failures over the next 24 hours.   Fingers crossed at this point - if the failures comes back I'll update this thread.   The HD-PVR I'm using may be one of the first ones produced (rev D1) - I purchased it in 2007 I think (and never used until recently) - and I have saw some threads where the early ones had some heat issues.

---

### Post by romanyiv on 2011-11-27
Darn....cooling fan's not the fix.  I see quite a few of other people having these failures (and failing when it tries to starting recording - over the last several months without any resolution...I'm running the latest mythbuntu btw....

> **romanyiv said:**
> I have been getting  anywhere from 3 to 9 failures a day - where a recording is going on and than fails with a "MPEGRec(/dev/video0) Error: StartEncoding failed".   I did a lot of reading but nothing really made any difference (make sure it's on a 2.0 USB bus (alone), replace power supply, etc).   I finally decided to see if it might be heat related - I took the top cover off (easy to do - 4 screws at the base) and left it off overnight.  I had one failure over the next 12 hours.  Not definitve but encouraging - so I cut a 4 inch circle opening in the top cover and mounted a "muffin" fan - drilled about a dozen 3/8 in holes in the sides for exhaust outlets - hooked up the fan to a 12VDC adapter - put everything back together and have had zero failures over the next 24 hours.   Fingers crossed at this point - if the failures comes back I'll update this thread.   The HD-PVR I'm using may be one of the first ones produced (rev D1) - I purchased it in 2007 I think (and never used until recently) - and I have saw some threads where the early ones had some heat issues.

---

### Post by romanyiv on 2011-12-01
I think I got this finally fixed.   I'm using a Cisco 4642 set-top cable box.  I have the component output connected to my 1212 but also the HDMI connected to port 2 on my HDTV (just to allow my wife to bypass mythtv if needed).   Now with this Cisco 4642 device if it detects that the HDMI output is active it will disable component out (I noticed that early on - the HDPVR blue recording light would go out when input 2 on the TV was selected).   I have had quite a bit of failures during recordings - on average perhaps 5 during a 24 hour period - very frustrating.  At one point 2 days ago I decided to disconnect this HDMI cable to eliminate this variable - I have not had a single failure since.   I connected the HDMI back up this morning - and had a failure 30 minutes later.   I've not spent any time proving it but I think that most - if not all - of these failures occurs when the TV is off - I don't recall seeing failures watching livetv thru myth.   If so it's during this "tv-off" phase that perhaps the status of the HDMI on the 4642 becomes un-clear.  As of right now everything working very well...I have my IR script down to like .2 second delay between digits - and channel changing has been reliable.   I was very close to ditching mythtv because of this - reluctantly.  I started down the MS Media center route - got a HD Homerun prime and cable card - stood up a MMC for testing.  I'm still going to play with it but the advantages with myth (to me) is the client/server model (read cheap linux "extenders) and PIPs.  I don't do netfix or play games - if I did the MMC model would make more sense.   If I was starting from scratch the MMC model might still make more sense - given the steep learning curve that linux/mythtv involves.  
I still occasionally get a zero-byte recording - one over 2 days - but I can live with that - that's another issue.

---

### Post by nickrout on 2011-12-01
The homerun prime will work in myth.

---

### Post by romanyiv on 2011-12-01
Not with Time Warner in Charlotte NC - they set all of their channels (except the locals) as "copy once" - since Myth does not play the DRM game the HDHR prime box is not an option.  If it did you would see cable card installation requests soar.

---

### Post by nickrout on 2011-12-02
> **romanyiv said:**
> Not with Time Warner in Charlotte NC - they set all of their channels (except the locals) as "copy once" - since Myth does not play the DRM game the HDHR prime box is not an option.  If it did you would see cable card installation requests soar.

Are you telling us that there are NO other providers?

---

### Post by romanyiv on 2011-12-02
Apparently not - where I live appears to only be served by TW...

---

