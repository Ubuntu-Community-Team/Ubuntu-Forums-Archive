---
title: "VLC cannot play video but Totem can"
date: 2008-09-06
forum: Multimedia Software
---

### Post by rudenudedude on 2008-09-06
Hi all,
I installed VLC a few weeks back and it used to work perfectly. Now VLC can only play the audio of the movie file (video is gone). Totem still seems to play perfectly fine.

I launched VLC from the terminal; played a file and these are the errors I got:
[PHP]
VLC media player 0.8.6e Janus
[00000344] motiondetect video output error: Failed to open description file motiondetect
[00000344] main video output error: no suitable vout module
[00000344] main video output error: cannot delete object (344, (null)) with children
[00000341] motionblur video output error: cannot open vout, aborting
[00000341] main video output error: video output creation failed
[00000341] main video output error: cannot delete object (341, (null)) with children
[00000306] main decoder error: failed to create video output
[/PHP]

PS: I suspect this happened after I played around with Advanced Desktop Effects Settings

Please help me out; thanks

---

### Post by rudenudedude on 2008-09-07
Problem solved. After countless hours of fruitless googling for a solution, I found the solution to this problem by accident. So for those who have this problem, here's what I did:

1a) Go to Settings > Preferences > Video > Filters
1b) uncheck motion blue filter and motion detect video filter
2a) Then go to Output Modules; check Advanced Options at the bottom-right of the window.
2b) Then select X11 Video Output for the Video Output Module
3) Save

---

### Post by Portable_Jim on 2009-01-01
> **rudenudedude said:**
> Problem solved. After countless hours of fruitless googling for a solution, I found the solution to this problem by accident. So for those who have this problem, here's what I did:

1a) Go to Settings > Preferences > Video > Filters
1b) uncheck motion blue filter and motion detect video filter
2a) Then go to Output Modules; check Advanced Options at the bottom-right of the window.
2b) Then select X11 Video Output for the Video Output Module
3) Save
Thanks

---

### Post by mike_perth on 2011-08-09
> **rudenudedude said:**
> Problem solved. After countless hours of fruitless googling for a solution, I found the solution to this problem by accident. So for those who have this problem, here's what I did:

1a) Go to Settings > Preferences > Video > Filters
1b) uncheck motion blue filter and motion detect video filter
2a) Then go to Output Modules; check Advanced Options at the bottom-right of the window.
2b) Then select X11 Video Output for the Video Output Module
3) Save

dude, i almost love you for that fix. for months i've been battling VLC (wouldn't show video, wouldn't go fullscreen, etc etc) and now all is well!!

---

### Post by SoftHacker on 2011-11-19
dude you rock :guitar:

this fixed it
vlc can play video again!!!

(also works for openSUSE)

---

