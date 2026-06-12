---
title: "How can I save/load mp3 tags to/from a file?"
date: 2009-04-20
forum: Multimedia Software
---

### Post by kung fu buntu on 2009-04-20
I want to dump mp3 tags to a file and then restore then latter (not necessarily on the same computer).
Ideally this should be with a command line tool.

I was thinking on using mp3info2 for this task and (after some problem solving) everything was going fine until it was time to restore those tags back... which resulted in an error:
*Writing of ID3v2.4 is not fully supported (prohibited now via `write_v24').*
FYI, when I was having shell scripting problems with handling mp3info2 output I opened another thread:
[http://ubuntuforums.org/showthread.php?p=7100298](http://ubuntuforums.org/showthread.php?p=7100298)
(in case you are curious on what I am trying to do)


I have also played with id3info and id3v2, but they failed to show the correct tags in the mp3 file.

flac, a less used format, has a convenient tool for doing this, metaflac.
I find it surprising there is nothing for mp3 files.

---

