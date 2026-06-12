---
title: "Screen Saver while watching movies."
date: 2007-07-28
forum: Multimedia &amp; Video
---

### Post by Ultra Magnus on 2007-07-28
Hi, I'm having a few problems when playing movies, dvds etc - its all fine but a few minutes in my screen goes blank - I'm not even sure whether its a screensaver issue because it just goes black - but if a wiggle the mouse around it comes back on again - but its pretty annoying.

I'm using compiz with xorg as well - any ideas?

---

### Post by Gremlinzzz on 2007-07-28
change your movie players video to X11 if you use beryl or compiz
:guitar:

---

### Post by RomeReactor on 2007-07-28
Hi. It might be the screensaver. Go to "System->Preferences->Screensaver", uncheck **Activate screensaver when computer is idle**. Still in "Screensaver", go to "Power Management->On AC Power" and move the **Put display to sleep when inactive for** slider all the way to the right ("Never").

---

### Post by russo.mic on 2007-07-29
Hear Hear!

Feel your pain.  It's not the Gnome screen saver, it's something to do with compiz.  Unfortunatly, with some AVI files you'll get strange artifacts to put the output to X11.  And i don't think that would help anyway, as it's a beryl/compiz thing.  Anyone have any ideas?  

Russo

---

### Post by RomeReactor on 2007-07-29
If this problem happens after a few minutes of watching the video, it might be the screensaver. If it happens faster (or immediately), then it might be related to the issue **Gremlinzzz** posted, which is a known bug and can be solved according to [UbuntuGuide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_do_I_fix_black_windows_during_video_playback").

---

### Post by luisbg on 2007-07-29
What I have to do is deactivate compiz to watch a movie, and then activate it back when I've finished.

luisbg

---

### Post by luisbg on 2007-07-29
forgot to say I do it this way because X11 looses image quality when the video is rescaled and consumes a lot more of cpu.

luisbg

---

### Post by azdragon on 2007-10-23
I have the same exact problem.   If there is no mouse or keyboard movement for exactly 15 minutes the screen goes blank.  It is a huge pain when I am laying on my bed and it goes blank when I watching the movie, then I have to jump up and move the mouse.  

I did not always have this problem. I remember it starting about 2 months ago, when i was running 7.04 and beryl.   Now I am running 7.10 and compiz, but the problem is still the same.

It is acting just like a screensaver would.   And it also does it after 15 minutes when I am not running a movie, but when that happens I don't care....I actually like it.   But under screen saver I have it turned off (The box is NOT checked)   In Power management it is also set all the way to the right, to NEVER.   

Just in case you care, all my video players are set to X11.....I have a Geforce 7600 video card.   I have a Athlon Dual Core CPU with a MSI motherboard.      I also have a 22inch monitor with a strange resolution.   

So far the only solution I have found was to go to the mall and buy a 12 foot USB extention cable, and I take the mouse with me to the bed when I watch movies.   It actually made it work quite well....and I can now pause and rewind and such from the bed   :)

---

### Post by Slartibartfast on 2007-10-23
> **azdragon said:**
> 
So far the only solution I have found was to go to the mall and buy a 12 foot USB extention cable, and I take the mouse with me to the bed when I watch movies.   It actually made it work quite well....and I can now pause and rewind and such from the bed   :)

:)

I really like that solution! I have the exact same problem, but I think I'm gonna buy a USB extension cable, even if there is a fix to this problem :D

---

### Post by wild_oscar on 2007-10-24
I have the exact same problem!

For those who don't want to buy an usb extension cable, what is the solution?

I didn't have this problem with Edgy, only with Gutsy...

---

### Post by hades_6_6_6 on 2007-10-26
Also have exactly the same problem since Gusty.

---

### Post by DasCrushinator on 2007-10-26
Have you guys tried this?

[http://ubuntuforums.org/showthread.php?t=284804](http://ubuntuforums.org/showthread.php?t=284804)

Works great for me on 7.04 and 7.10.

---

### Post by juamez. on 2007-11-01
> **luisbg said:**
> forgot to say I do it this way because X11 looses image quality when the video is rescaled and consumes a lot more of cpu.

luisbg
This is true in VLC player, but when you choose MPlayer with X11/Xv as your video output, the image quality remains the same when using the standard output with compiz disabled. I recently discovered it, to my joy.

---

