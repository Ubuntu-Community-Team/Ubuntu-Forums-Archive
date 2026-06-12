---
title: "Search for changes not working 10.10"
date: 2011-10-15
forum: Mythbuntu
---

### Post by chipppy on 2011-10-15
Good Evening

when I search for changes under videos nothing gets found

My setup is a little different from standard so I'll explain incase that part of the problem

It is a 8TB RAID5 system built using Xubutntu 10.10 Alt-install CD.  (yes thats right 8000GB).  I then installed mythtv from the software centre.  This is single Front/Backend machine, with no network connection.  I plan to connect to network and make it the master backend once I get the bugs sorted.

I have not changed anything from default (var/lib/mythtv/videos for storage path).
I have 50 movies (avi, vob, mp4, etc)in a folder called kids and 2 movies (vob and avi only) in the video folder. 

I went into Media library --> Watch Videos, I then press M and select search for changes.  Nothing appears.

I ripped 2 videos.  One into avi and one as perfect.  Again I went Media library --> Watch Videos, I then press M and select search for changes.  This time both of the ripped movies (only) appear and could be watched.

I checked the foler listing in Thunar and the three movies (2 ripped and 1 copied) are all in the same location (var/lib/mythtv/videos).

Any ideas what I am doing worng and how to fix???

Cheers
Chipppy

---

### Post by chipppy on 2011-10-16
Bump 
anyone?????  
any ideas???

---

### Post by azmyth on 2011-10-16
In your post, you said your path is var/lib/mythtv/videos. It should be /var/lib/mythtv/videos. Not sure if that was just a typo or if you're missing the "/" in your setup.

I'd check the permission of the videos in the folder and I'd recheck that you have the proper path in Settings->Setup->Media Settings->Video->General as /var/lib/mythtv/videos

If all this fails, do a scan for changes then tail the myth logs to see if it gives you any hints.

---

