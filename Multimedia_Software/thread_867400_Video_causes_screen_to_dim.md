---
title: "Video causes screen to dim?"
date: 2008-07-22
forum: Multimedia Software
---

### Post by wyth on 2008-07-22
Here's what's been happening: Every time I start some kind of video, no matter the program, my screen automatically dims to its lowest settings.  This happens when I fire up VLC or Totem. It happens when I see a video on Youtube.  It happens when I edit video in AviDemux.  It's constant.

I think this began after one of the recent kernel updates, but I'm not certain.  It's been happening for a while.

Any ideas what the problem might be?

[B]EDIT
[/B]This is an issue with the 2.6.24-20 kernel.  Rolling back to 2.6.24-19 takes care of the issue, but it remains for the current kernel.

---

### Post by wyth on 2008-07-24
Hey howdy.
</div>

---

### Post by Green9090 on 2008-07-24
If you go to preferences and click "Power Management," you should see an option called "Dim display when idle." If it's activated, try turning it off and see if that fixes it.

---

### Post by wyth on 2008-07-24
Okay, we're getting somewhere, thanks for the reply.

Dim while idle was already unticked, but it was ticked on for battery.  I unticked it there, and the backlight stayed the same for a video clip in Totem, but dropped again in VLC.  Different versions of the same clip (mpeg, avi) yielded the same results.  Youtube didn't dim the screen.

So this suggests maybe its a video setting in VLC.  Time to track that down.

---

### Post by wyth on 2008-08-03
Just wanted to say that I rolled back to the 2.6.24-19 kernel because I was having a series of issues with 2.6.24-20, and that roll-back took care of the screen dimming when video played.  

And the suspend/hibernate kernel panic.

And the wireless connection issues.

Something ain't right with 2.6.24-20.
</div>

---

### Post by 5of0 on 2008-09-06
I'm having this problem with just VLC.  I'm on 2.6.22-14-generic (at least that's what uname -r says).  I went through and, any video mode that actually outputs video (other than the ASCII art ones) have this problem.  So OpenGL, X11, and XVideo.  Anyone have any insight here?

---

### Post by piju on 2008-11-17
ya.
i got this problems too.
i end up with using smplayer to replace vlc

---

### Post by piju on 2008-11-17
now smplayer cause dimming too
anybody can explain how ?

---

### Post by brokenreality on 2008-11-18
I also have the same problem, I have noticed it with the youtube videos. I have new install of 8.10 and have not downloaded any videos yet so I am not sure if the problem is also with video players.

---

### Post by brokenreality on 2008-11-18
> **Green9090 said:**
> If you go to preferences and click "Power Management," you should see an option called "Dim display when idle." If it's activated, try turning it off and see if that fixes it.

This seems to help with the dimming problem, but watching youtube videos are still rough to do. The audio works perfect but the videos glich and pause a bit and its not a buffering problem or anything.

Edit: It still dims but just not as bad it starts to and stops real quick!

---

### Post by brokenreality on 2008-11-20
Bump

---

### Post by brokenreality on 2008-11-22
bump

---

### Post by brokenreality on 2008-11-23
BUMP BUMP BUMP BUMP, Yet another thread lost in the madness here. But my problem went away after I turned off the fading windows in my my compiz settings.

---

