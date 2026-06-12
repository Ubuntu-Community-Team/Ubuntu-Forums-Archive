---
title: "Found a solution for tearing on ubuntu 7.10 with compiz-fusion enabled"
date: 2007-10-10
forum: Multimedia &amp; Video
---

### Post by toupeiro on 2007-10-10
This has been something plaguing me for a while.  I found a solution to stop the tearing, but its a bit of a double-edged blade as now it seems some of the motion is laggy and there is a bit more cpu overhead.

I pretty much knew that horizontal tearing was a vsync problem, but didn't know why anything I set in my nvidia-settings tool wasn't taking effect.  I stumbled apon the answer today.  Compiz, in all its brilliance, seems to ignore nvidia's vsync to blank options, but in the ccsm tool, under general options | display settings, there is a vsync to blank option there, which is unticked by default.  Ticking this box instantly fixed the tearing options, but created a slight overhead as now it seems the compiz is controlling vsync and not my driver / hardware.  

So.. while I am happy I fixed the tearing in my window movement.  I'm a bit bummed at the overall smoothness loss.  the movements are not as fluid with it ticked, and its almost worth having the tearing there, as I'd rather the lag-free window tearing to lagged anything. :-(  Its not horrible, but for someone picky about my systems overall performance like me, its noticeable


either way about it, for those of you dead-set on fixing a video tearing issue, this may be something to consider.  Maybe you will have better luck than I did with the performance hit.

hardware: 
Geforce 7950GT 512MB
Samsung 204B 20" LCD (DVI-I)
Drivers: restricted driver: 100.14.19

---

### Post by toupeiro on 2007-10-10
Update!!

I don't know why I decided to try this, considering the sound of it seemd like it would potentially damage hardware, but in the same ccsm tab, there is two options.  a setting to auto-control the refresh rate, and a setting to set a manual refresh rate.  Well, apparently refresh rate in the case of compiz-fusion does not seem to be the same as resolution refresh rate on your hardware.  I run 1600x1200@60  but I unticked the auto-control and blasted the refresh slidebar up to 100 and it all the movements were incredibly smooth, and no tearing!

I went back to reverify -- all of my vsync to blank settings in the nvidia-settings config tool are disabled.  So, vsync for compiz-fusion is being directly controlled by itself.

---

### Post by adzik on 2007-10-13
I think i have read just about everything I can find on this, and it's become a really irritating issue that needs addressing.  :mad:
Thanks for your suggestions toupeiro, I have tried that method myself with no success, as with everything else I have read.
The only way I was able to actually get around the tearing/shearing video problem was to use VLC media player, and use OpenGL instead of X11/XVideo outputs.  For me, this at least smoothed out the tearing, but it's a little laggy when I switch to fullscreen and back, or pause and play again.
That's the only thing I have found works to solve this issue on my machine. (issue identical running on both Feisty & Gutsy thus far)

Cheers

---

### Post by ingvildr on 2007-10-13
wow, i'd just like to say this thanks for the idea, now i have smooth as silk compiz !!!!. Turning off detection of refresh rate, putting refresh to 100 and switching vsync on in ccsm fixes all my problems woohoo!!!

---

### Post by ZeusABJ on 2007-10-15
Hmmm yeah I noticed this issue right away while trying Gutsy Gibbon RC1. Maybe they'll have it fixed in the final release, but if not I really appreciate your taking the time to document your solution here. I'll try it!

Thank you!

---

### Post by Jonothewright on 2007-12-23
I have also been looking for a solution to this for some time but have had no real success.
Nothing seems to happen when I enable the vsync in CCSM. I don't know why this isn't working for me.

Any ideas?

---

### Post by break1979 on 2007-12-25
Hi and thanks for the tip!

I am also running Compiz on Gutsy with a nVidia 6600GT and the "nvidia" driver.

I fixed this issue, that was quite a pain while playing back videos, by:

- disabling the Detect Refresh Rate auto detection

- **enabling** Sync To VBlank (this really seems to make the difference with my setup)


changing the refresh rate manually does not seem to have much effect, or at least I am not able to notice any difference...


Cheers,

Olli

---

### Post by Jonothewright on 2007-12-29
I turned off detect refresh rate, enabled sync to vblank, and tried changing the refresh rate to 100. Still tearing :confused:

I have read, in other posts, that anyone using Xgl is pretty much stuck in this situation. But I noticed that some of the earlier posts on this page have fixed this with Compiz Fusion enabled, so I still have hope that it is fixable.

At the moment I use Ubuntu for everything except watching movies. For that I boot into Vista. If I can ever fix this then Vista will be nothing more than a bad dream to me.

Thanks to everyone who has already tried to resolve this issue.

---

