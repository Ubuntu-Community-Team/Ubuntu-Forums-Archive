---
title: "[SOLVED] Mythtv upgrade not working on Toshiba Laptop"
date: 2008-03-22
forum: Mythbuntu
---

### Post by jakenable on 2008-03-22
I allowed Ubuntu to update my MythTV a couple days ago.  Everything is OK on my backend/frontend setup on my office desktop.  

But my old toshiba laptop no longer works.  

When I try to watch TV or a recording, the screen goes blank for a few seconds, then kicks me out of MythTV.  I've tried most of the playback settings in TV setup, but none has worked. I've uninstalled and reinstalled MythTV a couple times.

I read somewhere (that I can no longer find) that the recent upgrade isn't using the legacy NVidia driver correctly.  Perhaps that is my problem.

I'm not an expert Linux user, still learning.  Can someone tell me how to 

1) diagnose the true problem and/or
2) how to roll back an update to the previous version?

I had everything working so well and was quite enjoying MythTV!  I'd like to get it back.

Thank you in advance for your help.

jake

---

### Post by laga on 2008-03-22
Check /var/log/mythtv/mythfrontend.log for hints.. maybe you want to post some snippets from that file.

---

### Post by jakenable on 2008-03-22
Thank you for the suggestion.  After reviewing the log, I selected this portion which is when I tried to watch TV:

2008-03-22 20:49:26.834 Connecting to backend server: 192.168.1.155:6543 (try 1 of 5)
2008-03-22 20:49:26.845 Using protocol version 40
2008-03-22 20:49:27.019 TV: Attempting to change from None to WatchingLiveTV
2008-03-22 20:49:27.034 Using protocol version 40
2008-03-22 20:49:29.759 New DB connection, total: 3
2008-03-22 20:49:29.763 Connected to database 'mythconverg' at host: 192.168.1.155
2008-03-22 20:49:29.811 DPMS Deactivated 
2008-03-22 20:49:30.610 AFD: Opened codec 0x8360940, id(MPEG2VIDEO) type(Video)
2008-03-22 20:49:30.610 AFD: codec MP2 has 2 channels
2008-03-22 20:49:30.610 AFD: Opened codec 0x839b550, id(MP2) type(Audio)
2008-03-22 20:49:30.766 Opening audio device 'default'. ch 2(2) sr 48000
2008-03-22 20:49:30.767 Opening ALSA audio device 'default'.
/usr/bin/mythfrontend.real: symbol lookup error: /usr/lib/libmythtv-0.21.so.0: undefined symbol: glXGetProcAddress

The screen went blank for a couple seconds, then kicked me out of MythTV completely.

Jake

---

### Post by jakenable on 2008-03-23
The post below suggest to me that I'm out of luck with my problem.  Is that right?  I can't upgrade my video card.  MythTV doesn't support the driver anymore.

[URL="http://ubuntuforums.org/showthread.php?t=721957&highlight=glXGetProcAddress"]
http://ubuntuforums.org/showthread.php?t=721957&highlight=glXGetProcAddress[/URL]

How do I roll back to the prior version?  I was much happier back then...

---

### Post by laga on 2008-03-23
We've fixed that problem in Hardy. 

If you read the thread you've linked to, you'll find that someone has actually created fixed packages for Gutsy.

---

### Post by jakenable on 2008-03-23
Thank you Laga.  I did not notice the second page.  Patches fixed the problem.

---

