---
title: "VLC under Lucid - How to Load a Playlist"
date: 2010-07-17
forum: Multimedia Software
---

### Post by -kg- on 2010-07-17
I have used VLC player in the past to play music under certain conditions, but am having a bit of a problem.  I have Googled this problem to no avail.

Nowhere in the menus can I find a way to load a playlist.  This playlist was generated under and saved from VLC.  When consulting the documentation at the website, it says to load the playlist from the "Playlist" menu, but there is no "Playlist" menu present, as shown in the screenshots from the site.  I can find the "Save Playlist to File" option under the "Media" menu, but nowhere can I find a "Load Playlist" option.

I have read that the playlist can be dragged and dropped (specifically, directly onto the player), but VLC won't play the playlist.  Can anyone tell me how to load a playlist into VLC?

---

### Post by mc4man on 2010-07-17
In vlc 1.0.X (assuming 1.0.6), playlists are just a file, so open like any other file.

(it may or may not have an issue with a  .xspf, .m3u is more reliable on 1.0.6

You may find vlc 1.1.X a bit more suited to playlists and or media collections

---

### Post by -kg- on 2010-07-17
Absolutely right about the .xspf, mc4man!  I reconstructed the playlist file and saved it as .m3u and it works perfectly.

It blows me away that there is even an option to save a playlist as .xspf when it doesn't seem to work.  They might as well leave it as a default .m3u format, at least until handling .xspf's fixed.  It doesn't make any sense to have VLC save playlists by default in a format that doesn't seem to work with it (and works with every other player that I've tried! :roll: ).

But that's just me...(I seem to be saying that a lot these days! :p )

---

