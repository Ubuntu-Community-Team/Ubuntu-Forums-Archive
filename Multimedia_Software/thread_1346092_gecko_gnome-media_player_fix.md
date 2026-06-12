---
title: "gecko gnome-media player fix"
date: 2009-12-04
forum: Multimedia Software
---

### Post by sdowney717 on 2009-12-04
gecko gnome-media player fix
[https://launchpad.net/~norsetto/+archive/ppa](https://launchpad.net/~norsetto/+archive/ppa)
install this gnome-mplayer and you can now view these videos in the browser

hunt for alien earths will now play instead of endlessly cache

[http://feeds.pbs.org/pbs/wgbh/nova-video/](http://feeds.pbs.org/pbs/wgbh/nova-video/)

these cnn sites will now play

[http://rss.cnn.com/services/podcasting/studentnews/rss.xml/](http://rss.cnn.com/services/podcasting/studentnews/rss.xml/)
[http://rss.cnn.com/services/podcasting/amanpour_video/rss/?format=xml](http://rss.cnn.com/services/podcasting/amanpour_video/rss/?format=xml)

so add in the repository under software sources
run synaptic search for gnome mplayer
right click the application package and select mark for upgrade 
apply



this is the bug report. the player will still cache the whole file but then it plays where as before it would cache and never play.
files that would normally start quick will still start quick
[https://bugs.launchpad.net/ubuntu/+source/gecko-mediaplayer/+bug/489191](https://bugs.launchpad.net/ubuntu/+source/gecko-mediaplayer/+bug/489191)

I had found other sites that had the same trouble and they should also work
it was great of the developer to fix this

---

