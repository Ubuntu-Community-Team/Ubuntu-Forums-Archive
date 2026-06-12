---
title: "Audio ptoblem"
date: 2009-12-23
forum: Multimedia Software
---

### Post by peterconway on 2009-12-23
Hi,

I'm new to Linux, so excuse greenness!
I'm running 9.04 and want to play internet radio either through Rythmbox or more usually through 'Radeo' interface.
Having problems getting Realplayer to work(some intrenet stations use this) - keep getting message text/html decoder needed, any idea how to get this downloaded?
I have Realplayer installed and sitting on desktop.
Radeo works on BBC and some stations ok, can't get any sounds out of Rythmbox internet radio.

Regards,

Peter

---

### Post by quixote on 2009-12-24
I'm not familiar with Radeo.  Does it work through the browser?  If yes, it may be wanting the browser plugin.

Also, did you install Realplayer from Synaptic or separately?  If the latter, that may be the problem, since it doesn't pull in dependencies. 

I'd do the following: 
--check for "helix-player" in synaptic. (It's the open source version of realplayer.)  That should show you whether synaptic sees it as installed. If not, install realplayer and mozilla-helix-player (the browser plugin) from synaptic.

--try running with something other than Rhythmbox, which is pretty hopeless at pulling in codexes.  Vlc is my favorite. (If you install that -- again, via synaptic -- then remember to also get mozilla-plugin-vlc.)  Other people swear by mplayer.

You may just want to try vlc or mplayer.  I can play realplayer files, but when I checked my synaptic, I see realplayer is apparently not installed.  I think vlc just knows the codecs, or something.  ??

---

