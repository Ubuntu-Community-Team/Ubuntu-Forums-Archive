---
title: "&quot;Screens &amp; Graphics&quot; app missing after Gutsy upgrade"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by raydar on 2007-10-21
I've upgraded 2 Feisty installations to Gutsy, the first being Ubuntu and the second being UbuntuStudio.  With the first, the new "Screens & Graphics" application was installed, but with the second, it doesn't appear to have been.  It's not in the menu in the 2nd installation where it was in the 1st, and I can't find anything in Synaptic that looks like it's that app. I also tried a few guesses at the command line, but no luck.  Anyone know what the app's called, or why it might not have shown up?

---

### Post by prshah on 2007-10-23
Try: gksu displayconfig-gtk

I find mine in System->Administration->Screens and Graphics.

Is your user allowed to do system administration? Better check user profile and group.

Cheers,
PRS

---

### Post by raydar on 2007-10-23
Right on the money:  The package displayconfig-gtk is the Screens and Graphics app.

I tried the command, and nothing happened; no "command not found" or anything.  Fired up Synaptic and found that displayconfig-gtk was not installed.  Installed it, reran gksu displayconfig-gtk in the terminal, and voila--there it is. :)

Thanks!

That's where I saw Screens and Graphics in the menu in my first installation; I just checked and it has appeared there now in this one. (System admin privileges were checked, as in visually just now and already with a checkmark.)

EDIT: Indirectly related, but oh boy did it screw up my 2 screens!  Resolution of 3072x1536 is the only option in Screens and Graphics, but it looks more like its usual 1600x1200 except the desktop is bigger than the screen & I can scoot it around at the edges w/my mouse.  My right-hand monitor, 1024x768, starts out with only half of its desktop space on it, the other half overlapping onto my half-again-as-big-as-it-should-be main desktop.  Depending on what I do with and without Compiz, I can get monitor #2's desktop squarely on it, but yeeks . . . oh well, troubleshooting is fun.

---

### Post by moon2js on 2007-10-24
All the press said Gutsy had dual monitor support but after upgrading I couldn't find it at all. Then after reading this thread, I went and installed displayconfig-gtk and then I had the "Screens and Graphics" options. Is there some reason why this wasn't installed in the first place?

And it doesn't really work. It doesn't seem to recognize my second monitor (the second just mirrors the first). And "Test" doesn't really work -- it brings up the Gnome-less bare X (mirrored on both screens) with the option to Cancel or Keep Settings.

But I'm also wondering if there's anything else that wasn't installed by default because when desktop effects are enabled, the windows lose their menu bars.

---

### Post by raydar on 2007-10-24
The Screens and Graphics app seems like a noble & more versatile (not Nvidia-card-specific) successor to nvidia-settings, but I have yet to get it to work properly.  I tried adding a second video card for the heck of it after my troubles mentioned in my original post above, and another screen (for a total of 3) showed up in Screens and Graphics, but I couldn't get my bios to properly handle the 2nd video card (no video), so I switched back to my orig. setup. But Screens and Graphics still lists it--disabled, but there, and there's no remove button.  On an earlier installation I upgraded from Feisty to Gutsy, I never did get the second screen working right (gibberish rather than no video or weird-but-sorta-right video), no matter what I did in Screens and Graphics; it wouldn't keep my changes.  The "location" bar at the top of Screens and Graphics was empty for me then, and it is now too, on this new (upgraded) installation.

Anyway, the "Test" button is greyed out for me; so you're doing better than I am there.  As for your second monitor mirroring the first, I've been running two monitors (one video card) since Feisty or before, relying mostly on the nvidia-settings app and a few edits to the xorg.conf file to get the second monitor acting the way I want (extension of 1st monitor's desktop).  Could be you could get yours working that way, at least if you have an Nvidia card.  One 2-monitor configuration I was stuck with for a while had a whole 'nother set of panel bars & menus on my second monitor, and I couldn't drag windows between them or run Firefox on both monitors, but neither was mirroring the other.  If you have Compiz installed for fancy desktop behavior, the Display Settings tab in the General settings under System-->Preferences-->Advanced Desktop Effects Settings has a place where you can force desktop size and position and screen resolution for a two-monitor setup.  I've been relying heavily on that.  (I fixed the problem in my last post above by replacing my xorg.conf file with a backup and re-tweaking things in those Advanced Desktop Effects Settings.)

When my panel bars disappeared like yours, a user named snoe came to the rescue--look toward the end of this thread: [http://ubuntuforums.org/showthread.php?t=574851](http://ubuntuforums.org/showthread.php?t=574851)  I also had problems with windows maximizing across both monitors, and there's a fix for that there too (full screen mode is still dodgy, but maximizing works ok).

Screens and Graphics is the only thing I found so far not installed that ought to be.  I also wound up with one *extra* thing too, but that's just a menu item--namely a second "Printing" item in System-->Administration (one's tooltip reads "Configure printers" and the other's reads "Configure your printers").  But I'm running UbuntuStudio, and it goes to extra lengths in organizing audio & video apps in the Applications menu, so a menu item glitch during an upgrade isn't the most surprising thing in the world.

---

### Post by lonniehenry on 2007-12-12
I have nothing in the screens and grapics app.  When I try to open it using  gksu displayconfig-gtk
it gives me an error message of 
*** Error: couldn't find any ServerLayout sections
How do I correct this?
I am using Hardy alpha 1 32 bit version -- graphics work correctly - compiz works
Thanks in advance

edit - I found a old version of xorg.conf from Gutsy and copied it to the xorg,conf in Hardy.  it then populated the screen and graphics app.

---

