---
title: "Amarok died"
date: 2007-04-15
forum: Multimedia &amp; Video
---

### Post by argentum2f on 2007-04-15
I was trying to get surround sound to work, and I changed a device setting in amarok (I think I selected oss instead of auto). Amarok died then, and I haven't been able to revive it. I tried removing then installing it again with apt-get, and it's still not working. If I could manually change the setting back, that would be find, but I can't find any config files.

When run amarok in a terminal I get:
```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```

Any suggestions of how to get it working again?

---

### Post by argentum2f on 2007-04-15
ok, I got rid of the "X Error: BadDevice..." errors (see [[COLOR="Blue"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=212025") thread)

I still get this:
```
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...

```

And it still doesn't do more than show the splash screen befor dying
[B]
EDIT:[/B]  Problem solved:
I finally found the config files in  ~/.kde/share/apps/amarok, so I renamed the folder and it worked. I then copied the files back till it stopped working, it was the collections.db file. Must've gotten corrupted or something when it crashed the first time.

---

