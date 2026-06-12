---
title: "Google Music not reading mp3gain tags"
date: 2013-02-14
forum: Multimedia Software
---

### Post by Joshimitsu on 2013-02-14
I think!

Hey everyone.  I use mp3gain from the terminal to normalise the volume of my music collection.  I use this:

```
cd ~/Music
find . -iname '*.mp3' -execdir mp3gain -r -k "{}" \; &
```This works fine when playing the music on the desktop using things like Banshee and Rhythmbox, but doesn't seem to work when I upload it to Google Music.  When playing it from the browser and on my android the volume jumps about.

Any ideas?  The settings on both the site Google Music and Google Music Player on the android are pretty basic, so I can't see any options relating to mp3gain tags.

Thanks! :)

---

