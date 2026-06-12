---
title: "No codec options in acidrip"
date: 2010-05-19
forum: Multimedia Software
---

### Post by xbrae.wrightx on 2010-05-19
When i try to select a codec for ripping a dvd to in acidrip, there are no codecs in the menu that is meant to be there.
I have tried reinstalling mencoder and acidrip but no luck.
running lucid with latest updates.
this has not worked since i first installed lucid.

i also get this when i run mencoder -ovc help

MEncoder SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
Option of: Unknown suboption lavc
Warning unknown option of at line 9
Option format: unknown format name: 'mp4'
Error parsing option lavcopts=format=mp4 at line 10

Exiting... (config file error)

---

### Post by xbrae.wrightx on 2010-05-23
Never mind, just had to delete an Mencoder config file from my ~./mplayer folder.

---

