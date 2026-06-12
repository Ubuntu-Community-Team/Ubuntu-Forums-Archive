---
title: "amarok's mysql not updating"
date: 2007-05-10
forum: Multimedia &amp; Video
---

### Post by catfishy on 2007-05-10
Hi!  I just switched over from sqlite to mysql for amarok and I was happy that it made the database *so* quickly!  (1 hour instead of 5!)  Anyhow, the database updates when I add more music to the collection, but the program is acting strangely:  favorite albums and favorite/suggested songs never show up when playing a song or sitting idle, regardless of the poularity of the band.  It appears that "Newest Albums" and "Favorite Albums" have been switched, as I see that the few albums I've listened to have been put in the Newest Album category while the Favorite Albums section continues to say  "A list of your favorite albums will appear here, once you have played a few of your songs."  If anyone's come across this problem I'd love to find a solution so I can start seeing my songs rated and so I can receive song suggestions.
Thanks so much!

The behavior makes me think that Amarok doesn't have proper write access, but it *does* update and it did make the database.
Re-installation of amarok had no effect.  Would tweaking the database externally fix the problem?

I just found that people have a similar problem here, but no solution:
[http://amarok.kde.org/forum/index.php?topic=13494.msg16780](http://amarok.kde.org/forum/index.php?topic=13494.msg16780)
[http://osdir.com/ml/kde.amarok.bugs/2005-09/msg00797.html](http://osdir.com/ml/kde.amarok.bugs/2005-09/msg00797.html)

Here is something that is not likely helpful, but I get this when I run amarok in the terminal:
```
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8096040 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8096040 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
```

My collection is on an external hdd.  Any ideas?

---

### Post by catfishy on 2007-05-12
Solved this particular problem with a weird database by:
re-scanning the database

i first dropped the amarok database
created a new database with the instructions here:
[http://amarok.kde.org/amarokwiki/index.php/MySQL_HowTo](http://amarok.kde.org/amarokwiki/index.php/MySQL_HowTo)
and when amarok was restarted it built the new one!

it all works perfectly now.  Thanks for reading.
All of my posts are soliloquies.

post-script: and oh, mysql kicks sqlite's butt for big collections; it's soooo fast!

---

