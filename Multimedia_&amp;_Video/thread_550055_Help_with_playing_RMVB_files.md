---
title: "Help with playing RMVB files"
date: 2007-09-13
forum: Multimedia &amp; Video
---

### Post by orangey on 2007-09-13
This is an age old topic, but this is the one remaining that thats bugging me, and the one thing I really need to work on ubuntu.  I've searched through threads and threads, and tried various players.  In short, I just want to watch rmvb files.  I've tried the following options:

1/ totem w/ gstream.  Won't play rmvb files at all, doesn't know what to do with them.
2/ totem w/ the other set of codecs (xine?).  Said it is unable to handle Real Media 4 videos.
3/ realplayer 10 gold.  Picture freeze, but I get audio.
4/ realplayer 10 gold with aoss.  Same as the above.
4/ mplayer with w32codecs.  This is the closest I got.  Picture works, and audio too, but the video lags far behind the audio.  Unwatchable.  I suspect the libs aren't handling the "variable bitrate" correctly, but really I know nothing about this.

Here's my system specs:
Pentium III 800Mhz
768 MB PC100
Nvidia Ti4400

I know my system is rather aged, but it should handle rmvb files no problem.  Ubuntu runs very smoothly on it, and I'm able to play divx and xvid without problems.  I'm at my wits end.  Please any suggestions?

I'm considering helix player (but isn't this the same as real player?).  I'm even willing to set up a streaming server to stream rmvb, but that's just too much work for something so "supposedly" trivial.  I'm at my wits end.  Help.  TIA.

---

### Post by orangey on 2007-09-13
Oh wait, I just found something.  "Uncheck use XVideo in real player preferences" in Edgy user guide.  I don't think thats it, but what does that do?  I won't be able to test it until I get home tonight.

---

### Post by orangey on 2007-09-13
Nevermind.  Pb solved.  Not sure whats different, but I reinstalled realplayer 10 and this time it worked.  I tweaked the preferences and unchecked "Xvideo" and I lowered the quality setting.  Still a little sluggish playing files, but its watchable.  I wonder if it'd be better if I raise the player's priorty.  Do I use 'nice' for that?

---

