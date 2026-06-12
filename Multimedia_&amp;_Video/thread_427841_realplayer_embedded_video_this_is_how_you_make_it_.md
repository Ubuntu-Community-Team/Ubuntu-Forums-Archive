---
title: "realplayer embedded video this is how you make it work"
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by sdowney717 on 2007-04-29
I could not watch cbsnews.com video or any embedded real player until I discovered that 
nphelix.so and nphelix.xpt with a compile date of july 19 2006 worked and the ones from 2005 were broken.

I archived my working copy of nphelix and you can get it off this post

SO,
to start, clear out the garbage 

send all real player folders to trash bin, wherever or however many you may have
send the mplayer plugin for realplayer to trash bin, 2 files only, the ones that gave mplayer plugin real player support mplayerplug-in-rm.so and mplayerplug-in-rm.xpt where-ever they me be located, perhaps in several places.

send all nphelix.so and nphelix.xpt to trash bin, where-ever they may be located.

NOW,

Install Realplayer10Gold.bin in the folder  /opt/RealPlayer folder.
run './filename.bin' and follow the prompts use the defaults

then in usr/lib/firefox/plugins and anywhere else they might be copy the 2006 versions of nphelix* to plugin directories.

If you already had installed realplayer, start it up and do a reset (listed in realplayer menu)  and restart realplayer to get the configuration script running.
close and restart firefox

AND it works at least for me!

I got the nphelix plugins out of an rpm from the helix site. It was the updated plugin.
I believe this is the site, see its an rpm file for fedora. ALL you need is the updated nphelix plugin, not the helix player!
[http://rpmfind.net/linux/rpm2html/search.php?query=HelixPlayer-plugin](http://rpmfind.net/linux/rpm2html/search.php?query=HelixPlayer-plugin)

---

### Post by sdowney717 on 2007-04-29
I still cant go fullscreen on cbs innertube online video . Too bad.

---

