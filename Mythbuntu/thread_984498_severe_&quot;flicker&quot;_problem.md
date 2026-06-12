---
title: "severe &quot;flicker&quot; problem"
date: 2008-11-16
forum: Mythbuntu
---

### Post by nathan42 on 2008-11-16
All,

I'm a new mythTV/Mythbuntu user.  I recently got my new myth box booting, and things seem to be working quite well, except that have a strange "flicker" problem.  The screen looks fine most of the time, but whenever I move mouse over the task bar at the top of the screen the top ~80% of my screen briefly flickers whitish (like someone turned the brightness way up).  Further, if I open certain programs (such as the nvidia settings GUI or the MythTV frontent), it starts flickering very fast and constantly until I close the offending application.

I've done some googling and man-paging and couldn't find any problems quite like this.  Any thoughts on what could cause this type of issue?  Refresh rate?  HSync/VSync issues?  I do have some minor overscan problems, too, but I've read about how to compensate for that.  Could that be related?

Some system info in case it's relevant:
Mythbuntu 8.10
Onboard NVidia GeForce 8200
NVidia proprietary driver v177
Emerson 720p LCD TV connect via HDMI

Thanks in advance,
Nathan

---

### Post by nathan42 on 2008-11-19
As an update, I've resolved my flickering and overdrive issues with a custom modeline.  I think the trick was lowering the refresh rate.  According to the TVs EDID data (which I found decoded on the internet), it supports 57-63 MHz refresh rate.  The NVidia driver had picked 60 MHz, but when I lowered it to 57, it seemed to work fine.  I may try running it at 63 to see if that works as well and possibly improves the picture, but I'm quite satisfied as things are now.

Once I had a custom modeline working to adjust the refresh rate, I was also able to compensate for my minor overscan issues.

These wiki pages on modelines were especially helpful:

[http://www.mythtv.org/wiki/index.php/Working_with_Modelines](http://www.mythtv.org/wiki/index.php/Working_with_Modelines)
[http://www.mythtv.org/wiki/index.php/Modeline_Database](http://www.mythtv.org/wiki/index.php/Modeline_Database)

I will add my modeline to the collection once I get home.

---

