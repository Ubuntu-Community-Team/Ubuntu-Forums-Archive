---
title: "mplayer command does not open a new window"
date: 2012-09-27
forum: Multimedia Software
---

### Post by mike004 on 2012-09-27
Lubuntu 12.04 on a Thinkpad 600X.

The installed version of mplayer did not work. "This software was compiled on a different computer to the one you are using..." or similar.

I'm only interested in running mplayer from the command line. So, I download the sources from the mplayer site and compiled my own version.

Everything compiled OK and when I run the mplayer command from a terminal window, I get a long help message, as expected.

But ther are problems when I try to "run" a video file from the command line:
mplayer test1.mpg

mplayer does not open a new window to play the video in. Console messages are dumped to the open terminal window, suggesting that the file is playing OK. Sometimes I can hear audio. But no video.

How can I get mplayer to spawn a new terminal window? On Gnome/Red Hat systems this is done automatically.
Is this an issue with the window manager used by Lubuntu?

---

### Post by marinara on 2012-09-28
install VLC.  not sure why mplayer isn't outputting video, so I can only guess
That mplayer bug is a known bug on older CPU's for 12.04.  would you be interested in testing 12.10?

---

