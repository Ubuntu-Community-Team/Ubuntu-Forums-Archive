---
title: "Temporary move (TV guide setup)"
date: 2009-10-08
forum: Mythbuntu
---

### Post by Caps18 on 2009-10-08
I am going on a trip for 4 weeks and am thinking of taking my Mythbuntu computer with me.  I will have a lot of off time to catch up on previous TV shows I've recorded.  

The question is, is it easy to change the channels to the correct local ones?  Is it easy to change them back when I get home?  How did I do this when I first set this machine up almost 2 years ago?

Does it take long for Schedules Direct to make the changes (or is it done right away)?  And if the hotel room has basic cable, should I even think about hooking it up and messing with adding cable channels to the guide?  I've never tried using analog cable with the pchd-5500 card that I have.

Any advice would be helpful.  Thanks!

---

### Post by Lepy on 2009-10-08
If you want to take the computer with you and try to snag some local channels, this is what I would do.

I don't use Schedules Direct, but I assume you can call the hotel and ask what service they provide, or look up the zip/region on SD to better plan what you might do.

If you hook into the basic cable, I would open the backend configuration and create a new video source called Hotel (option 3). Then input the tuner connection(s) you will use to that source, scan for channels, and then add the guide source (option 4).

From mythweb, you should go to Config -> TV -> Channel Info and uncheck visible on all of your old channels. Now your guide should only show the local hotel channels. Once you get home, you can just reverse the process and delete the Hotel video source. 

However, if you have a lot of channels, unchecking the visible ones may take a lot of time and I don't think this will stop the database from using your recording schedule for your old channels.

---

