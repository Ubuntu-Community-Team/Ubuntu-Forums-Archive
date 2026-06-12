---
title: "Xrandr s-video output + media"
date: 2007-11-08
forum: Multimedia &amp; Video
---

### Post by Salazar420 on 2007-11-08
So, after a long chronological series of searches, I finally, after seemingly ages, I came across a simple, yet truly obscured solution to my tv-out problem: xrandr. And to think, it was there all the while.

Still, though, I have my issues. Finally, after making the tv-out functionality of my Radeon 9250 work, it seems to all have been for nothing, because the very reason I was trying to get s-video output working was to play dvd's on my television.

So, for reasons unknown, when I attempt to play dvd's, I get the GUI of the program (for example: Totem Movie Player), yet where the movie should be, I get nothing but blackness, except for, of course, my computer monitor. Any suggests would be greatly appreciated. If you need information about my configurations or settings, etc, let me know. I'll be checking back. 
                                          ----XeNoUsEr

---

### Post by CarpKing on 2007-11-12
The Xv overlay can only be on one screen.  To switch it to the TV, install "gxvattr."  After enabling the screen with Xrandr, enter the following:

```
xvattr -a XV_CRTC -v 1
```

(see [http://ubuntuforums.org/showthread.p...87#post3467287](http://ubuntuforums.org/showthread.p...87#post3467287))

To switch it back, replace the 1 in that command with a 0 (I think).  If you figure out how to make it go fullscreen on that monitor alone, tell us (that's where I'm stuck).

---

### Post by Salazar420 on 2007-11-27
Thanks. I will definitely try this. Sorry about the wait for a reply, too; I've been out for a while. Anyway, will be checking back to post the results.

---

### Post by Salazar420 on 2007-11-27
GOod news: the method you had me attempt was successful. I do wonder, however, if there might be a way to have this feature enabled on both screens? Is that in any way possible, do you think?

---

### Post by rubberglove on 2007-12-01
> **Salazar420 said:**
> So, after a long chronological series of searches, I finally, after seemingly ages, I came across a simple, yet truly obscured solution to my tv-out problem: xrandr. And to think, it was there all the while.

Still, though, I have my issues. Finally, after making the tv-out functionality of my Radeon 9250 work, it seems to all have been for nothing, because the very reason I was trying to get s-video output working was to play dvd's on my television.

So, for reasons unknown, when I attempt to play dvd's, I get the GUI of the program (for example: Totem Movie Player), yet where the movie should be, I get nothing but blackness, except for, of course, my computer monitor. Any suggests would be greatly appreciated. If you need information about my configurations or settings, etc, let me know. I'll be checking back. 
                                          ----XeNoUsEr

Hi - I'm wondering if you can post your configuration/xrandr commands.
I have the same radeon 9250. I have the s-video out mostly working (I use mplayer for fullscreen viedo), but it could use some adjusting. 

For example, on the tv, the image does not go all the way to the left edge of the screen. 
I assume that it's a rate problem, but I can't seem to get it to change.

Thanks.

---

