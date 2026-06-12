---
title: "How to: fix flickering and lagging Flashplayer FULLSCREEN"
date: 2011-11-04
forum: Multimedia Software
---

### Post by Claus7 on 2011-11-04
Hello,

there is a lot of fuss about the issue.

Specs:
i) ubuntu maverick 64 bit
ii) ati hd radeon 5670
iii) catalyst 11.10

iv) flash aid installed
v) the trick with /etc/adobe/
and the file
mms.cfg
and inside that file the option
OverrideGPUValidation=true

done.

ALL the above did NOT solve the problem I had in FULL SCREEN irrespective of the resolution, while I was trying to watch you tube videos.

So, I tried to copy and do something similar with what it was done here in KDE:
[http://www.youtube.com/watch?v=Yz31wqPpbwQ](http://www.youtube.com/watch?v=Yz31wqPpbwQ)

**by doing the following:**
System->Preferences->CompizConfig Settings Manager

Select, on the left hand side, the tab: Advanced search 
and type:
fullscreen

Then you will see some options->click the **General Options**
and **UN**check the:
**Unredirect Fullscreen Windows** option.

The difference was enormous.

Regards!

---

