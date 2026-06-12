---
title: "need a media player that works with jack"
date: 2008-06-27
forum: Multimedia Software
---

### Post by dvdplaya on 2008-06-27
I have tried everything.  I love the simple layout/library view of rhythmbox but it does not have jack support.  I got Jack working with amarok but it cannot play flac files (they are all stuttery and unlistenable).  If anyone knows a solution to this stutter issue in amarok please enlighten me, I've looked everywhere.

I'm looking for a media player that will allow me to output audio through jack and has a library view.  XMMS works fine but I dont want to use playlists and frankly i hate xmms.

I'm using Hardy 8.04.  please help i am very annoyed.

---

### Post by leepesjee on 2008-08-10
Hi dvdplaya,

Aqualung plays over jack. It plays flac OK on my system. I don't exactly understand what you mean by 'library' view, but you can try if it satisfies you.

BTW, found your post looking for a possibility to play rhythmbox over jack, but apparently that's not possible.

P.S.
Another way is to use pulseaudio and route pulseaudio to jack. It's been figured how to do that in this thread [http://ubuntuforums.org/showthread.php?t=875378](http://ubuntuforums.org/showthread.php?t=875378)

Good luck, Leo.

---

### Post by leepesjee on 2008-08-10
OK, found the fix,

Rhythmbox *does* have jack support, but its routed to pulseaudio in Hardy by default. It can be easily rerouted to jack, following this thread:  [http://ubuntuforums.org/showthread.php?t=554457](http://ubuntuforums.org/showthread.php?t=554457)
Don't bother about the .jack.plumbing thing if you don't do fancy things with jack-rack, just replace pulseaudiosink with jackaudiosink.
Leo.

---

