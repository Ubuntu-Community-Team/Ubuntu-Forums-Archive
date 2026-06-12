---
title: "X config for i810"
date: 2008-05-25
forum: Multimedia Software
---

### Post by shochatd on 2008-05-25
I recently did a clean install of 8.04 on an old-ish Gateway PC that has an Intel i810 video subsystem. I can tell that something is not right with the video configuration because when I go into screensaver prefs and click on the various screen savers, instead of getting mini previews inside the prefs window, I get a bunch of moving horizontal lines along the bottom half of my screen, except for a few of the screensavers. This has worked properly, including GL, with earlier versions of Ubuntu, so I wish I had saved my old xorg.conf. When I look at the one that was created by the install, it seems to be extremely short and generic. It doesn't even mention i810 or intel anywhere, which seems very suspicious. So my question is, what tool can I use to set up a new video configuration? I tried dpkg-reconfigure xserver-xorg, which looks like it's going to do this, but it ends up just configuring the keyboard and exiting. It never asks any video questions at all. I looked at the Intel section on the x.org web site and they mention a tool called "xorgconfig" but they say the actual name of this tool is "system-dependent". Is there a good tool for setting up a detailed xorg.conf that is available for Ubuntu?
Thanks. 
-- David

---

