---
title: "mplayerplug-in noembed=1 option not working"
date: 2007-06-09
forum: Multimedia &amp; Video
---

### Post by battra on 2007-06-09
Hi,

I run Xubuntu Edgy Eft.  I'm trying to watch streaming video using mplayer and mplayer-plugin (i.e. mozilla-mplayer).  On Linux, the only way I can get it to work is to set the noembed=1 option in /etc/mplayerplug-in.conf.   But, on Xubuntu Edgy, the noembed=1 is being ignored by mplayerplugin.  All the other options in mplayerplug-in.conf are being read, so I know the mplayerplug-in.conf file is being used by the plugin.  It's only the noembed=1 option that is being ignored.

Anyone have ideas of what I can do to get the noembed=1 option recognized by mplayerplug-in?

---

### Post by battra on 2007-06-09
SOLVED

My problem was that the w32 codecs were installed in /usr/local/lib/codecs and not /usr/lib/win32.

The stand alone mplayer (for downloaded wmv files) worked fine because it was using the /usr/local/lib/codecs directory.  But, mplayerplugin in firefox for streaming video wasn't working because it was searching for the codecs in /usr/lib/win32.  The noembed=1 option wasn't launching an external frame because the video couldn't be played anyway.

After copying codes to /usr/lib/win32, noembed=1 option launched an external frame and video/sound plays great (on CNN.com).

---

