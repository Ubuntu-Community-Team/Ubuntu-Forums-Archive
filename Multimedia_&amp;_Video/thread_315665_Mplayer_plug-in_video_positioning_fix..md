---
title: "Mplayer plug-in video positioning fix."
date: 2006-12-09
forum: Multimedia &amp; Video
---

### Post by kylevan on 2006-12-09
I don't know if anyone else has come across this problem (I couldn't find anything searching the forums,) but when playing embedded video in Firefox with the mplayer plug-in, I was having this weird scaling/position problem.

When the video started, it was like the video was scaled about 25% too large for the embedded window.  Basically you would see from the upper left corner to as far as the embedded video size, yet the bottom and right sides were cut off.

Anyway, what worked for me was editing the mplayerplug-in.conf file.

```

cd ~/.mplayer

vim ./mplayerplug-in.conf
(or substitute gedit or whatever you like for vim)

```

I had to change the vo= line from "xv" to "x11".  After saving the file and restarting firefox, videos appear properly.

You could also do this through a GUI.  Open up a website with embedded video, and right click the video.  The configure option will bring up the same options, just in pretty listbox form.  I just prefer to edit configs in the terminal. :mrgreen: 

Anyway, I hope this helps someone.

---

