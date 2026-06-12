---
title: "video encoding with subtitles"
date: 2007-02-27
forum: Multimedia &amp; Video
---

### Post by qbproger on 2007-02-27
I was wondering what options there are for adding subtitles to videos when encoding them to DVD.  Previously on windows I had used software called The Film Machine to encode it.  I'd like to completely remove my dependence on windows.

Does anyone know of a software package that encodes video to a DVD and supports subtitles?  I'd prefer something with an interface if it's possible.  Thanks.

If there aren't any options, has anyone run any software in wine (i haven't installed it yet because i wanted to use native linux options) that does what I'm looking for?

Thanks again.

---

### Post by timjayko on 2007-02-27
well i am on ubuntu edgy and in add/remove under sound/video there is an app called KSubtile that seems to be what you need.. hope so good luck

---

### Post by RomeReactor on 2007-02-28
I've seen that option in **AviDemux**, though i've never used it myself (that option, i mean); look for it in Synaptic, or from the terminal

```
sudo apt-get install avidemux
```

---

### Post by jocheem67 on 2007-02-28
There's avidemux indeed, great app. Furthermore there's dvdrip, my favourite...
Tovid is command-line but it's a powerful tool, and under wine you can use dvdshrink. It's easy to set up.

There are several howto's on this forum, it kind of depends on what your goals are...just copying a dvd, dvdshrink is the easiest.

Transcoding to .avi ( xvid ) dvdsrip is an easy one and almost always works well. A/V sync is okay. It lets you rip the subs from dvd in .sub format, viewable with mplayer and vlc. Not ideal but works.

tovid let's you convert a .avi to dvd with subtitles.

---

### Post by Erlander on 2007-02-28
I have been looking for the same sort of program and have had Q DVD-Author recommended to me.  [http://qdvdauthor.sourceforge.net/](http://qdvdauthor.sourceforge.net/)

Its also in Synapatic as qdvdauthor but that version id 6 months old.

Rob

---

### Post by qbproger on 2007-03-03
avidemux + qdvdauthor seems like a great combination just a few bugs in avidemux holding up the progress :x

the version is the repository (2.1.2) seems to always have the highest compression

the version on their website (2.30) sets ' to " in subtitles.

---

