---
title: "Rhythmbox data files"
date: 2010-07-20
forum: Multimedia Software
---

### Post by phil1349 on 2010-07-20
Can anyone tell me where Rhythmbox stores it's data and configuration files ? What I want to do is copy the playlist information from one computer to another.

Thanks

---

### Post by mc4man on 2010-07-20
Don't particularly use rhythmbox but look in ~/.local/share/rhythmbox
( .local is a hidden folder in home dir. ( View - > Show  Hidden ...

---

### Post by sgosnell on 2010-07-20
/home/user/.local/share/rhythmbox is where the files are stored.  Playlist.xml contains the playlists, and rhythmdb.xml contains the music database.  You may not want to use this, because the music will be in a different place on the other computer, and the file is recreated on launch.  Copying the playlist file should be no problem, though.

---

