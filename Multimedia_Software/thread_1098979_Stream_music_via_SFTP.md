---
title: "Stream music via SFTP"
date: 2009-03-17
forum: Multimedia Software
---

### Post by beingfamous on 2009-03-17
I'm using an SFTP connection to my media server as a way to store music and videos. Currently I play music with VLC Media Player, one file at a time. 

What I want to do is have a media player that forms a playlist and will stream the files via the SFTP and automatically play them.

Any suggestions?

---

### Post by zyrorl on 2009-03-17
You could mount it using GVFS?

Places-> connect to server

custom location:

sftp://youraddress/

connect..

done.

Then just load music on your favourite media player (or right click folders and add them to playlist or drag them into your media player).

easy.

---

### Post by beingfamous on 2009-03-17
That's what I'm currently doing to browse the files and open them inside VLC. However, when I tried doing that with other media players, I would have an 'error sftp:// is unknown' (nonverbatim) error.

---

