---
title: "Where does Rhythmbox 0.12.5 store playlists?"
date: 2010-03-08
forum: Multimedia Software
---

### Post by carljm on 2010-03-08
0.12.5 is the Rhythmbox version packaged with Karmic, and I can't find my playlists on disk anywhere. I've created a playlist, exited and restarted Rhythmbox to make sure it has to persist it somewhere; still nothing in ~/.config, ~/.gnome2, or the Rhythmbox section in gconf-editor. Anyone have a clue?

I found some posts from years past that said ~/.gnome2/rhythmbox, but it's not there...

---

### Post by carljm on 2010-03-08
Found it, with the help of:

```
strace -e trace=open rhythmbox
```

It's in ~/.local/share/rhythmbox/playlists.xml.

---

