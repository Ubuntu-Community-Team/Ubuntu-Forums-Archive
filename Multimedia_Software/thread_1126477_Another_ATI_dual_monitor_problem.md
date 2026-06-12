---
title: "Another ATI dual monitor problem"
date: 2009-04-15
forum: Multimedia Software
---

### Post by xeddog on 2009-04-15
This is a long story but I will condense it as much as possible.  I'll start by not giving a blow-by-blow of the prior 3 days of trying to get this working.  Anyway, I installed the ATI 9.3 drivers on my Intrepid 32-bit system with ATI Radeon 9600 graphics card.  That seemed to work on on the umteenth try and I was finally able to get my system running again.  Problem is that it came up with the dual monitors mirrored.  I used the CCC to reconfigure the monitors so that I had everything arranged and configured the way I wanted them, clicked the apply button and got the prompt to reboot.  I used the system this way for a little while, but when I rebooted the system came back up with the displays mirrored again just as if the configuration never happened at all.

Now here is the part that I think is weird.  I watched the system come up and I can see where the two monitors actually start to work properly.  I get the plain background on both monitors and I can move the cursor between the two just as I should be able to do with the "bigdesk".  Then, as the system continues to come up, both of the monitors will rapidly click off and back on again and the screens are mirrored again.  WTF!!!!

I also examined the xorg.conf before making any of the configuration changes, and then again after setting up the "bigdesk", and there are no changes being applied to xorg.conf.  

So,  any ideas why my dial monitor config is not being saved?  Or perhaps someplace I can look to see why the monitors are switching back to mirrored?  Or ANYTHING?????????????????????


TIA,

xeddog

---

### Post by markbuntu on 2009-04-15
Try this, it seems to work for some people. Once you get the big desktop setup go to System/preferences/screen resolution. the screen resolution window will open, click close.

---

### Post by xeddog on 2009-04-15
Well I'll be damned.  IT WORKED!

Any idea why it works that way??

Thanks,

xeddog

---

### Post by markbuntu on 2009-04-15
Screen resolution is for gconf user settings. I would guess amdcccle defers to gconf but this only seems to happen for some cards. I never had this problem myself with my HD3650 and the ati drivers.

---

### Post by wetmonkey on 2009-04-15
Interesting..

I just posted an issue with ATI and monitor brightness ( [http://ubuntuforums.org/showthread.php?t=1126592](http://ubuntuforums.org/showthread.php?t=1126592) ) 
Does the ATI Catalyst offer color correction other than gamma?

---

