---
title: "[SOLVED] Can't Manually entering the IMBD # anymore?"
date: 2008-03-21
forum: Mythbuntu
---

### Post by freymann on 2008-03-21
Here's the version of MythBuntu I'm running..

MythTV Version   : 16468
MythTV Branch    : tags/release-0-21
Library API      : 0.21.20080304-1
Network Protocol : 40

Before I did all the updates and was using 0.20, I was able to go into Settings, Manage Videos, and select an AVI file and either search for the IMDB info or manually enter the number (via keyboard or remote).

Since updating to the latest release I can no longer enter anything into the box when I'm trying to manually enter the IMDB #. That's weird!?

Is this a bug?

The automatic search feature works great though! :-)

---

### Post by digler on 2008-03-21
hi

i have a similar issue. last night i decided to install all the 47 updates that have been sitting in the tray for the past week or so. after updating myth has gone wobly. the UI changed to gant and i anything to do with VIDEO won't work. if i select watch videos in the list and try and select it nothing happens. if i try and use video manager nothing also. everything else seems to be fine except losing all my themes and video. i only have gant and 2 blue themes now (sorry can't remember the names). if i browse mythweb using a browser i notice that it has been updated and looks different also. when i look at settings for video in mythweb every section is blank. i thought updates were supposed to be tested prior to rollout! i know these issues are too vague to expect an answer but if somebody could point me in the right direction on what to do next that would be great. basically updates have screwed my install
1. themes gone'
2. anything to do with video won't open.
3. guide seems to work after 1000 presses on the remote.
4. waf factor has plummeted. I quote "the old one was so much better" old one being MCE!!!!

---

### Post by cjtinant on 2008-03-21
Im having issues with editing medadata in MythVideo.  Freeman, try sudo apt-get install mythvideo.  That should get you up and running again.

Check this thread for an answer/fix to the MythVideo issue:
[http://ubuntuforums.org/showthread.php?p=4537335](http://ubuntuforums.org/showthread.php?p=4537335)

---

### Post by freymann on 2008-03-21
> **cjtinant said:**
> Im having issues with editing medadata in MythVideo.  Freeman, try sudo apt-get install mythvideo.  That should get you up and running again.

My MythBuntu installation is working great...

but as mentioned, the only thing I can't do is manually enter the IMDB # into the box. That's my only issue. I already have mythvideo installed, so I don't know what another install command is going to accomplish.

For the other poster, there are many threads that will fix your problem, including one that I started and replied to.

Try [this thread]("http://ubuntuforums.org/showthread.php?t=725091") and do what I mention in Msg #3.

---

### Post by freymann on 2008-03-22
> **cjtinant said:**
> 
Check this thread for an answer/fix to the MythVideo issue:
[http://ubuntuforums.org/showthread.php?p=4537335](http://ubuntuforums.org/showthread.php?p=4537335)

 That was the answer.

 I can now manually enter the IMBD #.

 I had to change themes from blootube to Blue and then it worked.

---

