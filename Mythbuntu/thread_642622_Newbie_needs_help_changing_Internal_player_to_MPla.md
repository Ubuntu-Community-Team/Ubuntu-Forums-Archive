---
title: "Newbie needs help changing Internal player to MPlayer, VLC, and Xine"
date: 2007-12-16
forum: Mythbuntu
---

### Post by thematadorme on 2007-12-16
Internal player is giving me grief. I want to try switching to an external player, but have not had any success. VLC works fine when launched from the desktop, but not from within Myth frontend. In the settings, I have replaced "Internal" with things like, "vlc dvd:/dev/dvd", "mplayer dvd:/dev/dvd", etc. I can get the disc drive spinning, but nothing on screen. I know I need to use commands like, "-fs" (full screen) or "-vo" (video overlay), but whenever I do, my system freezes. Am I missing something because I'm watching on a TV through video out? If someone could please tell me EXACTLY what I need to type in for MPlayer, VLC and Xine to work, it would really save Christmas.

---

### Post by Titus A Duxass on 2007-12-18
For xine I use: xine -phfq --no-splash -r 4:3 which replaces the command Internal found when you go into setup, dvd play, etc. Not in mythtv-setup.

---

### Post by majoridiot on 2007-12-18
for vlc dvd functionality, the player setting is:
```
vlc --fullscreen dvd:// %d vlc:quit
```

there are settings, etc. to config and tweak for vlc to play nicely with mythtv.  
a decent, though not thorough reference can be found at:

[http://www.mythtv.org/wiki/index.php/VLC](http://www.mythtv.org/wiki/index.php/VLC)

---

