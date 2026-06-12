---
title: "switching between 2 xorg.conf files?"
date: 2007-11-21
forum: Multimedia &amp; Video
---

### Post by The_Fozz on 2007-11-21
I searched and didn't find anything specific to my issue.

I'm using twinview to run a pair of samsung 19inch LCDs, this works well enough (kind of annoyed with only one monitor having a window bar along the bottom, but haven't looked too far into this) this works good, but the computer is set-up for SLi, and I have 2 eVGA 7600GTs.  

Right now, the LCDs are set-up to one video card, and that all works, the problem comes when I go and run day of defeat (steam/valve), wine turns off my 2nd monitor, and runs just the main monitor, which is fine, but if it does that, I'd like to have SLi, since the graphics aren't all that great (choppy and edgy, even though settings are high, it was alot better when running SLi in windows)

cliff-notes:  I have 2 LCDs, 2 video cards in SLi, both monitors connected to one GPU.

How can I run normal for normal PC duties like web browsing, but switch to single monitor in SLi when I want to play games?

if it comes down to using 2 different xorg.conf files, like I think it will, can I make a script that will let me just switch to one or the other before I go to play a game, or come back from playing games and want both of my monitors.  (when changing xorg.conf, do I have to restart xserver?  doesn't that mean I have to log out, then log back in?)

thanks :D

--Justin

---

### Post by RawMustard on 2007-11-21
I don't think you can run dual monitors under sli, it's not supported at all by nvidia.  To do as you say, you would need to open your box and remove the bridge before going into dual mode.  At least that's the problem I was faced with, with my system.  Unless things have changed?

I do as you have said with my system with two xorg files for gaming, one for dualhead use and one for single gaming use, but I cannot run sli without huge reconfiguration of my system.

---

### Post by The_Fozz on 2007-11-21
From what I've seen, that is correct.  I was running SLi before I got the 2nd monitor, now the 2nd GPU is connected, but not doing anything (probably just wasting energy)  the bridge is still connected, but it doesn't show up in nvidia-settings.

I don't really wish to run the 2nd monitor when in SLi.  Trying to find if there's a way to make the 2nd head not work, and switch on SLi when I go to game, then go back to dual-head on one card when I want to do normal duties.

wait.

just checked, nvidia-settings DOES see both GPUs, GPU-0 has my 2 LCDs and GPU-1 just has thermal monitor.

I believe with my motherboard, SLi is done in BIOS, the very first SLi boards Asus had (which I have in my 2nd computer) has the selector card, but the new ones don't.  Which makes me think this may be possible some how.

thanks

--Justin

---

