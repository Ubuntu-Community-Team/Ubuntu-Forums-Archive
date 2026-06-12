---
title: "Xvid -&gt; DVD Converter?"
date: 2005-05-01
forum: Multimedia &amp; Video
---

### Post by halo five on 2005-05-01
Hi all,

I have some videos that the author encoded in Xvid format.  I have heard of applications that allow one to convert one or more Xvid files into a burnable dvd iso (or similar).  This ISO could then be burned to DVD-R and viewed on a standalone DVD player.

Anyone know of anything along these lines?  This question isn't ubuntu-specific, I know -- But you guys seem to know everything  ;-) .   Apps already in the ubuntu universe are preferred  :smile: 

Thanks in advance for any pointers.

---

### Post by calraith on 2007-11-26
[DeVeDe]("http://www.videohelp.com/tools/DeVeDe") is the best I've found for converting * to DVD ISOs.  I'd like to have seen other recommendations in this thread, though, as DeVeDe isn't perfect.  For instance, its estimates of disc usage after conversion aren't accurate at all.  If you tweak your audio and video bitrates to try to squeeeeze your video onto 4.7 gigs, and DeVeDe estimates 100% usage, the resulting ISO will be about 2 gigs.  DeVeDe is also giving me a little grief with converting the audio track of an Xvid I have -- but usually it does fine with audio.

Update: It appears that the version of DeVeDe in the repos is old, version 2.13.  Current version as of this writing is 3.4.  And the sound issue I had was due to a buggy version of mencoder.  Enabling Backports in the repositories allows updating to a version of mencoder that has this bug fixed.  The [DeVeDe homepage]("http://www.rastersoft.com/programas/devede.html") has instructions on how to do this.

---

