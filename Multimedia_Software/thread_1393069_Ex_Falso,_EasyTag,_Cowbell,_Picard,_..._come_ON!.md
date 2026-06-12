---
title: "Ex Falso, EasyTag, Cowbell, Picard, ... come ON!"
date: 2010-01-28
forum: Multimedia Software
---

### Post by lifestream on 2010-01-28
I've tried Ex Falso,  EasyTag, Cowbell, Picard.... 

I want a program that will go through my entire Music folder, and AUTOMATICALLY uses the Internet to find the tags and album cover, then save both to the music file itself.

I've tried the programmes named above, and none seem to want to do that.

Cowbell so far seems the most promising one, however

```
~$ cowbell -q --batch  /media/WD_BACKUP/Music/Jon\ Hopkins
Searching /media/WD_BACKUP/Music/Jon Hopkins/Contact Note...
Found /media/WD_BACKUP/Music/Jon Hopkins/Contact Note

Unhandled Exception: System.ApplicationException: URI could not be converted to local file path
  at Cowbell.Base.SafeUri.UriToFilename (System.String uri) [0x00000] 
  at Cowbell.Base.Filesystem.Import (System.String[] uris) [0x00000] 
  at Cowbell.Base.Batch.ProcessAlbum (System.String dir) [0x00000] 
  at Cowbell.Base.Batch..ctor (System.String[] paths, Boolean quiet) [0x00000] 
  at Cowbell.Runtime.Main (System.String[] args) [0x00000] 

```

So yeah.
And using it from the GUI gives AMAZON error....


So is there a AUTOMATIC tagging program? That ALSO downloads album covers and saves them in the MP3 itself?

Wheee.... *keeps googling*

---

