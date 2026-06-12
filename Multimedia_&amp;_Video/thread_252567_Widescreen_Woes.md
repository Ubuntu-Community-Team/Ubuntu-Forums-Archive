---
title: "Widescreen Woes"
date: 2006-09-07
forum: Multimedia &amp; Video
---

### Post by trexjack on 2006-09-07
I just bought a shiny new 19" widescreen (1440x900) Envision monitor, and have gotten it to work well for most standard applications, but video has been a problem.  Running the auto config for xorg did the trick getting the desktop up, although I have tweaked this and that since first doing it... I've been trying to fix the following problems all day ](*,) .

First of all, I'm using an nvidia geforce2 mx graphics card, and the nv driver for it.

DVD's: the main reason I wanted a widescreen monitor was to be able to play back widescreen movies without the "black bars," but this just won't work, regardless of the aspect ratio/zoom/etc.  I prefer totem/xine, but have tried mplayer as well.

MythTV: won't work for live tv or recorded programs, and locks system.  First, I get a black screen with audio, then it locks.  I've tried this at lower resolutions, as well.

General:  Occasionally, on rebooting from a myth crash or at other times, my display comes up with a wide black band on the left side of the screen, and a square display on the right 2/3's of the screen.  I've found I can fix this by changing to a lower resolution, then back to the 1440x900 default.

After much reading and tweaking, I edited my xorg.conf file's monitor section to correctly include a modeline and displaysize, like so:

> Section "Monitor"
[INDENT]Identifier	"H193Wk"
DisplaySize	408 255	
HorizSync	30-80
VertRefresh	55-75
Option		"DPMS"
Modeline "1440x900_60"  108.84  1440 1472 1880 1912  900 918 927 946 +hsync +vsync[/INDENT]
EndSection

I've also commented out the "wacom" references in xorg.conf, which was causing mythfrontend to report an error when starting (I remember having to do this when I initially set myth up).  This fixed the error, but still no video.

I've also tried reinstalling totem/xine for the DVD problem.  Anyone have any ideas?

---

### Post by trexjack on 2006-09-07
No answers?  I know these forums are active (believe me, I've read enough posts)...

---

### Post by trexjack on 2006-09-08
Making some progress now, and I'm guessing now that all three of these are separate issues...

This is my first time to actually document the troubleshooting I've done on this system, so if this helps anyone searching for help with the same issues, I'd like to know.

Regarding the widescreen DVD issues: thanks to the instructions [here]("http://gentoo-wiki.com/HOWTO_MPlayer_Introduction_Guide#Watching_Movies_on_a_Widescreen_Monitor"), I finally confirmed that yep, those black bars are part of the source file, and have to either be cropped out (mplayer), or the image zoomed (xine).  Just follow the instructions in section 6.4 of the link to "fix" mplayer. for me, the command "gmplayer -vf crop=720:368:0:58 -aspect 4:3 dvd://" worked for a perfect full screen viewing of Crash.

I had begun to suspect that this was the case, and actually could've saved hours of "learning" had I figured out the controls for zoom in the different flavors of xine.  For totem it's "R" and "r;" for the xine ui it's alt-Z and alt-z.  For that matter, I should've found the mplayer article sooner, as well - poor search habits on my part, I suppose...

I would like for this to happen automatigically, but at least now I understand why that's so difficult (mainly because there are several different aspect ratios movies are shot in, thus giving you different size black bars on movies labeled "widescreen")

On to MythTV (in the first post I forgot to mention that I had finally gotten 1.19 to work on my CRT)

---

