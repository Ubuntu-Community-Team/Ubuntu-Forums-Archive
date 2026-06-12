---
title: "gamespot.com streaming videos....."
date: 2006-11-30
forum: Multimedia &amp; Video
---

### Post by scotty2hott2k on 2006-11-30
hi, streaming video form gamespot.com no longer works for me, it sued to work in dapper, then all of a sudden stopped working and doesn't work in edgy either. streaming from gametrailers.com doesn't work either, ive got the w32codecs pack installed, mplayer-plugin, also tried kaffeine plugin and vlc, neither of them work either.

can someone try it and see if it works for them? or offer me a suggestion/solution?

thanks in advanced,

scott

---

### Post by padre999 on 2006-11-30
It works for me when I open gamespot with Konqueror, but not with Firefox... I guess you would have to install some plugin for Mozilla/Firefox from the repositories.

Konqueror uses the Xine plugin.

But anyway I guess you are using Gnome, so no Konqueror for you.

---

### Post by scotty2hott2k on 2006-11-30
so you can actually stream a video off the site? man thats a bummer :(, it used to work for me to :(

---

### Post by princemackenzie on 2006-11-30
> **scotty2hott2k said:**
> so you can actually stream a video off the site? man thats a bummer :(, it used to work for me to :(

AFAIK the "mozilla-mplayer" package is what you need to stream videos in firefox.  It is in the multiverse repository.

EDIT: I saw that you tried that... it might be a codec issue then.  Can you try to view the mplayer output for that stream?

---

### Post by scotty2hott2k on 2006-11-30
how would i go about viewing the mplayer output?

---

### Post by CarpKing on 2006-12-01
> **scotty2hott2k said:**
> how would i go about viewing the mplayer output?

Find the URL of the movie, open up a terminal and type "mplayer http://urlofmoviefile."

---

