---
title: "X11 and VLC"
date: 2008-11-25
forum: Multimedia Software
---

### Post by r6jeff on 2008-11-25
I am trying to run the user interface of VLC from my desktop on my laptop while displaying the video on my desktop's screen. The only way I have been able to accomplish this is if I run

jeff@Laptop - xhost +
jeff@Desktop - xhost +
jeff@Desktop - xterm -display jeff-laptop:0
on xterm displayed on laptop - jeff@desktop - vlc &
Then set the output display on VLC to jeff-desktop:0.


If anyone can suggest a better way I'm all ears. Using this way I have to run these commands every time I restart. If you need any more info let me know, thanks in advance!

---

