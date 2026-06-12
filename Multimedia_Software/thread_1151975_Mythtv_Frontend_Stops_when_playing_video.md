---
title: "Mythtv Frontend Stops when playing video"
date: 2009-05-07
forum: Multimedia Software
---

### Post by swingboy3 on 2009-05-07
Just upgraded to Jaunty Mythbuntu. Everything was going well until last night my backend stalled.  I don't know if that is related.  
I restarted the backend and now every time I watch a recording the frontend stops so that when the recording ends the frontend is  no longer there.  This isn't a huge problem because I just have to start the frontend again.  
I checked the frontend log and didn't see anything out of the ordinary.

---

### Post by swingboy3 on 2009-05-07
Just a bit more information.  This is the frontend log when I turn on and turn off the video.  I don't have much to compare to.  Nothing happens after the last line.  The backend log doesn't show anything at all.  I think it is missing "Changing from watchingprerecorded to none"

2009-05-07 13:44:45.851 TV: Changing from None to WatchingPreRecorded
2009-05-07 13:44:45.857 Realtime priority would require SUID as root.
greedyhdeint: size changed from 0 x 0 -> 720 x 480
2009-05-07 13:44:45.866 Video timing method: USleep with busy wait
2009-05-07 13:45:49.674 TV: Attempting to change from WatchingPreRecorded to None
Segmentation Fault


So what is a segmentation fault

---

### Post by swingboy3 on 2009-05-09
Solved!

I found this after increasing the verbosity of my log

[https://bugs.launchpad.net/mythbuntu/+bug/366002](https://bugs.launchpad.net/mythbuntu/+bug/366002)

I actually had to remove pulseaudio all together.  I am not using it so it was not a problem.

I hope this helps someone else

---

