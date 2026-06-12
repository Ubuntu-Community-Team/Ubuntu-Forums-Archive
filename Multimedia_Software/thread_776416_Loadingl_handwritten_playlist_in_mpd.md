---
title: "Loadingl handwritten playlist in mpd"
date: 2008-04-30
forum: Multimedia Software
---

### Post by shearn89 on 2008-04-30
Hey all - just tried to load an exported playlist in mpd, and no luck.

I exported it from itunes in windows, then edited it so it was just the paths to the files, just like my mpd created playlists. It looks perfect, but when i try to load it, it just doesn't work. No errors, just nothing?

the playlist is a list of files, one per line, with full paths starting from the music directory:
```

artist/album/track.ext
artist/album/track.ext

```

I checked, and this is exactly the same way the playlists that i created WITH MPD are formatted. The permissions are all exactly the same. Its kinda weird that it just isn't working...

Any help/ideas/abuse would be helpful.

---

### Post by shearn89 on 2008-04-30
DOH! just discovered the prob - because its windows, all the "/" are "\". Man i feel stupid.

Consider this solved. Where is that button?

---

