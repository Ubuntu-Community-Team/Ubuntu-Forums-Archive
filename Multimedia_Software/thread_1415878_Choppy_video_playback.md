---
title: "Choppy video playback"
date: 2010-02-25
forum: Multimedia Software
---

### Post by GrdLock02 on 2010-02-25
CPU: Athlon 64 X2 5000
RAM: 4GB
Video: ATI 4850
Ubuntu 9.10

I'm running whatever the latest proprietary ATI driver from the Hardware Drivers menu.

I play my movies in VLC. Most movies play a little choppy at times. There's lines in the video, etc. I have some 1080p movies, and those play very choppy at times.

Is VLC not using any hardware acceleration from the video card? In Windows my computer plays 1080p movies silky smooth.

What should I check for or do to make video playback smoother in Ubuntu?

---

### Post by krige on 2010-03-14
I have the same problem.

In the attempt to fix it I have thoroughly followed this guide:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
but nothing has changed.

I have noticed an improvement in the video quality if I set in VLC / Preferences / Video / Output = X11, but still some break lines appear in the middle of the screen, especially in the fast scenes. 720p and 1080p movies play very choppy.

---

### Post by krige on 2010-03-23
It seems they fixed this in the latest 10.04. I have just installed it and all videos are now playing like a charm!

---

### Post by mikeljnola on 2010-03-30
I have a similar problem with my playback.  I have a AMD x2 6400 3GHz with 4GB RAM and a 8500GT.  Top shows Totem using >60% CPU.  I would use VLC but there is still that damn blue screen color problem.  

Any other problems with the beta upgrade?

---

### Post by lidex on 2010-03-30
> **mikeljnola said:**
> I have a similar problem with my playback.  I have a AMD x2 6400 3GHz with 4GB RAM and a 8500GT.  Top shows Totem using >60% CPU.  I would use VLC but there is still that damn blue screen color problem.  

Any other problems with the beta upgrade?

I wouldn't call beta an upgrade. If you want to try it download the LiveCD and install to a separate partition:
[http://www.ubuntu.com/testing]("http://www.ubuntu.com/testing")
If you're using compiz, disable it before playing videos.

---

### Post by dabby_yo on 2010-03-31
> **krige said:**
> It seems they fixed this in the latest 10.04. I have just installed it and all videos are now playing like a charm!

Are you using the closed or open drivers?

---

### Post by mikeljnola on 2010-03-31
> **lidex said:**
> I wouldn't call beta an upgrade. If you want to try it download the LiveCD and install to a separate partition:
[http://www.ubuntu.com/testing](http://www.ubuntu.com/testing)
If you're using compiz, disable it before playing videos.

Great advice.  I did "metacity --replace".  All video runs like a charm..

BTW, is there a consensus on why compiz messes up video so bad?  I know it's GPU/CPU intensive, but I figured if only a video was running and no effects were on, it wouldn't kill video playback so much.

Thanks again.

---

### Post by dabby_yo on 2010-03-31
> **mikeljnola said:**
> Great advice.  I did "metacity --replace".  All video runs like a charm..

BTW, is there a consensus on why compiz messes up video so bad?  I know it's GPU/CPU intensive, but I figured if only a video was running and no effects were on, it wouldn't kill video playback so much.

Thanks again.

Could be a vSync issue.

---

### Post by lidex on 2010-03-31
> **mikeljnola said:**
> Great advice.  I did "metacity --replace".  All video runs like a charm..

BTW, is there a consensus on why compiz messes up video so bad?  I know it's GPU/CPU intensive, but I figured if only a video was running and no effects were on, it wouldn't kill video playback so much.

Thanks again.
This works for me:
Install compizconfig-settings-manager if not already. Go to "General Options" and click the "Display Settings" tab. Uncheck "Detect Refresh Rate" and just below set the rate manually. At the bottom check "Sync to VBlank"

---

### Post by krige on 2010-03-31
> **dabby_yo said:**
> Are you using the closed or open drivers?

In some of my computers I have the closed ones, in some other the open ones. The video problem was present in all of them, and was gone in all of them after installing lucid.

---

### Post by HolidayQueen on 2010-05-05
I had to change my video output module to XVideo, though when i crop the video, it gets choppy and i have this diagonal line.

---

### Post by ghostborg on 2010-05-17
> This works for me:
Install compizconfig-settings-manager if not already. Go to "General Options" and click the "Display Settings" tab. Uncheck "Detect Refresh Rate" and just below set the rate manually. At the bottom check "Sync to VBlank"

Ubuntu 10.04 AMD64
lidex advice above worked for me.


My motherboard is a Gigabyte MA78GM-S2H .

Thanks

---

### Post by Maupertus on 2010-05-19
I can confirm this solution working for me as well. Ubuntu 10.01 AMD64, have to say that I didn't experience this problem in 9.10

---

### Post by jerome.gagnon.1 on 2010-05-20
> **lidex said:**
> This works for me:
Install compizconfig-settings-manager if not already. Go to "General Options" and click the "Display Settings" tab. Uncheck "Detect Refresh Rate" and just below set the rate manually. At the bottom check "Sync to VBlank"

MANY THANKS ! This worked for me too on my HDTV linked with DVI cable. Awesome !!! Ubuntu 10.04, wasn't getting this problem on 9.10 too. Refresh rate was set at 50 when it should be 60. idk why compiz mess around with refresh rate like this ?

---

### Post by gopinndn on 2010-05-26
> **lidex said:**
> this works for me:
Install compizconfig-settings-manager if not already. Go to "general options" and click the "display settings" tab. Uncheck "detect refresh rate" and just below set the rate manually. At the bottom check "sync to vblank"


thankyou verymuch iam trying to fix this problem but i cant,thankyou verymuch

---

