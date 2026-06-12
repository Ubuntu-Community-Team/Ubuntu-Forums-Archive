---
title: "External monitor all of a sudden stopped working (ati x300 // hardy heron)"
date: 2008-04-25
forum: Multimedia Software
---

### Post by kebabdylan on 2008-04-25
Not sure what happened. Had dual monitors working (compiz wasn't). Got compiz working. Yippee!

Then all of a sudden, my external monitor just stopped coming on when booting up. In the ATI Catalyst CC, the "2" monitor is greyed out.

output of xrandr -q:

Screen 0: minimum 320 x 200, current 1400 x 1050, maximum 2800 x 1050
default connected 1400x1050+0+0 0mm x 0mm
   2800x1050      60.0  
   1400x1050      50.0* 
   1280x1024      50.0  
   1152x864       50.0  
   1024x768       50.0  
   800x600        50.0  
   640x480        50.0  
   640x400        50.0  
   640x350        50.0  
   512x384        50.0  
   400x300        50.0  
   320x240        50.0  
   320x200        50.0  


output of aticonfig --query-monitor
  Connected monitors: crt1, lvds, tmds1
  Enabled monitors: lvds

I can post the xorg.conf if needed.

Anyone else have this happen? What other settings are there to look at?

---

