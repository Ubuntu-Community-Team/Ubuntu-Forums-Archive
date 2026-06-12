---
title: "Choppy 2D video w ATI, Hardy Heron, AMD 64"
date: 2008-05-03
forum: Multimedia Software
---

### Post by halberd25 on 2008-05-03
As the title says, I get choppy video with computer.  The ATI drivers are properly installed (3d rendering works flawlessly).  If I try to watch video in mplayer or kaffeine, it renders ok, but the larger I make the window, the choppier it gets.  The same also happens for 2d visual effects and 2d screensavers.  I've done a little browsing so far, but haven't turned up much.

By the way, I don't have Compiz installed and I tried the desync-video option.

Oh, and btw, if I disable the ATI drivers and restart, the video plays fine, but I have to go to a much lower resolution (I run normally at 1680x1050 and have to revert to 1024x780 (I think), so that's not an option).

---

### Post by omicrondelta on 2008-05-04
I had this problem with Gutsy on my laptop with an Intel965... Seems to be working fine in Hardy though...

The only solution I found was to uninstall xserver-xgl to watch it fullscreen or in a maximized window without dropping frames, though, I never had the fancy schmancy compiz effects, but as I said before, everything works fine with Hardy...

---

### Post by chris2000 on 2008-05-18
I had the same problem (choppy video playback after upgrade to Kubuntu 8.04), but only with Kaffeine. Frames were dropped (video_out: throwing away image with pts 356796 because it's too old).
With Kubuntu 7.10 I never experienced problems.

After not finding a solution, I downloaded the "old" Kaffeine 8.3 packages (kaffeine + kaffeine-xine) from the medibuntu server and everything works fine now. Not a clean solution but at least it works.

My system
Kubuntu 8.04 for amd64, KDE 3.5.9
latest fglrx-driver installed 1:8-4+2.6.24
MB Gigabyte GA-MA690-S2H (with ATI Radeon X1250 onboard video)

---

### Post by halberd25 on 2008-05-18
Well, on my system, all 2D video is messed up if it's large enough (even screensavers or visual effects).  When I got rid of xserver-xgl, it seems a little bit better, but still no where near close to perfect.

---

### Post by beckettwarren on 2008-07-02
Have you tried the newest restricted driver from ATI?
I was having the same problem after Gutsy working fine, but this guide:
[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)
Got everything working and looking fine.

---

### Post by halberd25 on 2008-07-02
I've been mostly using Vista right now, but next time I go on xubuntu I'll definitely give it a shot, thanks.

---

### Post by halberd25 on 2008-07-03
Ok, I'm on xubuntu now and I added those options to my xorg.conf

After I reboot, the problem is now mostly fixed.  Video that runs at full screen is perfect.  Any video that isn't full screen (except flash) now flashes at a regularly interval.  Still, I'd rather have it this way, because I'll watch my movies at full screen.

---

