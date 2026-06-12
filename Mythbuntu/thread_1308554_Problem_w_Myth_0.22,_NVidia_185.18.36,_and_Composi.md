---
title: "Problem w/ Myth 0.22, NVidia 185.18.36, and Composite extension"
date: 2009-10-31
forum: Mythbuntu
---

### Post by mbobak on 2009-10-31
Hi all,

Upgraded to Karmic, running Myth 0.22 from the -trunk Mythbuntu daily builds, and, now that I'm on Karmic, have the 185.18.36 binary driver.

I've read many times that starting with (I think) 180.60, video playback w/ composite extension will no longer cause image tearing.

So, I thought I'd try it.  So far, no tearing.  But, I do have a different problem.  When mythfrontend runs, it refuses to cover the gnome window manager bars at the top and bottom of the screen.  With composite disabled, it's not a problem, but with it enabled, I see the top and bottom bars.

Anyone else running myth w/ composite enabled?  See this problem?

Thanks,

-Mark

---

### Post by suffice on 2009-11-04
I just got a new setup and put karmic on it....and then the mythbuntu-desktop package.

it also doenst cover the gnome panels, the videos i have are 16:9 but it makes them much more wide angled and squished, and when downloading metadata it shows the description but doesnt show the cover art.

on my older computer all of this worked fine, but was just slow to navigate around, because it was a slower machine.

i'll be looking into things more seriously really soon, but if you find anything out let me know

---

### Post by hackmeister on 2009-11-04
You should not be running compositing with VDPAU. It's a long time known issue:
[http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)

Look at the trouble shooting section

---

### Post by mbobak on 2009-11-14
> **hackmeister said:**
> You should not be running compositing with VDPAU. It's a long time known issue:
[http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)

Look at the trouble shooting section

Actually, according to [this]("http://www.nvnews.net/vbulletin/showthread.php?t=141064"), the issues w/ video tearing are resolved, or, nearly so.  That's also my experience, the tearing issues are resolved.

My only remaining issue w/ Myth/VDPAU/Compositing is the gnome task bars that refuse to hide under the fullscreen Myth display.  If that can be resolved, I think that compositing will play nice w/ Myth and VDPAU.  Actually, Myth and VDPAU already appear to be playing nice, with the tearing issue resolved.  The remaining problem has nothing to do with VDPAU.  It's an issue with MythTV not running on top of the Myth task bars when compositing is enabled.  What I don't know is, if it's a Myth problem, or a compositing problem.

-Mark

---

### Post by mbobak on 2009-11-14
One more thought:

This really has nothing to do with VDPAU, since VDPAU is only used for video playback, and this problem crops up as soon as I run mythfrontend w/ the NVidia 185.18.36 driver and compositing enabled.

As a quick test, I tried XMBC, and it has no problem covering the Gnome task bars.  So, this does seem to be isolated to mythfrontend.

-Mark

---

