---
title: "mplayer timeout/delay at start, disable screensaver - solved"
date: 2008-04-28
forum: Multimedia Software
---

### Post by alterpinguin on 2008-04-28
mplayer timeout/delay at start, disable screensaver - solved

mplayer shows a significant delay at startup
and from the console messages it depends on the missing screensaver-functionality.

in /etc/mplayer/mplayer.conf
there is an entry for disable and enable after run for mplayer:

#Screensaver support (for non gmplayer)
stop-xscreensaver = "yes"

set this to "no",
or even better create your user-mplayer config
in your home-directory:
~/.mplayer/config

and put in the line to do no screensaver check:

stop-xscreensaver = "no"

and mplayer will start at once, when called directly from commandline.

This delay is only for video files not for audio-only files.

(btw. i have not disabled my metacity screensaver)

---

