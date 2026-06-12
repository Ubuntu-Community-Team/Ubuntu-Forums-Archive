---
title: "Help with Live &quot;server - 'client, client'&quot;  streaming"
date: 2014-03-01
forum: Multimedia Software
---

### Post by mike.azzara on 2014-03-01
Hi this is my first post,
 I'm fairly new to Linux but have a fundamental understanding of it. Currently i have a headless media server build that i am trying to add live music streaming to. Essentially my buddy and I game together a lot and previously have streamed separate music sources respectively. While this accomplishes getting each of us in the zone we would like to listen to the same source at the same time to take this to the next level. I have a large mp3 database that i would use as a source.. Plex and subsonic offer a supplementary solution as we can both time the initiation of a playlist but again this is not one but two feeds - ultimately i would like more control over the stream in more of a DJ sense. 

I'm certain this is possible I'm just not certain which solution is best for my situation. Any input is greatly appreciated - Thanks!

(Ubuntu Server 12.04.4 LTS running on a HP G62 notebook)


I am able to setup VLC's web interface which achieves the type of streaming i desire although it's web gui is very difficult to use on the fly ie selecting the next song or updating playlists quickly.

---

### Post by tgalati4 on 2014-03-02
I would use *mpd* or *mixx*:

tgalati4@Mint14-Extensa ~ $ apt-cache search mixx
mixxx - Digital Disc Jockey Interface

For updating playlists, you could set up some scripts that are activated with keyboard shortcuts.  Now, changing costumes to stay in the Zone is beyond the scope of this thread.

---

### Post by mike.azzara on 2014-03-03
What I really mean is a live media streamer with a solid WebGui i can operate from my windows laptop ect..

---

### Post by tgalati4 on 2014-03-04
I've used firefly in the past.  It is cross-platform.  [http://en.wikipedia.org/wiki/Firefly_Media_Server](http://en.wikipedia.org/wiki/Firefly_Media_Server)

---

