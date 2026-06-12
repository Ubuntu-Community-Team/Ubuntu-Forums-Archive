---
title: "HDTV on mac mini (i945)"
date: 2007-10-08
forum: Multimedia &amp; Video
---

### Post by BrooksT on 2007-10-08
I'm having a terrible time getting either 7.04 or 7.10 to output HDTV resolutions on a Mac Mini (intel, core2 duo 1.83).   I've tried xorg.conf with settings found on the mythtv wiki, I've tried removing xorg.conf altogether (with 7.10), and nothing seems to do it.

915resolution doesn't display either 720p or 1080i resolutions as an option, but I believe that doesn't matter with the xserver-xorg-video-intel driver.  I've tried setting modes using 915resolution, but they disappear on reboot.

No matter what I do with xorg.conf or 915resolution, neither 1280x720 nor 1920x1080 appear in the dropdown list of resolutions in system/preferences/screen resolution.

I've tried stopping X, editing xorg.conf, running 915 resolution, deleting .gconf/ from my user dir, everything.  No go.

I'm connecting to an HDTV using the DVI port, a DVI->HDMI converter (which I believe is just electrical, right?), and an HDMI cable.  This HDTV does not support HDTV resolutions over its VGA plug (which I'd rather not use anyways, since it's analog).

Any tips on getting this to just work?

Thanks
-b

---

### Post by anville on 2007-10-12
I am in the same boat.  I am using a mac mini as a media center with my Philips 32" LCD TV.  I would love to use Linux & Freevo, but I cannot get any widescreen resolutions, either.  Last night I installed the gutsy release candidate, but still no luck.

Anyone out there with some tips on contructing an xorg.conf file for this sort of thing?  I have seen references in google to things like "monitor-tv" but can't seem to get anything work.

Help! :-)

---

