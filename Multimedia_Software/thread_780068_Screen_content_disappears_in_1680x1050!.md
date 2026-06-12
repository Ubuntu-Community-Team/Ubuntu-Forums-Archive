---
title: "Screen content disappears in 1680x1050?!?"
date: 2008-05-03
forum: Multimedia Software
---

### Post by slikar on 2008-05-03
Hello! I have Samsung 225MW widescreen monitor connected to ATI Radeon 9200 graphic card.
After installing Hardy I got very annoying problem of screen content disappearing when I move, resize or maximize windows, and sometimes even when I just move the mouse... It happens only at the monitor's native resolution of 1680x1050px @60Hz. At the lower resolution of 1280x1024px (at both 60 and 75Hz) everything works fine.
Just to mention, my xorg.conf file look quite generic, and considering the fact that all advanced desktop effects are working I suppose that the system has installed appropriate driver for my card...

Any idea how to fix this issue?
Thanx!

---

### Post by Zorael on 2008-05-03
The new X version in Hardy relies a lot less on the xorg.conf than the Gutsy and earlier versions did, instead auto-detecting your available resolutions, etc. As such, it defaults to the highest resolution available.

I believe you can set the default to 1280x1024 by manually adding some lines in said xorg.conf, in your Screen section. Example excerpt:
```
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
```
The first entry will be the default. Try this first, and if you're getting 60hz when you want 75hz etc (hopefully it'll autodetect and use the best available), just add @X after those resolutions, where X is the refresh rate you want.
```
	SubSection "Display"
		Depth		24
		Modes		"1280x1024@75" "1680x1050@75" "1024x768@75" "800x600@75" "640x480@75"
	EndSubSection
```

Flatscreens generally want input to be in 60hz, so if that's an LCD screen you might want to leave it at that.

---

### Post by slikar on 2008-05-03
Ooops man, it looks you got it all wrong, or I haven't explain it very well...
The 1280x1024 resolution (which is working fine) is not what I need - it's 1680x1050!
That one (1680x1050) is my monitor's native resolution, but when I switch to it the screen keeps on disappearing occasionally. So, I'm wondering is it a problem with the graphic card driver or something else..?

Any similar experience anyone?

---

### Post by monraaf on 2008-05-03
I have a similar problem with my nvidia card but it only manifests itself when I play a 3D game with wine while using the DVI output.

If you are using the DVI output try using the analog VGA output, that is if your card has one and your monitor has an VGA input.

---

### Post by slikar on 2008-05-04
> **monraaf said:**
> If you are using the DVI output try using the analog VGA output...
Thanx man, that has solved the thing.

It shouldn't be the final solution for our problems, though. If DVI input exists it should be working in any situation! Considering the fact that you have different graphic card (and maybe different monitor, as well), I am wondering could it be solved without use of that little downgrade..?

Could it be something to do with primary and secondary output on the graphic card? Maybe DVI is recognized like secondary and because of that is making problems?
Also, for Radeon 9200 I have found a manufacturers list of supported resolutions but 1680x1050 is not charted there... On the other hand, that card is rather old, so maybe 1680x1050 resolution wasn't standard at the time they were making the list..?

More opinions?

---

### Post by monraaf on 2008-05-04
I have an old Nvidia FX 5200 card connected to a Samsung 215TW monitor running at 1680x1050 resolution.

Like your ATI card 1680x1050 is also not listed as a supported resolution for the DVI output of my Nvidia card. In fact I had to add the Nvidia specific option:

```
Option          "ModeValidation"        "NoMaxPClkCheck"
``` to my xorg.conf to get 1680x1050 from my DVI output.

If you want to investigate further, you can try experimenting with different modelines (**man cvt**) or with driver specific options (**man radeon**).

For me the problem only manifests itself when playing a game with wine so it's not a big problem for me. I'm running twinview in cloned mode so when I want to play a game all I have to do is push the source button on my monitor to switch from the DVI to the VGA input.

---

