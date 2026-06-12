---
title: "Can Hardware Acceleration be slowing down 2D games?"
date: 2010-06-12
forum: Multimedia Software
---

### Post by iLag!!!!! on 2010-06-12
At least in the case of my Netbook, I think that the Intel GMA 3150 in my Acer Aspire One 532h is killing my performance in 2D Games.  Here's an example:
Playing Urban Terror, an ioQuake3-based game, I get around 30fps at the minimum.  That's perfectly acceptable for lousy onboard to perform that well.
Playing Cave Story, a very simplistic 2D SDL-based game, I go about half-speed in the Mimigma Village (first area outside the first cave).
This is unacceptable.  This is insane.  This is illogical.  This is paradoxical.  Even my PSP can run the area full speed!  And that's when it's downclocked to 111mhz! There is a problem here!

I've done the following to try to help solve the problem:
- Installed xserver-xorg-video-intel version 2.11 from the x-swat PPA.
- Created an xorg.conf with the following inside:
```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"uxa"
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
	Option		"Tiling"			"true"
EndSection
```
Neither improved my performance in any way.  If you know of something else that might help me, please tell me.

However, what I want to do now is test if my theory of Hardware Acceleration slowing the game down is accurate.  The problem is, I don't know how to safely do this.  I've tried adding Option "NoAccel" "true" to my xorg.conf, but that did nothing.  If there's an easy command to input (which there always is) or if removing xserver-xorg-video-intel won't render X inoperable, please tell me.

One last note: I have Kubuntu installed, but that shouldn't make any difference.

---

