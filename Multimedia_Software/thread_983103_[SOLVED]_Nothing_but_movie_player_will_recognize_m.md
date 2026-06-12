---
title: "[SOLVED] Nothing but movie player will recognize my music files now?!"
date: 2008-11-15
forum: Multimedia Software
---

### Post by finalrequiem on 2008-11-15
Last night I went through and cleaned up the file names of all my mp3's.  Now nothing but the movie player will play them.  They don't show up in Amarok, etc.  They are in my file system and the properties show them as mp3's.  If I add .mp3 to the actual filename, they show up.  Is there a way around having to do that?  Help...

---

### Post by xc3RnbFO8P on 2008-11-15
Install **mp3rename** in Synaptic Package Manager
In Terminal:
> cd /home/your folder/Music what ever your mp3 files are.
> mp3rename -s '(&a)-&t-&b'
> mp3rename *

It uses tag information to rename the music files.

---

