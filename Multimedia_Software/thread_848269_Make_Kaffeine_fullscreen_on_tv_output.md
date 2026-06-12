---
title: "Make Kaffeine fullscreen on tv output"
date: 2008-07-03
forum: Multimedia Software
---

### Post by rubberglove on 2008-07-03
Just thought I'd share my solution to something that was bugging me for a while. I have S-Video working on my desktop nicely (thank you xrandr!). 

I've been running KDE for a while now, and like using kaffeine as my video player. One feature that I've been missing is the ability to make a video fullscreen on my S-video output without having to first drag it over and make it fullscreen. 

Okay, it's not a huge problem, but it is a little annoying since my TV screen is across the room from my desktop, and I'm used to the 'present movie' features present in VLC and Quicktime on my girlfriend's powerbook. 

So, I sat down and brushed up on some bash scripting (this is assigned to a hotkey):

```
#!/bin/bash
fullscreen=`dcop kaffeine kaffeine-mainwindow#1 fullScreen`
if [ "$fullscreen" != "true" ];
then
`dcop kaffeine kaffeine-mainwindow#1 move 0 0`
dcop kaffeine KaffeineIface fullscreen
else
exit 0
fi
```


This assumes that the secondary (TV) screen is located to the left of the main screen. This is probably not a shining example of master bash scripting, but it does work for me, so I thought I'd share it. If anyone has any suggestions/improvements, I'd love to hear them ;-)

note: I also have a second script that runs some xrandr commands to turn the S-Video output on and off, but I won't get into that here.

---

