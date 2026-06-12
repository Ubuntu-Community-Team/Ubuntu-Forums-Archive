---
title: "Black and White Video?"
date: 2008-05-24
forum: Multimedia Software
---

### Post by dalezjc on 2008-05-24
Okay, something weird is going on.  When I play my video files (.wmv, .mpg) with VLC, they play in color.  If I use any other video player, they play in black and white.  If I play with a non-VLC player FIRST, then even VLC won't play in color from then on, unless I reboot.

What's causing this and how do I fix?
thanks,
Dale

---

### Post by mc4man on 2008-05-24
first try what's here (also try the saturation) [http://ubuntuforums.org/showthread.php?t=769209&highlight=playback+black+white](http://ubuntuforums.org/showthread.php?t=769209&highlight=playback+black+white)
if that doesn't work run in terminal
```
rm -rf ~/.gconf/apps/totem/
``` then restart x (Ctrl,Alt, backspace)

if that doesn't work go system -> preferences -> multimedia systems selector -> video -> default output -> plugin -> no xv (least desirable option, hope 1 of previous 2 work)

if one of first 2 work maybe get rid of totem (gutsy) or add totem-xine and set as default totem player (hardy)

---

### Post by rampageoberon on 2008-05-24
You could also do this which doesn't need you to login again or restart X.

Stop your video, run totem and go to preferences. And for the display preferences adjust them as follows.

Brightness	32-33
Contrast	16
Saturation	8
Hue	        32-33

Where by 8 I mean set it all the way to the left and move it 8 steps to the right with the keyboard.
Restart the video now and it should be fine

---

### Post by R4f4 on 2010-02-04
> **rampageoberon said:**
> 
Stop your video, run totem and go to preferences. And for the display preferences adjust them as follows.



This works for me. I just reset "Color Balance" to defaults.
Thanks!

Note: I'm using Ubuntu 9.10 with a nvidia graphic card.

---

