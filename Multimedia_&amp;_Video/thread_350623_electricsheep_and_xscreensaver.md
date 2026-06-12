---
title: "electricsheep and xscreensaver"
date: 2007-01-31
forum: Multimedia &amp; Video
---

### Post by spin2cool on 2007-01-31
I spent a few frustrating hours trying to get xscreensaver to launch electricsheep correctly on a dual monitor setup, and I thought I'd document my progress and ask for help here.

Versions: 
electricsheep 2.6.8-2ubuntu1 
xscreensaver 4.24-4ubuntu2 (both from the ubuntu repositories)

Description:
This issue affects systems using NVIDIA dual-monitor setups with Twinview enabled.  My desktop, as an example, uses 2048x768 resolution.

When the computer goes idle, xscreensaver launches two seperate instances of each screensaver, one on each monitor, each with a resolution of 1024x768.  This works correctly on all other screensavers.  However, when electricsheep is launched, xscreensaver correctly launches two instances, but both instances of electricsheep believe the screen resolution to be 2048x768.  This results in only half of the video appearing.

I poked around in the documentation and code, and there seems to be no way to pass parameters to either electricsheep or to mpeg2dec_onroot that will allow for correct resolution to be specified.

Any ideas?  Has anyone figured out how to get xscreensaver to launch mplayer as a screensaver successfully, using the --player option?

If not, consider this an FYI to twinview users trying to set this up...

---

