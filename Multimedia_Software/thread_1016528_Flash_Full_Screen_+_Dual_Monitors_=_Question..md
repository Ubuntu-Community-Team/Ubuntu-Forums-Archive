---
title: "Flash Full Screen + Dual Monitors = Question."
date: 2008-12-20
forum: Multimedia Software
---

### Post by Roasted on 2008-12-20
I'm running a 19" wide LCD and 24" wide LCD. When I full screen a video in firefox playing on my 24", it'll full screen on the 19". Why? Can I change that somehow? I can't seem to get it to move over to the 24"...

---

### Post by dal on 2009-06-15
Might be due to the issue I encountered and mentioned in my post on this

[http://ubuntuforums.org/showthread.php?p=7458326](http://ubuntuforums.org/showthread.php?p=7458326)

thread. Basically for me flash seems to want to fullscreen on the monitor containing X's 0,0 coords, and as I have my secondary monitor set in nvidia-settings as the leftmost one, it fullscreens there instead of on my primary one. Which is fine for me, since thats what I'm after in the first place :) - just a pain that whenever I change focus to from the fullscreened flash vid (i.e. to a window on my primary monitor, or even just clicking the ubuntu applications menu) the fullscreened flash video window disappears and I'm left looking at the embedded video playing in a firefox window instead :(

Anyhow maybe switching the relative orientation of your monitors will fix this for you :)

---

### Post by Roasted on 2009-06-15
My secondary monitor is set as "Absolute +0+0." What should it be to get it to work?

---

### Post by HappyFeet on 2009-06-15
I believe it should be Absolute +1920+0

---

### Post by Roasted on 2009-06-15
I just tried that. Didn't work.

It full screens on my second monitor, but it's not centered. It's like I see the video, but in a cropped mode.

Example: I have a youtube video here of some guy performing an acoustic song. He's dead center in the frame. When I full screen it, his head is almost touching the right side of the 2nd monitor, however, in the embedded video on youtube, he's dead center in the video.

So I get full screen with both +0+0 and +1920+0, but I don't get it centered.

---

