---
title: "Duel Moniter problems Ubuntu 11.10"
date: 2011-12-03
forum: Multimedia Software
---

### Post by UserName17 on 2011-12-03
Hello everyone. Not sure if this is the exact place to post this but.. I recently set up a duel monitor set up with ubuntu. Im kind of a n00b with ubuntu and still use tutorials when trying new things so i used this one for the monitor set up... [http://hpclab.blogspot.com/2011/08/setting-up-dual-monitor-on-ubuntu-1104.html](http://hpclab.blogspot.com/2011/08/setting-up-dual-monitor-on-ubuntu-1104.html) ... (i have a nVidia GeForce GT 220. The set up went fine for the most part, a few flubs but got it working and was happy with it. After a restart my settings didn't come back so i redid the set up, again a few flubs later (flubs=Unity despairing) got it going, this time i clicked "Save to X configuration File" assuming thats why the settings didn't come back the last time.  Im use to unity vanishing leaving me with nothing but some desktop icons so one of those icons is "log out" haha. I logged out, logged back in and was greeted with the message:  --------------------------------------------------------------------------- COULD NOT APPLY THE STORED CONFIGURATION FOR MONITORS  None of the selected modes were compatible with the possible modes: Trying modes for CRCTC 354  CRTC 354: Trying mode 2944x1080@50hz with output at 1920x1080@51hz (pass0) CRTC 354: Trying mode 2944x1080@50hz with output at 1920x1080@51hz (pass1) ---------------------------------------------------------------------------  I clicked exit as it was my only option. Now, everything is WORKING fine, have both screen, Unity desktop and everything, but for some reason all my thumbnails are the same generic piece of paper looking thing which is making all my files very confusing. Also the drop down menus and home folder explorer (basically anything that isn't Unity) look like there from Windows NT haha. My first thought was something was disabled in Compiz so i went through and checked everything and everything seemed fine (though now my windows lag greatly when resizing) I know its really just and esthetic's issue, everything is working okay, but i was wondering if there is just a default setting i could revert back to to get my icons and everything looking normal again. Thanks for your time in advance and id be happy to add any info someone might need to help me out with this problem.

---

### Post by kmace17 on 2011-12-09
I did the exact same thing, and I'm having the same issue. I was wondering if it could have something to do with the graphics driver?

---

### Post by kmace17 on 2011-12-09
I managed to fix it. I went into CompizConfig Settings Manager. changed my profile from unity to default (my computer then crashed) after reset I changed it back to unity (I lost the menu bar, so I had to run it from the terminal: alt+ctrl+t for terminal and the command is ccsm). after a second reset, it all works... not sure what happened but there you go.

---

### Post by UserName17 on 2011-12-11
The new update took care of it for me, every thing is back to normal now. laziness pays off again! glad to hear you made out well also. srry for the slow reply too. :/

---

### Post by Macrotus on 2011-12-12
Hi

I'm having the same problem. I tried all those suggestions, but none of them helped. Everything works, but I got that message.

Ubuntu 11.10 (newest updatest, latest were installed about 2 hours ago)
NVIDIA GTX 560 Ti

BTW. That's nice! I have the taskbar on both screens! This is what I have waited for.

---

### Post by UserName17 on 2011-12-12
hmmm... I had not logged out since the last update (except on restart) and just did to see if i still got the message... I did, and everything is broken again haha... I blame you Macrotus -.-  haha jk. Ill try Kmace's fix and see if it works.   If the message still comes up, but everything is fine, id be satisfied with that tbh.

---

### Post by UserName17 on 2011-12-12
Wow... so i gave Kmace's fix a try... haha. After i switched from unity to default profiles it did freeze, restarted, went to switch back, lost mouse, restarted, went to switch back, already on "unity" profile with unity plug in disabled, enabled plug in, restarted, unity was disabled again, enabled, restarted, did all that a few more times. Finally started in unity with plug in enabled yay~. Lost desktop cube and wobbly windows and things like that, and cant re enable them the same way as before because conflict resolve is different than last time i did it, and to top it all off ICONS STILL DONT WORK! haha. Im sad now haha. Oh well, I guess ill try to fix all that now. at least i wont be bored :P haha.

---

### Post by BicyclerBoy on 2011-12-12
Could try from terminal:

unity --reset-icons
or
unity --reset

Good luck with **any** compiz extras working with unity..the extras are not guaranteed to work.

Unity is a specific compiz plugin setup, no customizing is supported.

---

### Post by Macrotus on 2011-12-13
My desktop icons are working just fine. Everything else is working also right, but I get that message always when I start the system.

---

### Post by UserName17 on 2011-12-13
Well, I got everything working again, cube, windows, all that fun stuff. Basically back at square one now, which, iv learned to accept haha. Kinda scared to try --reset now haha, but i prob will once my confidence levels return. (and yes Macrotus, having the taskbar on both screens is awesome!) haha.

---

