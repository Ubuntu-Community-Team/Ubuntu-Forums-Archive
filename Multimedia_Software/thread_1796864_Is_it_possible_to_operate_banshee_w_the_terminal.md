---
title: "Is it possible to operate banshee w/ the terminal?"
date: 2011-07-04
forum: Multimedia Software
---

### Post by Redsoul90 on 2011-07-04
what i mean is like type

"banshee play Hatsune_Miku" 

and it plays.

youtube and google yield no results so i brought it here.

---

### Post by Enigmapond on 2011-07-04
You would need the full path to file...i.e.

```
banshee /home/Music/This Song Rocks.FLAC
```

---

### Post by Redsoul90 on 2011-07-04
thanks for the response.

i was looking for a shortcut to play the whole album/artist but given you have to use the full path i dont think thats possible

---

### Post by nothingspecial on 2011-07-04
Not being funny but that is a very slow way of doing what you want to do. Why not use mplayer or cvlc and use globs.

For example say you want a particular song, then yes use the full path.

Assuming your music collection is arranged Music/Artist/Album/songs

Then for a whole album 

```
mplayer Music/Artist/Album/*
```

for an artist ```
mplayer Music/Artist/*/*
```

for everything

```
mplayer Music/*/*/*
```

To play any of those options randomly just add the shuffle flag, eg

```
mplayer -shuffle Music/*/*/*
```

If your music collection is a mess then find is your friend.

---

### Post by Cyjan on 2011-08-17
> **nothingspecial said:**
> Not being funny but that is a very slow way of doing what you want to do. Why not use mplayer or cvlc and use globs.

For example say you want a particular song, then yes use the full path.

Assuming your music collection is arranged Music/Artist/Album/songs

Then for a whole album 

```
mplayer Music/Artist/Album/*
```for an artist ```
mplayer Music/Artist/*/*
```for everything

```
mplayer Music/*/*/*
```To play any of those options randomly just add the shuffle flag, eg

```
mplayer -shuffle Music/*/*/*
```If your music collection is a mess then find is your friend.

is it possible to do the same with/in banshee ??
what am i missing?
i tried : 
banshee -shuffle
and 
banshee /home/xxxxxxxxxx/music/*/* -shuffle

thank you

---

