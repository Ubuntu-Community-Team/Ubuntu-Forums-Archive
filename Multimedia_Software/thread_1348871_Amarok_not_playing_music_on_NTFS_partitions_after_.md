---
title: "Amarok not playing music on NTFS partitions after kernel update"
date: 2009-12-07
forum: Multimedia Software
---

### Post by JBAlaska on 2009-12-07
I just tried to play some music on a NTFS partition with Amarok 2, It can be added to the playlist but will not start, music on my ext4 partition plays fine. The NTFS partition IS mounted and the MP3's play fine with mouseover or banshee.

Amarok was working just fine until the latest kernel upgrade, debug mode gives me this:
```
amarok:   [EngineController] [WARNING!] Phonon failed to play this URL. Error:  "Cannot find demultiplexer plugin for MRL [file://media/Storage_Drive_1/Music/Joe Bonamassa Discography 2001-2006/2006 - You And Me/11 - Torn Down.mp3]" 
```

Anyone? this is driving me nuts.

[COLOR="Red"]Edit: I found the fix:[/COLOR]
```
rm ~/.xine/catalog.cache
```

---

