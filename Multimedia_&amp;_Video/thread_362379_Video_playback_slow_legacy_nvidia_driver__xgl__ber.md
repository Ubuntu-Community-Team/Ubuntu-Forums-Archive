---
title: "Video playback slow: legacy nvidia driver / xgl / beryl"
date: 2007-02-15
forum: Multimedia &amp; Video
---

### Post by Tyr_7BE on 2007-02-15
Hello all

I have an old GeForce II MMX (I think that's what it's called).  It's one of the cards supported by nvidia's legacy driver.  A while back when XGL was young and fresh I tried running compiz with XGL on this card and everything worked fine, except for video output.  Whenever I played a video, the CPU would spike to 100, and if I fullscreened the video playback would be choppy to the point of unwatchable.  Well I just threw Edgy onto the same box, followed the beryl wiki to get Beryl set up with the nvidia legacy drivers and XGL, and guess what, same issue!

-Normal Beryl works ok.  Wobbly windows / etc are a little bit sluggish, but nothing terrible.  I'm definitely getting acceleration with my wobbly windows, as CPU usage is minimal when moving windows around.
-Video playback is unusable.  The CPU goes to 100% when I try to play a video and it just can't do fullscreen.

The only way to watch videos in the past was to kill Compiz and re-enable metacity.  I'd _really_ like to not have to do this.  Can anyone recommend anything I can do to get smooth video playback?  My usual player is totem-xine, and this solution has to work with DVD playback as well as AVI/MOV/etc playback (the box I'm trying to set this up on is a media box that's been dedicated to the task of watching videos).

Ideally I'd like to have accelerated video playback (ie, so that I can engage the Beryl desktop cube plugin, and the video continues playing without a hitch, so I can get transparent video playback, etc etc...).  I've read that you can run Beryl without XGL or AIGLX if you have a card that's supported by the unified Nvidia driver.  Will buying a new card that uses the unified Nvidia driver rather than the legacy driver help my problem?  Because I'll gladly shell out a few bucks for a new card if it means accelerated playback.

Running Ubuntu 6.10, Edgy.

Thanks for any help you can offer.

---

### Post by david_2001 on 2007-02-15
One potential quick fix that solved the choppy fullscreen video problem for me:  In Beryl Settings Manager, General Options, Advanced, check "Unredirect Fullscreen Windows".

I have to admit that I don't have the same cpu usage problem.  It's definitely higher when playing a video with beryl active but the difference is less than 5%.

---

### Post by Tyr_7BE on 2007-02-15
Thanks, I'll give that a try.

Are you also running the legacy nvidia driver?  From what I've read, the new unified driver provides a few niceties over the old legacy driver (ie, you don't need XGL to run Beryl, which is a HUGE performance increase).

---

### Post by david_2001 on 2007-02-16
Ok, I admit to running AIGLX with Ubuntu nvidia-glx rather than nvidia-glx-legacy.  However, the quick fix still ought to have an effect.

---

### Post by wxnker on 2007-02-17
> One potential quick fix that solved the choppy fullscreen video problem for me: In Beryl Settings Manager, General Options, Advanced, check "Unredirect Fullscreen Windows".

Thank you so much for this tip. Fullscreen video was driving me nuts. Your suggestion improved fullscreen playback a lot.

:D

---

### Post by Tyr_7BE on 2007-02-25
Resurrecting this thread, as I'm giving it another kick at the can.

Beryl is up and running for certain.  Liquid smooth graphics, etc.

However, whenever I play a video it's choppy.  More than just choppy, it's choppy to the point of unwatchable.  This is not just in fullscreen, this is even in small windows.

I installed totem-gstreamer, and opened up gstreamer-properties and went through all the possible video output methods.  Here are the results:

-SDL output: video very choppy, audio cuts out after a second or two
-X.org output (shared memory, no xv): video choppy ("chops" are faster and come more frequent, but it's still just a series of images instead of a video), audio cuts out after a second or two
-X.org output (xv): video VERY choppy (0.5 fps or so), audio fine


This is all without fullscreen.  I've heard that using XShm (ie, X.org with no xv) will fix the issue, but so far that's not the case.  Also, when I don't have beryl on (ie, metacity is enabled when xgl is running), I get MAJOR redraw issues.  Moving a window means the window disappears from one spot on the screen and reappears at another spot, or leaves a trail as you move it that disappears when you drop it in place.  I don't know whether this problem is related, but it's another issue I'm seeing when I have xgl running.


Can anyone suggest any fixes?

XGL (latest stable)
Beryl (latest stable)
nvidia legacy driver
nvidia geforce II MMX

---

### Post by sshetye on 2007-02-25
mplayer work great, at least for ATI cards. Maybe it'll work for nVidia too.

Try the [post here]("http://ubuntuforums.org/showpost.php?p=2213333&postcount=17").

---

### Post by ppnaive on 2007-02-25
have the same problems, now fixed, great thanks

---

### Post by Tyr_7BE on 2007-02-28
I had tried mplayer in the past, to no avail.

I've managed to work around the issue.  I switched my player to VLC, and now run it in skin mode (ie, non-gtk mode) via the nonXgl script located at [http://ubuntuforums.org/showthread.php?t=176636](http://ubuntuforums.org/showthread.php?t=176636) .  It's really not an ideal solution, but it lets me watch videos just fine, looks ok, and lets me run Beryl.

Thanks all.

---

