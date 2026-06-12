---
title: "My mouse thinks it's panning the screen but it's not! (fglrx 8.28.8)"
date: 2006-08-21
forum: Multimedia &amp; Video
---

### Post by kr4z on 2006-08-21
I'm having a really strange problem when trying to use "big desktop" mode with the Radeon X300 in my thinkpad T43. I have a larger monitor at 1280x1024 connected to the VGA port and the LCD is 1024x768.

Up til now I've been running the version of fglrx that comes with dapper, but I was having problems with it crashing whenever the "Hyperspace" screensaver came on, as well as a weird distorted vertical area on my display whenever I moved the mouse into the hidden rectangle created by my un-rectangular screen.

So I've updated to fglrx 8.28.8 using the directions in [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI), using the seveas respository. Now the screensaver no longer crashes and I'm not getting the distortion, but I'm having an even stranger problem. ](*,)

This is kind of hard to describe, but on my smaller monitor, it seems like the mouse thinks it is panning the screen, but it is not. When I try to move my mouse into the hidden area under the screen, it appears as if it has been stopped at the edge (normally it just goes into the hidden area). After doing this, if I move the mouse up, the mouse will appear in one location, however the GUI will respond as if the mouse is further down.  Moving the mouse to the top of the screen, trying to go up, and then moving it back down fixes it.

It's as if the mouse is panning the screen because the resolution is bigger then it can display, however the GUI itself is not being panned. :-k 

Has anybody heard of this kind of problem? Is there a version of fglrx that doesn't do these things, or maybe some sort of workaround?

If I could find a program that could prevent the mouse cursor from trying to go off the bottom of the screen, I think that could hide the problem pretty well. Does any program like this exist?

---

