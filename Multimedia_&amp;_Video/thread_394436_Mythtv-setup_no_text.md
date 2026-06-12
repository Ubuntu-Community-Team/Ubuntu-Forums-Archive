---
title: "Mythtv-setup no text"
date: 2007-03-26
forum: Multimedia &amp; Video
---

### Post by nullspace on 2007-03-26
I installed everything with no problems. I boot into the gui I am running (openbox)
and run mythtv-setup from the terminal and I get the graphical part of the setup but it has no text effectively making the whole thing useless.

here is the error report I get when I launch mythtv-setup 

```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-03-26 22:44:13.243 Using runtime prefix = /usr
2007-03-26 22:44:13.259 DPMS is active.
2007-03-26 22:44:13.274 New DB connection, total: 1
2007-03-26 22:44:13.280 Connected to database 'mythconverg' at host: localhost
2007-03-26 22:44:13.281 Total desktop dim: 1280x768, with 1 screen[s].
2007-03-26 22:44:13.317 Using screen 0, 1280x768 at 0,0
2007-03-26 22:44:13.331 Current Schema Version: 1160
2007-03-26 22:44:13.441 Total desktop dim: 1280x768, with 1 screen[s].
2007-03-26 22:44:13.451 Using screen 0, 1280x768 at 0,0
2007-03-26 22:44:13.453 Switching to square mode (G.A.N.T.)
2007-03-26 22:44:13.752 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-03-26 22:44:14.891 Joystick disabled.
2007-03-26 22:44:16.619 Loading from: /usr/share/mythtv/themes/G.A.N.T./base.xml
2007-03-26 22:44:16.649 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-03-26 22:44:37.708 RecordFilePrefix is not set? 
```

any ideas?

---

### Post by superm1 on 2007-03-26
Install msttcorefonts.  Minor bug in packaging (didn't realize several themes DO depend on it).

---

### Post by nullspace on 2007-03-27
omg thank you.

---

