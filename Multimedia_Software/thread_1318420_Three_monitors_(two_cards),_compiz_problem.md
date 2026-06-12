---
title: "Three monitors (two cards), compiz problem"
date: 2009-11-07
forum: Multimedia Software
---

### Post by slamhound on 2009-11-07
As the title suggests, I have two nvidia graphics cards and three monitors on a clean 9.10 install.  I have the nvidia 185 drivers installed and the "ultimate" setting for compiz effects.  Two of the monitors are linked with twinview on one screen, the third is on a separate Xscreen.  Everything worked fine except that initially, windows on the first (twinview) xscreen would maximize across both.  I figured out how to fix that problem by using Compiz Settings Manager to disable Compiz detecting the outputs and then setting two separate 1280x1024 outputs.  

That solution worked fine until I go to the second screen (third monitor) and try to maximize a window on the third monitor.  That would disable the settings on the first screen and any windows on the first screen would automatically maximize across both screens again.

I followed the guidelines on [this]("http://bbs.archlinux.org/viewtopic.php?id=78949") site and created a new config file for screen 1, which specified not to detect outputs and to set the output on that screen as 1280x1024.  This worked and I could maximize on any of the three monitors and they would work correctly. However, the fix does not "stick" and after a while, maximizing in the second screen screws up maximizing on the first screen.  It turns out that maximizing on that second screen actually turns off compiz altogether and I lose all effects.  I need to go back into System/Preferences/Appearance and turn effects on again to get my original settings back.

Any thoughts on how to fix this?

One other piece of information:  If I open Compiz Settings Manager from the panel on Screen 0, it has a box that allows me to select options for Screen 0 or Screen 1.  The options for Screen 0 are correct and match what I get if I use gconf-editor to edit things like whether to detect outputs and what the outputs are.  The options for Screen 1, however, do not match what I see in gconf-editor.  If I use the panel on Screen 1 to open Compiz Settings Manager, it also has options for Screen 0 and Screen 1, but neither match the settings I see when using gconf-editor.

---

### Post by slamhound on 2009-11-07
Okay, an update and hopefully a fix (this was also posted in response to another thread discussing similar issues).  

Because I was getting different information in CCSM depending on whether I opened it from screen 0 or screen 1, I tried setting them separately.  Specifically, I opened CCSM from the panel in screen 0 and set everything up for the two twinview monitors (the important ones being "do not detect outputs" and setting output to be "1280x1024+0+0 and 1280x1024+1024+0").  Then I opened CCSM from the panel in screen 1 and set the settings for screen 1 (again, "do not detect outputs" and setting the correct output values for the one monitor).  Now maximizing windows in screen 1 does not break the maximizing of windows in screen 0 (or shut down compiz). We'll see if it lasts.

---

### Post by slamhound on 2009-11-08
Okay, this fix doesn't stick.  It'll work for a while and I can maximize correctly on all three monitors, but then occasionally it'll break.  It usually occurs when opening or maximizing a window on Screen 1 (Monitor 3), though that does not reliably do it, and it seems that sometimes other events cause it. And to repeat what I said in my previous post, when this happens Compiz crashes and needs to be restarted.  So I'm at a loss here.  Any suggestions?

---

### Post by hcaicedo on 2009-11-10
I have the same setup as you (3 monitors 2 cards). I was looking for a way to fix the maximize problem. finally it works !!!!!!. I setup as you said and is working (at least for now) Thanks

---

### Post by slamhound on 2009-11-10
It looks like my problem may be related to a bug in the Wobbly Windows effect.  I disabled that and have had no problems since (though it's only been a day).  May experiment a bit more to see for sure.  But if you run in to the problem I had, try turning that effect off.

---

### Post by John von Neumann on 2009-12-04
I have precisely the same problem. If I enable "detect outputs", then everything works (bar windows maximising over two screens on the twinview pair), but the settings wont "stick". As soon as I do something on the second x-screen (3rd monitor), I lose the settings.

Everything used to work just fine, until I upgraded to 9.10.

---

### Post by slamhound on 2009-12-04
For me, turning Wobbly Windows off fixed it.  It has worked since my last post.  To see whether it really was Wobbly Windows, I turned the effect back on yesterday and had the same problem re-emerge.  So turned them off again and everything is fine.  Seems that any other effect that I want works as long as Wobbly Windows is off.

---

### Post by John von Neumann on 2009-12-04
If I set "detect outputs" to true, then everything works (including wobbly windows), but this means maximised windows span both monitors on the twinview screen. Short term fix is to enable "grid" in compiz, and create shortcuts to put windows "to the left" (puts them in the left monitor), and similarly for the right monitor. This gives the illusion of maximised windows on each monitor of the twinview screen.

If I try and manually enter the displays, i.e. for me:

Screen 0 (twinview)
1680x1050+0+0
1680x1050+1680+0

Screen 1 (separate x-screen)
1280x1024+0+0

then either Screen 0 or Screen 1 will go wrong (resolution is incorrect, graphics tearing, completely unusable). It looks like compiz can only handle settings from one screen. I've tried all the different combinations of applying these settings from different x-screens, to no avail.

---

### Post by techstop on 2009-12-06
I found the same problem. Disabling WW fixed it. Disappointing, as WW is kind of the "heart" of compiz.

---

