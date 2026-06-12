---
title: "[SOLVED] MPD won't index certain songs"
date: 2008-07-05
forum: Multimedia Software
---

### Post by stinkinrich88 on 2008-07-05
Hello,

For some reason, when I run mpd --create-db, it adds all my music except a couple of albums. One album an mp3 album, the other a flac album ripped with EAC, just like my other albums that work fine. 

The albums play fine in vlc, but for some reason mpd won't index them. 

Any ideas?

Thanks

---

### Post by stinkinrich88 on 2008-07-11
solved!!

anyone with the same problem: check out the properties for the album folder. Make sure all three "Folder access" drop-down boxes have "Create and delete files" then click "apply permissions to enclosed files"

---

