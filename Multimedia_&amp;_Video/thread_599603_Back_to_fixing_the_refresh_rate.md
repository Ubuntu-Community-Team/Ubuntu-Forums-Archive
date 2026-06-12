---
title: "Back to fixing the refresh rate"
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by Rhapsody on 2007-11-01
I have had numerous, never-ending problems with refresh rates on Edgy and Feisty, but they're in the past now. So it's time for my new and totally different refresh rate problems on Gutsy!

The default refresh rate Kubuntu Gutsy has selected for me at 1024x768 is 60Hz, and it's horrible! My eyes are literally hurting right now, and I need my 85Hz back. Problem is, Gutsy already says I'm at 85Hz! In fact, KControl says 85Hz is all that's possible for this resolution! Yet my monitor (and my eyes) still say this is 60Hz.

Getting more strange, selecting another resolution does nothing. KDE says I'm now at the selected resolution, but absolutely nothing changes! I'm still at the same resolution!

The obvious thing now would be to tell KDE exactly what monitor I'm using (Samsung SyncMaster 793s, which my monitor actually had printed on it), which is very sensible and what I did. It resulted in a corrupted picture that I could do nothing with. So that's out.

I'm not scared about messing with xorg.conf, and I wouldn't mind installing the binary NVIDIA drivers (in fact, I'd like that because I want hardware acceleration) but I have to get 85Hz back. I can't really use the PC otherwise.

---

### Post by ddrichardson on 2007-11-01
Try [this]("http://blog.lynxworks.eu/?p=20") first.

---

### Post by Rhapsody on 2007-11-01
That didn't seem to work, and (as it was before) KDE just seems to be ignoring xorg.conf, where the relevant section says:

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection
```
In my experience, a HorizSync of 70 is enough for a VertRefresh of 85 at 1024x768, but KDE isn't interested. I'm convinced there's something in KDE's settings that needs to deleted, I've formatted and started again with the root partition **THREE TIMES** now, the problem must lie in /home.

---

### Post by ddrichardson on 2007-11-01
Create another account to confirm it.

---

### Post by Rhapsody on 2007-11-01
Ugh, problem remains even on a new account. Actually, now that I think about it, even the Kubuntu 7.10 Desktop CD had this problem. But I've still no idea how to fix it. I had it going at 1024x768@85Hz this morning, so it can be done, but I need to figure out why KDE doesn't want to let me do it.

---

### Post by mc4man on 2007-11-01
I got 1280x1024 @85hz (which is proper for my monitor) on a nvidia 7800gs in a very roundabout way. If you need I'll try to recollect, though I'm using gnome. One thing I did notice is that with a setting of " Generic Monitor" the refresh will never go above 60hz

---

### Post by Rhapsody on 2007-11-01
> **mc4man said:**
> I got 1280x1024 @85hz (which is proper for my monitor) on a nvidia 7800gs in a very roundabout way.
I've generally had to do the same thing. Ubuntu seems to be *very* bad regarding refresh rates. I'll be sure to get an LCD monitor when I next have some money. That way my eyes won't hurt so much.

> **mc4man said:**
> If you need I'll try to recollect, though I'm using gnome. One thing I did notice is that with a setting of " Generic Monitor" the refresh will never go above 60hz
But when I tried to select my actual monitor, the result was completely unusable! I don't want to go messing with my monitor settings like that again without a foolproof way of reverting it.

---

### Post by mc4man on 2007-11-01
```
I don't want to go messing with my monitor settings like that again without a foolproof way of reverting it.
```
That's why I'd be hesitant to advise to you - I  don't mind screwing up my own machine, but someone else's is different
this thread shows the final step
[http://ubuntuforums.org/showthread.php?t=583802](http://ubuntuforums.org/showthread.php?t=583802)
To get to that point I had done all the usual stuff - enable restricted drivers
 dpkg-reconfigure xserver-xorg  (using advanced for video settings)
That gave me resolutions but no good/valid refresh rates or modelines
I then forced the failsafe mode and _while in it _ went to screens and graphics to choose my monitor, (maybe another round of reconfigure next),restarted and inserted the line from above link. Now everything is good

---

### Post by whatteaux on 2007-11-02
This is a known and persistent Ubuntu bug...
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/27508](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/27508)

---

### Post by Rhapsody on 2007-11-02
So the first step either way is to enable the proprietary NVIDIA driver? That's no problem since I wanted hardware acceleration either way, but I'd like to be clear on this so I can get it right.

---

### Post by Rhapsody on 2007-11-02
I seem to have finally got it by messing with advanced settings though the "dpkg-reconfigure xserver-xorg". Hardly a user-friendly solution, but I have 85Hz for now.

---

