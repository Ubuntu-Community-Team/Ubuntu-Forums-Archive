---
title: "Triangular Artifact on MythTV Output"
date: 2014-02-04
forum: Mythbuntu
---

### Post by bill26 on 2014-02-04
Setup a new Mythbuntu (Ubuntu 12.04.4 LTS) instance and now have a triangular shape (upper right-hand corner) pop up for ~ 1ms in between each frame change on my MythTV display.  This happens for HD recordings and video files that have been uploaded to the box.  When I try to play either of these same videos from outside MythTV (i.e. using a terminal with mplayer), I do not have this triangular artifact appear.
 
Here's a quick picture of what I'm seeing:[INDENT]
 [IMG]http://i.imgur.com/yqCSqu0.jpg?1[/IMG][/INDENT]


Any thoughts as to what may be causing this or how I can resolve?

Video Card:  AMD/ATI RV370 [Radeon X600/X600 SE]
MythTV 0.27

Thanks!

---

### Post by blm-ubunet on 2014-02-04
Does the triangular piece "belong" to the previous frame ? (need high motion scene)

What -vc & -vo options do you use with mplayer (that works) ?
Could be video overlay method ..De-interlacer method option?

Can the radeon driver do anything with the X600?
Decode must be happening in CPU.

LIBGL_DEBUG=verbose glxinfo

---

### Post by bill26 on 2014-02-04
Thanks for your response!


To be honest, I'm not entirely sure but believe that the trianglular artifact is in fact part of the previous frame.


For my mplayer test from the the console, I simply tried "mplayer <video>.avi" as the command and didn't see any issues.


How can I check / change the video overlay or De-interlacer options?  


My output of LIBGL_DEBUG=verbose glxinfo is posted here - [http://paste.ubuntu.com/6876274/](http://paste.ubuntu.com/6876274/)




Thanks again!

---

### Post by blm-ubunet on 2014-02-05
If the triangle was a residual fragment from previous it could be a clue to the exact mechanism..

Your glxinfo stdout looks correct (to me).

Running mplayer from terminal should indicate the -vc & -vo options used (even if just default) in the stdout logging..
There is a default config file for mplayer ..could be ~/.mplayer/config

Could try mplayer with other -vo options to try to induce the problem..
try: -vo  [ vdpau | xv | gl_nosw | x11 | xover | gl ]
(where you choose one of [ option1 | option2 | ... ]

I doubt your video h/w supports vdpau but no harm trying..

---

### Post by bill26 on 2014-02-23
Sorry, it's been a little while, but I finally had a chance to give your suggestions a shot.


Here's what I found with mplayer from the command line (i.e. mplayer -vo <...>):


[INDENT]vdpau - no video playback
xv - triangle artifact present
gl_nosw - no triangle present!
x11 - small screen (not full screen)...tough to tell
xover - no video playback
gl - no triangle present![/INDENT]


So, the two "gl" options do not have the triangle artifact present.  Now what does that tell us? :)  Is there anyway that I can use mplayer with these options as my default for all recordings and videos?


Thanks again for your help!

---

### Post by blm-ubunet on 2014-02-24
VDPAU does not work & xv causes the triangle to appear..

You can configure mythtv to use the much the same video decode/presentation as mplayer..
Try setting FE playback profile to "openGL".
I think "xv" is the default profile.

[http://wiki.x.org/wiki/RadeonFeature/](http://wiki.x.org/wiki/RadeonFeature/)
The RV370(X600):
VDPAU on the 3d engine is a WIP...UVD is n/a.

HD might be a good excuse to upgrade h/w.

---

### Post by bill26 on 2014-02-24
Thanks for the response!

I tried the "OpenGL Normal" and "OpenGL Slim" Profiles and they indeed fixed the triangle artifact.  Unfortunately, some of my recordings are choppy and not watchable.  I presume these are higher quality recordings and can't be handled by this profile.  Are there any tweaks that I can make to get these profiles to work, or could I create my own custom profile?

It should be noted that I didn't have these problems with HD recordings and this same hardware under MythTV 0.25.  With that said, I don't know how the default (Internal) player differed under that older version.

Thanks again!

---

### Post by blm-ubunet on 2014-02-26
I don't have much experience with low end marginal systems except for 1st gen atom netbook..
The netbook copes (just) with mythtv SD H264 decoding & most basic de-interlacing.
But haven't used this h/w since 0.25 was latest release.
My main system has always had core2duo & nVidia GPUs.

I seem to remember that 0.26 & early 0.27 were slower & more sluggish than master now.
I think the performance of 0.26 made me shift to building master & not the fixes branch.

There were playback profile rejigging sometime in recent past but I can't find the commit or mailing list archive comments.
There used to be a list of options from CPU-- to openGL-high to VDPAU etc..
Is there still a "CPU--" profile?

The profile list (in master) is simplified (shorter).
Sorry this is not very helpful..

You should read your log files (/var/log/mythtv/*.log) to see if there is a easy fix/clues.
You may need to stop & restart the FE with extra logging options & redirect log to file:
mythfrontend -v playback > logfile.txt

Mythbuntu could make this difficult because of auto-spawning FE & (potentially) renaming the FE executable file.

---

### Post by blm-ubunet on 2014-03-12
If you're looking at a new card..
The 2nd generation version of GT630 GK208 (384 shaders) is a very good PCI-express option.
Do you have any PCI-express slots.
PCI VDPAU card are scare & ancient.

---

