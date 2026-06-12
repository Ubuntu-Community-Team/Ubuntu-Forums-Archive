---
title: "Mplayer problem with ATI Radeon Mobility x1300"
date: 2006-11-16
forum: Multimedia &amp; Video
---

### Post by ribamar on 2006-11-16
Hello folks.
I have an Acer Aspire 5601, with a ATI RADEON MOBILITY X1300, with Ubuntu 6.10.
I installed Mplayer.
At the beggining he gave me the error: Error opening/initializing the selected video_out (-vo) device.

So i searched in mplayer faq site, and i understood that the current video driver "xv" wasn't the right one.
So i changed the driver to "x11", which isn't recommended since x11 does not support scaling in hardware and since scaling in software can be incredibly slow, therefore, i can't go full screen, because when I go into full screen mode I just get black borders around the image and no real scaling to fullscreen mode. 
What do i have to do to solve this problem?
When I had Ubuntu 6.06 installed i had the same problem, but i managed to solve it with the last drivers at the time, right now i have the newest drivers for 6.10 Edgy and the problem persist...

What do i have to do so i don't spend hours for solving this same problem again in a future installation? And recommending other software would no do the trick, since i like very much mplayer, i used it very well in 6.06.

Help please, I'm desperate... ](*,)

---

### Post by got_nix on 2006-11-16
kinda in the same baot with you need my mplayer working like now..

---

### Post by infoseeker on 2006-11-19
Same problem here.
I have nvidia 6600GT. Mplayer plays normally at command line tho.  Tried reinstalling, drivers, plugins, everything.  I have the same problem with 2 separate installations - one Ubuntu and the other Kubuntu (on 2 separate partitions). The correct installation procedure was followed under here ----> [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
Fortunately for me Kaffeine works normally.

EDIT.  Plays video and audio now, with an error, but plays. Something about 'afm=mp3lib'. Had to select 'x11' in 'video' section under 'preferences'.

---

