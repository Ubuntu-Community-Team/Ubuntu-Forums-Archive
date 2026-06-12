---
title: "Dynamic playlists in Clementine"
date: 2019-05-27
forum: Multimedia Software
---

### Post by CatKiller on 2019-05-27
I've been using Amarok for quite a while, but it's kinda buggy and not really maintained any more, so I'm trying to like Clementine instead.

One function of Amarok that I use all the time is to use a dynamic playlist to have a *curated random* slice of my library. It shows the last couple of songs played, and the upcoming *n* tracks. Any that I'm not in the mood for can be deleted, and the number of tracks is instantly replenished to *n* again.

I haven't been able to replicate this behaviour with Clementine. Its dynamic playlist doesn't clear previous songs, and nor does it update when you remove tracks. There is also a huge **Dynamic mode is on** dialogue that I can't seem to make go away.

Have I overlooked something, or is Clementine just really limited in its functionality?

---

### Post by Holger_Gehrke on 2019-05-30
Clementine updates dynamic playlists only while playing them and then at the time it goes to the next song in the list. So a dynamic playlist set to contain 40 songs will actually show 46 songs after it has been playing for a while: 5 that have been played, the currently playing song and the next 40. If some of those 40 are removed the list will be filled back up when the player goes to the next song in the list. At that time it also removes the oldest song from the backlog. I don't know if the number of played songs it keeps in the list is fixed at five or can be changed in some way.

And no, I haven't found a way to make the indicator for the dynamic mode less of an intrusive eyesore.

Holger

---

### Post by CatKiller on 2019-05-30
OK, thanks. Good to know that I hadn't missed anything, although it's a shame that it doesn't have those functions.

---

