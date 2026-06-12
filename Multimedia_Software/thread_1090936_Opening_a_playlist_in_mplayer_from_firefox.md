---
title: "Opening a playlist in mplayer from firefox"
date: 2009-03-08
forum: Multimedia Software
---

### Post by lucas42 on 2009-03-08
Hi,
     I'm having a problem opening playlists from firefox in mplayer.  
I think this is because mplayer needs the "-playlist" parameter to play playlists.  I'm not sure how to pass parameters from firefox, I've tried writing a bash script containing `mplayer -playlist "$@"` and running it from firefox, but that didn't seem to work.
I've tried a few mplayer derivatives; mplayer, gmplayer and smplayer all don't work as they require the "-playlist" parameter.  kmplayer doesn't require it and it runs fine.  I'd like to be able to do it on other machines that don't have kmplayer installed.

Any suggestions?

Thanks.

---

