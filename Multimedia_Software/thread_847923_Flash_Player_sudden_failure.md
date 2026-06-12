---
title: "Flash Player sudden failure"
date: 2008-07-03
forum: Multimedia Software
---

### Post by thegr8brian on 2008-07-03
I have been using 64bit Hardy Heron since the beta and love it!  However just now I ran into odd yet extremely troubling issue...I am watching a youtube video (or any web based flash video for that matter), and it's buffering and playing and then suddenly it stops loading content and the video stops playing and the time tracker goes back to the beginning...at this point I can not restart the video and the only solution is to refresh the page...however to no avail...the videos seem to stop in similar places every time...I am using the nonfree firefox flash plugin from the repositories...I tried the adobe beta 10 driver that came out today and got it to play videos but I had the exact same issue(however I did notice considerably less cpu usage when watching a video)...I rolled back to a different kernel just for trial and errors sake but that was also no good...Was there any updates that may have caused this and if so how do I roll back?  Any permanent solution?

This may not seem like a major problem but it's honestly making me consider switching to my windows partition right now just to do simple web browsing...normally I only switch over for games...

Thanks,
Brian

---

### Post by thegr8brian on 2008-07-03
any help?

---

### Post by thegr8brian on 2008-07-04
anything?

---

### Post by GammaRay256 on 2008-07-04
Well, there are some compatibility issues with Flash in 64-bit.

I used 64-bit for a while, until I also ran into Flash problems (Flash applets sometimes would not load and the browser had to be restarted).  
I am now running 32-bit again and I haven't had any problems since switching back.

---

### Post by thegr8brian on 2008-07-04
I would prefer to stay in 64 bit since I have 4gb of ram and so forth...

---

### Post by lifve on 2008-07-04
same problem here, some web can't even load. but youtube, mostly works well. and yeah if it stopped it should refreshed.

---

### Post by rossdub on 2008-07-11
I'm having the same problem.  Any help would be appreciated.

---

### Post by TryMe on 2008-07-11
1. go to adobe and download Ver.9
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux")

2. extract the file libflashplayer.so 

3. place it in the '/usr/lib/flashplugin-nonfree' folder

you should be good after that. 

p.s.
oh wait your having issue with flash 64bit support not just the recent flash 10 update. Never mind.

---

### Post by TryMe on 2008-07-11
thegr8brian it looks like you already found a solution on a different thread. For everyone else take a look at [http://ubuntuforums.org/showthread.php?t=843927]("http://ubuntuforums.org/showthread.php?t=843927") post #8

---

