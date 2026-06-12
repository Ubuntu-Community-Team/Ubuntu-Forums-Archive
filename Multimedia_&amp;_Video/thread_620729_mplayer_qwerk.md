---
title: "mplayer qwerk"
date: 2007-11-22
forum: Multimedia &amp; Video
---

### Post by thinkt4nk on 2007-11-22
every file i run with mplayer displays off-center with a black bar at the top that pushes the actual video frame down so that a portion of it hangs below the viewer window.  when i run -fs it conforms to the bottom of my screen (after manipulating the conf file to display widescreen) but still displays a large, black, horizontal bar across the top of the view frame.  what's going on?

---

### Post by taurus on 2007-11-22
Look in Preferences to see which video you are using.  Try a difference one like xv or even x11.  Don't forget to close it first after you make a chance and then open it up again.

---

### Post by bthoward on 2007-11-23
Not that I have a solution but switching to an X11 output isn't going to help you.  You're just going to find that it gives you a native video size with a black border around it.  Then once you figure out that there is a zoom option to get it full screen you're going to find that it does this zoom in software and that the video starts to get a bit choppy if its a decent quality video.

---

### Post by thinkt4nk on 2007-11-24
no, taurus was right.  thanks a lot, man!!  i changed to opengl x11 and it works perfectly now!! :)

---

